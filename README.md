### build 一个android项目

git@github.com:iwmobileapplab/Androxy.git

### 找到一个build盒子
https://github.com/mingchen/docker-android-build-box

### clone项目
git clone git@github.com:iwmobileapplab/Androxy.git

切换目录
cd Androxy/

### 拉镜像
docker pull mingc/android-build-box:latest

mingc/android-build-box                latest                                     10f68e166664   44 hours ago    14.6GB

15G的镜像，真是恐怖

### 试着来一下
cd <android project directory>  # change working directory to your project root directory.
docker run --rm -v `pwd`:/project mingc/android-build-box bash -c 'cd /project; ./gradlew build'



### 一顿输出
Downloading https://services.gradle.org/distributions/gradle-6.5-bin.zip
.................................................................................................
Unzipping /root/.gradle/wrapper/dists/gradle-6.5-bin/6nifqtx7604sqp1q6g8wikw7p/gradle-6.5-bin.zip to /root/.gradle/wrapper/dists/gradle-6.5-bin/6nifqtx7604sqp1q6g8wikw7p
Set executable permissions for: /root/.gradle/wrapper/dists/gradle-6.5-bin/6nifqtx7604sqp1q6g8wikw7p/gradle-6.5/bin/gradle

Welcome to Gradle 6.5!

Here are the highlights of this release:
 - Experimental file-system watching
 - Improved version ordering
 - New samples

For more details see https://docs.gradle.org/6.5/release-notes.html

Starting a Gradle Daemon (subsequent builds will be faster)
> Task :app:preBuild UP-TO-DATE
> Task :app:preDebugBuild UP-TO-DATE
> Task :app:compileDebugAidl NO-SOURCE
> Task :app:generateDebugBuildConfig
> Task :app:compileDebugRenderscript NO-SOURCE
> Task :app:checkDebugAarMetadata
> Task :app:generateDebugResValues
> Task :app:generateDebugResources
> Task :app:createDebugCompatibleScreenManifests
> Task :app:extractDeepLinksDebug
> Task :app:processDebugMainManifest
> Task :app:processDebugManifest
> Task :app:mergeDebugNativeDebugMetadata NO-SOURCE
> Task :app:javaPreCompileDebug
> Task :app:processDebugManifestForPackage
> Task :app:mergeDebugShaders
> Task :app:compileDebugShaders NO-SOURCE
> Task :app:generateDebugAssets UP-TO-DATE
> Task :app:mergeDebugResources
> Task :app:mergeDebugAssets
> Task :app:processDebugResources

> Task :app:compileDebugKotlin
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (4, 27): 'PreferenceManager' is deprecated. Deprecated in Java
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (15, 24): 'PreferenceManager' is deprecated. Deprecated in Java
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (15, 42): 'getDefaultSharedPreferences(Context!): SharedPreferences!' is deprecated. Deprecated in Java

> Task :app:compileDebugJavaWithJavac
> Task :app:compileDebugSources
> Task :app:compressDebugAssets
> Task :app:processDebugJavaRes NO-SOURCE
> Task :app:mergeDebugJavaResource
> Task :app:checkDebugDuplicateClasses
> Task :app:desugarDebugFileDependencies
> Task :app:mergeLibDexDebug
> Task :app:dexBuilderDebug
> Task :app:mergeDebugJniLibFolders
> Task :app:mergeProjectDexDebug
> Task :app:validateSigningDebug
> Task :app:preReleaseBuild UP-TO-DATE
> Task :app:compileReleaseAidl NO-SOURCE
> Task :app:mergeDebugNativeLibs
> Task :app:compileReleaseRenderscript NO-SOURCE
> Task :app:stripDebugDebugSymbols NO-SOURCE
> Task :app:generateReleaseBuildConfig
> Task :app:checkReleaseAarMetadata
> Task :app:generateReleaseResValues
> Task :app:generateReleaseResources
> Task :app:mergeExtDexDebug
> Task :app:createReleaseCompatibleScreenManifests
> Task :app:extractDeepLinksRelease
> Task :app:processReleaseMainManifest
> Task :app:processReleaseManifest
> Task :app:javaPreCompileRelease
> Task :app:processReleaseManifestForPackage
> Task :app:mergeReleaseNativeDebugMetadata NO-SOURCE
> Task :app:mergeReleaseShaders
> Task :app:compileReleaseShaders NO-SOURCE
> Task :app:generateReleaseAssets UP-TO-DATE
> Task :app:mergeReleaseAssets
> Task :app:compressReleaseAssets
> Task :app:checkReleaseDuplicateClasses
> Task :app:packageDebug
> Task :app:assembleDebug
> Task :app:mergeReleaseResources
> Task :app:processReleaseResources

