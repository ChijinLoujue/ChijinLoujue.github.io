# Jenkins 

持续部署
持续集成
持续


![avatar](https://s1.ax1x.com/2020/08/13/dSs0rq.png)

```sh
echo ===============================Client============================
D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\trunk\GM33.uproject -noP4 -platform=Win64 -clientconfig=Development -serverconfig=Development -cook -allmaps -build -stage -pak -archive -archivedirectory=E:\MiNiProject\GM33\trunkPackage\Client\Revision_%SVN_REVISION%_BUILD_%BUILD_ID%
```

```sh
echo ===============================Server============================
D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\trunk\GM33.uproject -noP4 -platform=Win64 -clientconfig=Development -serverconfig=Development -cook -server -serverplatform=Win64 -noclient -build -stage -pak -archive -archivedirectory=E:\MiNiProject\GM33\trunkPackage\Server\Revision_%SVN_REVISION%_BUILD_%BUILD_ID%
```


## 问题

UE4的手动打包参考的主要流程参考在[EPIC：Android快速入门](https://docs.unrealengine.com/zh-CN/Platforms/Mobile/Android/GettingStarted/index.html)，目前能够成功打包UE4_22.3的示例项目到Android 5.1的手机
UE4的主要参考文档在[虚幻引擎知识地图](https://km.netease.com/topics/topic/3383/item/31437)中，其中说明UE4的主要插件在于公司内部的版本，这个需要申请。UE4的最后公版是4.21版本，此时我们项目组已经在EPIC上下载4.22版本进行开发，是否应该更换为公司内部的版本？
UE4的自动打包流程主要参考[UE4打包以及改造](https://km.netease.com/topics/topic/3383/item/31437)和[UE4自动化打包流程](https://km.netease.com/article/292120)两篇文章，第二篇文章应该是关键但我基本不太明白，首先是我没有公版

![km里的pipiline](https://s1.ax1x.com/2020/08/21/dttql8.png)

![我自己的pipiline](https://s1.ax1x.com/2020/08/21/dtURVH.png)

我在jenkins中新建pipeline后没有UE4相关的内容，不知道教程中是在哪儿导入的，界面基本上不一样，



d38ce965-b93e-45a4-b077-68679709aa93
^GM33/art_resource/*


python "%WORKSPACE%\Scripts\build.py" --engine_root_path="%Engine_Root%" --project_path="%WORKSPACE%" --configuration=%Configuration% --build_platform=%Platform% --game_name=%JOB_NAME% --release_version=%BUILD_NUMBER% --release_path="E:\Release"

python "E:\MiNiProject\ChijinLoujue\Scripts\Scripts\build.py" --engine_root_path="D:\WorkSoftware\UE_4.22\" --project_path="D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest\trunk" --configuration=Development --build_platform=Win64 --game_name="Test" --release_version=1_1 --release_path="E:\MiNiProject\GM33\release"

    command = """call "{uat_tool}" BuildCookRun -project="{project_file}" -noP4 -platform={platform} -clientconfig={config} -serverconfig={config} """.format(
        uat_tool=uat_tool,
        project_file=project_file,
        platform=platform,
        config=configuration)
    command += " -cook -allmaps -build -stage -pak -compressed"


"{uat_tool}" BuildCookRun -project="{project_file}" -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -ue4exe=E:\WorkSpaces\UnrealEngine4.24\Engine\Binaries\Win64\UE4Editor-Cmd.exe -utf8output -targetplatform={platform} -cookflavor=ETC1 -build -cook -allmaps -unversionedcookedcontent -pak -createreleaseversion=0.2 -manifests -compressed -stage -package -cmdline=" -Messaging" -archive -archivedirectory=E:\jenkinsoutput\Client\Revision%BUILD_NUMBER%


//pull code
```sh
checkout([$class: 'SubversionSCM', additionalCredentials: [], excludedCommitMessages: '', excludedRegions: '', excludedRevprop: '', excludedUsers: '', filterChangelog: false, ignoreDirPropChanges: false, includedRegions: '', locations: [[credentialsId: '52664811-4ae6-4427-aca9-f5d8bf8ba823', depthOption: 'infinity', ignoreExternalsOption: true, local: './trunk', remote: 'https://svn-nb.gz.netease.com/202007/GM33']], workspaceUpdater: [$class: 'UpdateUpdater']])
```



```sh
E:\WorkSpaces\UnrealEngine4.24\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=E:\test\project.uproject -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -ue4exe=E:\WorkSpaces\UnrealEngine4.24\Engine\Binaries\Win64\UE4Editor-Cmd.exe -utf8output -targetplatform=Android -cookflavor=ASTC -build -cook -allmaps -unversionedcookedcontent -pak -createreleaseversion=0.2 -manifests -compressed -stage -package -cmdline=" -Messaging" -archive -archivedirectory=E:\jenkinsoutput\Client\Revision_%SVN_REVISION%_BUILD_%BUILD_ID%
```

D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest\trunk\Test.uproject -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -ue4exe=D:\WorkSoftware\UE_4.22\Engine\Binaries\Win64\UE4Editor-Cmd.exe -utf8output -targetplatform=Android -cookflavor=ASTC -build -cook -allmaps -unversionedcookedcontent -pak -createreleaseversion=0.2 -manifests -compressed -stage -package -cmdline=" -Messaging" -archive -archivedirectory=E:\MiNiProject\GM33\release\Revision_1_BUILD_01

//参考的
D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest\trunk\Test.uproject -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -ue4exe=D:\WorkSoftware\UE_4.22\Engine\Binaries\Win64\UE4Editor-Cmd.exe -utf8output -targetplatform=Android -cookflavor=ASTC -build -cook -allmaps -unversionedcookedcontent -stage -pak -createreleaseversion=0.2 -manifests -compressed -package -cmdline=" -Messaging" -archive -archivedirectory=E:\MiNiProject\GM33\release\Revision_1_BUILD_01

//改后的
D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest\trunk\Test.uproject -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -ue4exe=D:\WorkSoftware\UE_4.22\Engine\Binaries\Win64\UE4Editor-Cmd.exe -utf8output -targetplatform=Android -cookflavor=ETC1 -build -cook -allmaps -unversionedcookedcontent -stage -pak -createreleaseversion=0.2 -manifests -compressed -package -cmdline=" -Messaging" -archive -archivedirectory=E:\MiNiProject\GM33\release\Revision_1_BUILD_01

D:\WorkSoftware\UE_4.22\Engine\Build\BatchFiles\RunUAT.bat BuildCookRun -project=D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest\trunk\Test.uproject -noP4 -clientconfig=Shipping -serverconfig=Shipping -nocompileeditor -utf8output -targetplatform=Android -cookflavor=ETC1 -build -cook -allmaps -unversionedcookedcontent -stage -pak -manifests -compressed -package -cmdline=" -Messaging" -archive -archivedirectory=E:\MiNiProject\GM33\release\Revision_1_BUILD_01

//参考的
"E:\WorkSpaces\UnrealEngine4.24\Engine\Binaries\Win64\UnrealVersionSelector.exe" /projectfiles "E:\test\project.uproject"

"E:\WorkSpaces\UnrealEngine4.24\Engine\Binaries\Win64\UnrealVersionSelector.exe" /projectfiles "E:\test\project.uproject"

//参考的
"E:/WorkSpaces/UnrealEngine4.24/Engine/Binaries/DotNET/UnrealBuildTool.exe" Development Win64 -Project="E:/test/project.uproject" -TargetType=Editor -waitmutex -FromMsBuild -DEPLOY

//改后的
"D:/WorkSoftware/UE_4.22/Engine/Binaries/DotNET/UnrealBuildTool.exe" Development Win64 -Project="D:/WorkSoftware/qkit_jenkins/jenkins/workspace/packageTest/trunk/Test.uproject" -TargetType=Editor -waitmutex -FromMsBuild -DEPLOY



## 错误0824 
```sh
	at com.cloudbees.groovy.cps.sandbox.SandboxInvoker.methodCall(SandboxInvoker.java:17)
Caused: java.io.IOException: Cannot run program "nohup" (in directory "D:\WorkSoftware\qkit_jenkins\jenkins\workspace\packageTest"): CreateProcess error=2, 系统找不到指定的文件。
	at java.lang.ProcessBuilder.start(Unknown Source)
```
原因：
```sh
        stage('build code'){
            steps{
                sh '    '
            }
        }
```
在linux下为sh
在win下为bat
应该为
```sh
        stage('build code'){
            steps{
                bat '    '
            }
        }
```

## 错误0825
除了bat和还有其他linux和w的区别 在参数化构建中linux是${premer}, 而win是%premer%


## 备忘
Jenkins的Token值
df8c4073fc92be8a57d0849284a56ce4

个人IP:
10.250.41.183

http://10.250.41.183:10000/

http://47.104.77.127:8080/jenkins/ -auth test:123qwe build test

http://10.250.41.183:10000/job/GM33_Android_pull_build_release/

http://yangzhenxin:df8c4073fc92be8a57d0849284a56ce4@10.250.41.183:10000/job/GM33_Android_pull_build_release/buildWithParameters?token=GM33&CONFIG=Development&RENAME=GM33_Android&EXPLAIN=An available version 

    CURL 发送POST请求


$ curl -d '{"login": "emma", "pass": "123"}' -H 'Content-Type: application/json' http://10.250.41.183:10001/webhook

http://127.0.0.1:10001/webhook

http://10.250.41.183:10020/pre-commit-webhook

```c
print(cd)
```