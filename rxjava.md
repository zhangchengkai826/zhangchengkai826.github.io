---
title: RxJava SA Research
---

# Learn to use RxJava

## Build RxJava from source

```
$ git clone git@github.com:ReactiveX/RxJava.git
$ cd RxJava/
$ ./gradlew build
```

### Learn to use gradle

#### Tutorials Used

- [Creating New Gradle Builds](https://guides.gradle.org/creating-new-gradle-builds/)

#### Problems Met

```
%USERPROFILE%\Desktop\experiment\gradle\basic-demo>gradle init

Welcome to Gradle 5.4.1!

Here are the highlights of this release:
 - Run builds with JDK12
 - New API for Incremental Tasks
 - Updates to native projects, including Swift 5 support

For more details see https://docs.gradle.org/5.4.1/release-notes.html

Starting a Gradle Daemon (subsequent builds will be faster)

Select type of project to generate:
  1: basic
  2: cpp-application
  3: cpp-library
  4: groovy-application
  5: groovy-library
  6: java-application
  7: java-library
  8: kotlin-application
  9: kotlin-library
  10: scala-library
Enter selection (default: basic) [1..10] 1

Select build script DSL:
  1: groovy
  2: kotlin
Enter selection (default: groovy) [1..2] 1

Project name (default: basic-demo):

BUILD SUCCESSFUL in 1m 0s
2 actionable tasks: 2 executed
%USERPROFILE%\Desktop\experiment\gradle\basic-demo>gradlew copy
Downloading https://services.gradle.org/distributions/gradle-5.4.1-bin.zip

Exception in thread "main" java.net.SocketException: Unexpected end of file from server
        at sun.net.www.http.HttpClient.parseHTTPHeader(HttpClient.java:851)
        at sun.net.www.http.HttpClient.parseHTTP(HttpClient.java:678)
        at sun.net.www.protocol.http.HttpURLConnection.doTunneling(HttpURLConnection.java:2055)
        at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:183)
        at sun.net.www.protocol.http.HttpURLConnection.getInputStream0(HttpURLConnection.java:1564)
        at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1492)
        at sun.net.www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:263)
        at org.gradle.wrapper.Download.downloadInternal(Download.java:67)
        at org.gradle.wrapper.Download.download(Download.java:52)
        at org.gradle.wrapper.Install$1.call(Install.java:62)
        at org.gradle.wrapper.Install$1.call(Install.java:48)
        at org.gradle.wrapper.ExclusiveFileAccessManager.access(ExclusiveFileAccessManager.java:69)
        at org.gradle.wrapper.Install.createDist(Install.java:48)
        at org.gradle.wrapper.WrapperExecutor.execute(WrapperExecutor.java:107)
        at org.gradle.wrapper.GradleWrapperMain.main(GradleWrapperMain.java:63)
```

#### Solutions Tried

- [Set gradle proxy to socks](https://discuss.gradle.org/t/how-can-i-set-gradle-proxy-to-socks/15508) **SOLVED**

Add those lines to %USERPROFILE%\\.gradle\\gradle.properties

```
org.gradle.jvmargs=-DsocksProxyHost=127.0.0.1 -DsocksProxyPort=1080

systemProp.http.proxyHost=socks5://127.0.0.1
systemProp.http.proxyPort=1080

systemProp.https.proxyHost=socks5://127.0.0.1
systemProp.https.proxyPort=1080
```