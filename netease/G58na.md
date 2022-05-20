## 源
客户端代码：https://svn-g58.gz.netease.com/svn/lite/prog/source/trunk/client
压测机器人：https://svn-g58.gz.netease.com/svn/lite/tool/fake_client_new
压测机器人mgr：https://svn-g58.gz.netease.com/svn/lite/tool/fake_client_mgr_new
ssh://git@git-qa.gz.netease.com:32200/zhangyinghao/g58na_protobot.git

## 登录
create_entity   //   创建实体
{
    "entity_type": "ClientAccount",
    "entity_id": "5f966a390f69a0f9434b6764"
}

login                登录
{
    "method_name": "login",
    "args": "{'name': 'yzx', 'psw': '', 'sv': 100001, 'li': '10.231.36.64', 'nm': '255.255.254.0', 'vf': '0.999999.999999', 'vr': 999999, 'md5': '', 'tag': '4a6e2d17acc49d90ba3ea86354bdc1fd', 'lr': False, 'ch': 'netease', 'ach': 'netease'}",
    "entity": "<entity.ClientAccount.ClientAccount object at 0x000001C5CFB86630>"
}

become_player //          成为玩家
{
    "entity": "5f966a390f69a0f9434b6764",
    "method_name": "become_player",
    "args": "{}"
}

hotfix//          热修复
{
    "entity": "5f966a390f69a0f9434b6764",
    "method_name": "hotfix",
    "args": "{u'c': u'# -*- coding: utf-8 -*-\\n'}"
}

create_entity//          重新建立实体
{
    "entity_type": "ClientAvatar",
    "entity_id": "5f96359f72a7c874e8ade33a"
}

become_player//         重新成为玩家
{
    "entity": "5f96359f72a7c874e8ade33a",
    "method_name": "become_player",
    "args": "{}"
}

uploadDeviceInfo          上传设备信息
{
    "method_name": "uploadDeviceInfo",
    "args": "{'di': {'device_model': 'pc#pc#Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz#12#3192#GeForce GTX 1660 Ti/PCIe/SSE2', 'app_ver': '0.0.0', 'os_name': '', 'os_ver': '1.0', 'device_width': 540, 'device_height': 960, 'ip': '10.231.36.64', 'app_channel': 'g58na', 'info': 'client.exe', 'app_sub_channel': None, 'engine_ver': '0', 'imei': '', 'is_emulator': True, 'isp': '', 'network': 'non-wifi', 'mac_addr': 'A4-BB-6D-4A-8C-FD', 'transid': '', 'unisdk_deviceid': '', 'idfa': '', 'is_root': False, 'udid': ''}}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x000001C5CFB867B8>"
}
 
heartbeatServer          心跳服务器
{
    "method_name": "heartbeatServer",
    "args": "{}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x000001C5CFB867B8>"
}

logCheckCheat              日志检查作弊
{
    "method_name": "logCheckCheat",
    "args": "{'b': 'client.exe', 'p': []}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x000001C5CFB867B8>"
}

uploadTouchHistory           上传触摸历史
{
    "method_name": "uploadTouchHistory",
    "args": "{'h': []}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x000001C5CFB867B8>"
}

destroy_entity//    销毁实体
{
    "entity": "5f966a390f69a0f9434b6764"
}

on_heartbeat//  在心跳
{
    "entity": "5f96359f72a7c874e8ade33a",
    "method_name": "on_heartbeat",
    "args": "{}"
}


gmServerRequest
{
    "method_name": "gmServerRequest",
    "args": "{'c': 'p.afkData.afk_mission=20801'}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x00000215B6331518>"
}

gmServerReply   #
{
    "entity": "5f9f7b03dbac93693bdd246b",
    "method_name": "gmServerReply",
    "args": "{u'd': u''}"
}






## GM

gg.avatar.gmServerRequest('''p.afkData.afk_mission=20801''')
gg.avatar.gmServerRequest('''p.fakePvpRanklistData.remain_time=5''')
1	金币
2	经验值
3	测试物品
4	历练点数           天赋的五角星勋章
5	幻力精华           天赋的三角钻
6	幻力余烬           英雄升级用的
7	虚空遗骸          英雄突破用的
8	技能训练书
9	测试物品
10	晶钻                   黑门钻石
11	欧泊
12	竞技场币

1000 
1001 巧克力豆
1002 匕首
1003 月饼
1004 羽毛
1005 盆栽
1006 三角蛋糕
1007 炖锅
1008 铭牌
1009 碟片
1011 蛋糕
1012 高达
1013 心型巧克力
1014 花裙子
1015 电脑
1016 钻石

1101 冰淇淋
1102 粉球
1103 紫花
1104 蝴蝶
1105 金砖
1106 扁礼盒
1107 方礼盒
1108 长礼盒







/money xxxx   
/yuanbao xxxx 
/item itemid num

### 开启录制插件
import os,sys;os.getcwd();sys.path.append('./');from Infiltrator import Infiltrator;Infiltrator().start()

加所有英雄：/add_all_heroes

加所有英雄等级：/all_hero_level   level

==========================================================

{
    "entity": "5fa13d5edbac9369436d665a",
    "method_name": "reliableRpcCall",
    "args": "{u'_cbid_': 3, u'w': {u'p': {u'_r_': {}}, u'r': 3, u'm': u'serverCallbackCarrier'}}"
}

{
    "entity": "5fa13d5edbac9369436d665a",
    "method_name": "reliableRpcCall",
    "args": "{u'_cbid_': 5, u'w': {u'p': {u'_r_': {}}, u'r': 5, u'm': u'serverCallbackCarrier'}}"
}

{
    "method_name": "reliableRpcAck",
    "args": "{'s': 9}",
    "entity": "<entity.ClientAvatar.ClientAvatar object at 0x000002036EBE29B0>"
}