> Task :app:compileReleaseKotlin
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (4, 27): 'PreferenceManager' is deprecated. Deprecated in Java
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (15, 24): 'PreferenceManager' is deprecated. Deprecated in Java
w: /project/app/src/main/java/com/android/example/androxy/AppPreference.kt: (15, 42): 'getDefaultSharedPreferences(Context!): SharedPreferences!' is deprecated. Deprecated in Java

> Task :app:compileReleaseJavaWithJavac
> Task :app:compileReleaseSources
> Task :app:lintVitalRelease SKIPPED
> Task :app:dexBuilderRelease
> Task :app:desugarReleaseFileDependencies
> Task :app:processReleaseJavaRes NO-SOURCE
> Task :app:mergeReleaseJavaResource
> Task :app:collectReleaseDependencies
> Task :app:sdkReleaseDependencyData
> Task :app:mergeReleaseJniLibFolders
> Task :app:mergeReleaseNativeLibs
> Task :app:lint

### 报错

> Task :app:lint FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:lint'.
> Could not resolve all files for configuration ':app:lintClassPath'.
   > Could not resolve com.android.tools.lint:lint-gradle:27.1.3.
     Required by:
         project :app
      > Could not resolve com.android.tools.lint:lint-gradle:27.1.3.
         > Could not get resource 'https://dl.google.com/dl/android/maven2/com/android/tools/lint/lint-gradle/27.1.3/lint-gradle-27.1.3.pom'.
            > Could not GET 'https://dl.google.com/dl/android/maven2/com/android/tools/lint/lint-gradle/27.1.3/lint-gradle-27.1.3.pom'.
               > Connect to dl.google.com:443 [dl.google.com/203.208.39.193] failed: Read timed out



网络连接问题，再试一次

### 交互模式
docker run -v `pwd`:/project -it mingc/android-build-box bash

export http_proxy='http://xxxxx:13128'
export https_proxy='https://xxxx:13128'

./gradlew build


### 可以访问cache的方式
docker run --rm -v `pwd`:/project  -v "$HOME/.dockercache/gradle":"/root/.gradle"   mingc/android-build-box bash -c 'cd /project; ./gradlew build'

docker run --rm -v `pwd`:/project --env HTTP_PROXY="http://192.168.50.232:13128" --env HTTPS_PROXY="https://192.168.50.232:13128"  mingc/android-build-box bash -c 'cd /project; ./gradlew build'


### 快速验证ip
curl -s http://whatismyip.akamai.com/


### 成功了
BUILD SUCCESSFUL in 4m 3s
63 actionable tasks: 14 executed, 49 up-to-date

4分钟才能build出来，是真的累啊

然后在
app/build/outpus/apk/debug下，找到了abk啊
只能把debug包才能安装成功

### 安装adb
https://medium.com/macoclock/launch-adb-installed-by-homebrew-on-macos-59d87f4336c9

brew install --cask  android-platform-tools

==> Downloading https://dl.google.com/android/repository/platform-tools_r33.0.2-darwin.zip
######################################################################## 100.0%
==> Installing Cask android-platform-tools
==> Linking Binary 'sload_f2fs' to '/usr/local/bin/sload_f2fs'
==> Linking Binary 'dmtracedump' to '/usr/local/bin/dmtracedump'
==> Linking Binary 'e2fsdroid' to '/usr/local/bin/e2fsdroid'
==> Linking Binary 'etc1tool' to '/usr/local/bin/etc1tool'
==> Linking Binary 'fastboot' to '/usr/local/bin/fastboot'
==> Linking Binary 'hprof-conv' to '/usr/local/bin/hprof-conv'
==> Linking Binary 'make_f2fs' to '/usr/local/bin/make_f2fs'
==> Linking Binary 'make_f2fs_casefold' to '/usr/local/bin/make_f2fs_casefold'
==> Linking Binary 'mke2fs' to '/usr/local/bin/mke2fs'
==> Linking Binary 'adb' to '/usr/local/bin/adb'
🍺  android-platform-tools was successfully installed!
(base) lemonhall@mac-book-pro:~/Androxy$


### usb连接手机
https://blog.csdn.net/ckckjsws/article/details/123849295
参考这个

adb devices
用这个验证好有设备了
执行命令
adb shell pm grant com.android.example.androxy android.permission.WRITE_SECURE_SETTINGS

赋予权限

### 好嘞

安装完毕之后这个app有设置快捷方式的能力
这就很方便，可以全局下滑后打开或者关闭设置，简单多了是不是？

嘿嘿






