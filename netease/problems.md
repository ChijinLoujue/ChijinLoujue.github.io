# 问题集锦

## 2020/08/12
### 列表索引 ==已解决==
```py
items['link'] = tbody.xpath('./tr/th/a[@class="s xst"]/@href').extract()
items['headline'] = tbody.xpath('./tr/th/a[@class="s xst"]/text()').extract()
items['influence'] = tbody.xpath('./tr/td[@class="num"]/a/text()').extract()
```
语句能输出一个长度为1的列表:
```sh
{'headline': ['新引擎测试启动，御怨般若新皮上架（20200701体服维护解读）'],
 'influence': ['13'],
 'link': ['thread-7484921-1-1.html']}
```
但是为了使字典的值是字符串而不是列表，要取列表的值，如果用列表索引就出错：
```py
items['link'] = tbody.xpath('./tr/th/a[@class="s xst"]/@href').extract()[0]
items['headline'] = tbody.xpath('./tr/th/a[@class="s xst"]/text()').extract()[0]
items['influence'] = tbody.xpath('./tr/td[@class="num"]/a/text()').extract()[0]
```
就会出错
```sh
  File "E:\Grundstudium\opinionmonitoring\opinionforOnmyoji\opinionforOnmyoji\spiders\yysbbsSpider.py", line 29, in parse
    items['link'] = (tbody.xpath('./tr/th/a[@class="s xst"]/@href').extract())[0]
IndexError: list index out of range
```
如果列表只有一个值，用extract_first()就可以跑通，但如果多个值需要取第二个，就无法得到。
#### 解决
因为有的爬出来没有内容，列表表现为None，
在None中没有索引，所以即使是list[0]也表现出超出索引


### 爬虫子网页回退问题 ==未解决==
需要爬取论坛帖子的跟帖，在帖子页面爬到最后第59页时，正常应该回退第二个帖子的第一页，但是此处直接进入到第二个帖子的第60页
```sh
2020-08-12 16:43:52 [scrapy.core.scraper] DEBUG: Scraped from <200 https://yys.16163.com/thread-7046734-59-1.html>
{'comments': '\r\n阴阳师真好玩'}
2020-08-12 16:43:52 [scrapy.core.engine] DEBUG: Crawled (200) <GET https://yys.16163.com/thread-2416586-59-1.html> (referer: https://yys.16163.com/thread-2416586-58-1.html)
```
相关代码：
```py
    def parse(self, response):
        items = OpinionforonmyojiItem()
        tbodys = response.xpath('//tbody[@id!="separatorline"]')
        for tbody in tbodys:
            items['link'] = tbody.xpath('./tr/th/a[@class="s xst"]/@href').extract_first()
            items['headline'] = tbody.xpath('./tr/th/a[@class="s xst"]/text()').extract_first()
            items['reply'] = tbody.xpath('./tr/td[@class="num"]/a/text()').extract_first()
            items['view'] = tbody.xpath('./tr/td[@class="num"]/text()').extract_first()
            deeper_page_url = items['link']
            if deeper_page_url is not None:
                deeper_url = 'https://yys.16163.com/'+deeper_page_url
                yield scrapy.Request(url=deeper_url, callback=self.parse_detail, meta={'item': items},dont_filter=True)
            yield items

    def parse_detail(self, response):
        items = OpinionforonmyojiItem()   
        tbodys = response.xpath('//td[@class="t_f"]')
        for tbody in tbodys:
            items['comments'] = tbody.xpath('./text()').extract_first()
            yield items
        next_page_url = response.xpath('//a[@class="nxt"]/@href').extract_first()
        if next_page_url is not None:
            next_url = 'https://yys.16163.com/'+next_page_url
            yield scrapy.Request(url=next_url, callback=self.parse_detail, meta={'item': items},dont_filter=True)
```
## 2020/08/14
### 遍历字符串列表  ==已解决==
遍历字符串列表出现单个字符
```py
td_list = response.xpath('//td[@class="t_f"]/text()').extract()  # 这是个字符串列表
for td in td_list:    #这应该是个字符串
    item['comments'] = td
    yield item     #这也是个字符串，但输出的print是字符列表
```
输出：
```sh
{'comments': ['阴','阳','师','真','好','玩','啊'],
 'normalthread': '046734',
 'reply': '1174',
 'view': '3274189'}
```
#### 解决
是Pipeline的问题，之前在Pipeline里对item['comments']筛选时当作列表处理了，改为字符串之后没有对这进行修改，字符串当列表处理之后返回了一个单字符的列表


## 2020/11/24
### “cannot import name”错误  ==已解决==
python脚本出现“cannot import name”错误的一个可能原因:
如果不是环境问题的话，那就是文件名命名的问题
py文件名和要引入的模块重名了
解决方法: 修改py文件名使其与模块不重名