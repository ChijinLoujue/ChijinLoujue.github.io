#UE4的自动打包过程

## Android  手动
2020/08/18
问题：使用官网上的方法打包和预览都会卡死，分析原因可能在于安装Android环境时没有关闭UE4 ,导致后面卡死，解决方法，观察Android SDK中的JAVA_HOME和ANDROID_HOME路径是否有问题，在环境变量->用户变量中,查看，最终路径分别应该为NVPACK/jdk1.8.0_77和NVPACK\android-sdk-windows


## Android  自动打包
参考文档：


FastBuild   FastCode   Jenkins
