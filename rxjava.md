---
title: RxJava SA Reconstruction
description: Author - 章成凯 CHENGKAI ZHANG
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

#### Tutorials Used

- [Building Java Libraries](https://guides.gradle.org/building-java-libraries/)
- [A beginners guide to Gradle](https://medium.com/@andrewMacmurray/a-beginners-guide-to-gradle-26212ddcafa8) **INFORMATIVE**

#### Problems Met

```
%USERPROFILE%\Desktop\experiment\gradle\java-lib-demo>gradle init

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
Enter selection (default: basic) [1..10] 7

Select build script DSL:
  1: groovy
  2: kotlin
Enter selection (default: groovy) [1..2] 1

Select test framework:
  1: junit
  2: testng
  3: spock
Enter selection (default: junit) [1..3] 1

Project name (default: java-lib-demo):
Source package (default: java.lib.demo): demo.zck

BUILD SUCCESSFUL in 1m 30s
2 actionable tasks: 2 executed
%USERPROFILE%\Desktop\experiment\gradle\java-lib-demo>gradlew build
> Task :compileJava FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':compileJava'.
> Could not resolve all files for configuration ':compileClasspath'.
   > Could not resolve org.apache.commons:commons-math3:3.6.1.
     Required by:
         project :
      > Could not resolve org.apache.commons:commons-math3:3.6.1.
         > Could not get resource 'https://jcenter.bintray.com/org/apache/commons/commons-math3/3.6.1/commons-math3-3.6.1.pom'.
            > Could not GET 'https://jcenter.bintray.com/org/apache/commons/commons-math3/3.6.1/commons-math3-3.6.1.pom'.
               > socks5://127.0.0.1

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 1s
1 actionable task: 1 executed
```

#### Solutions Tried

- [Set JVM proxy to socks](https://stackoverflow.com/questions/37822473/jmeter-with-socks-proxy) **SOLVED**

Delete those lines to %USERPROFILE%\\.gradle\\gradle.properties

```
systemProp.http.proxyHost=socks5://127.0.0.1
systemProp.http.proxyPort=1080

systemProp.https.proxyHost=socks5://127.0.0.1
systemProp.https.proxyPort=1080
```

#### Tutorials Used

- [Publish gradle java library to JCenter](https://medium.com/@yegor_zatsepin/simple-way-to-publish-your-android-library-to-jcenter-d1e145bacf13) **INFORMATIVE**

#### References

- [Gradle: What is the difference between classpath and compile dependencies?](https://stackoverflow.com/questions/34286407/gradle-what-is-the-difference-between-classpath-and-compile-dependencies)
- [What the difference in applying gradle plugin](https://stackoverflow.com/questions/32352816/what-the-difference-in-applying-gradle-plugin)
- [ext and code block's meaning in the gradle file](https://stackoverflow.com/questions/21696534/ext-and-code-blocks-meaning-in-the-gradle-file)

### Read build.gradle

#### References

- [ext](https://docs.gradle.org/current/dsl/org.gradle.api.Project.html#N150E3)
- [animalsniffer](https://www.mojohaus.org/animal-sniffer/)
- [jmh](http://tutorials.jenkov.com/java-performance/jmh.html)
- [Difference between SCM and SVN](https://stackoverflow.com/questions/5872136/difference-between-scm-and-svn)
- [Implementation Vs Api](https://medium.com/mindorks/implementation-vs-api-in-gradle-3-0-494c817a6fa)

## Learn some basic concepts in RxJava

- [RxJava README](https://github.com/ReactiveX/RxJava) **INFORMATIVE**
- [RxJava Tutorial](https://www.tutorialspoint.com/rxjava/index.htm)
- [Disposable](https://medium.com/@vanniktech/rxjava-2-disposable-under-the-hood-f842d2373e64)
- [FlatMap](http://reactivex.io/documentation/operators/flatmap.html)
- [Difference between Observable.create() and Observable.fromCallable()](https://stackoverflow.com/questions/43785961/difference-between-observable-create-and-observable-fromcallable)
- [Schedulers](https://www.aanandshekharroy.com/articles/2018-01/rxjava-schedulers)
- [doOnNext vs. doOnEach](https://stackoverflow.com/questions/28723341/rxjava-difference-between-doonnext-and-dooneach)
- [subscribeOn vs. observeOn](https://proandroiddev.com/understanding-rxjava-subscribeon-and-observeon-744b0c6a41ea) **INFORMATIVE**
- [flatMap() vs. concatMap() vs. concatMapEager()](https://www.nurkiewicz.com/2017/08/flatmap-vs-concatmap-vs-concatmapeager.html) **INFORMATIVE**
- [flatMap() vs. parallel()](https://www.nurkiewicz.com/2017/09/idiomatic-concurrency-flatmap-vs.html) **INFORMATIVE**
- [blockingSubscribe()](https://stackoverflow.com/questions/44658357/rxjava-scheduler-to-observe-on-main-thread)
- [flatMapSingle()](http://reactivex.io/RxJava/javadoc/io/reactivex/Observable.html#flatMapSingle-io.reactivex.functions.Function-)
- [flatMapIterable()](https://medium.com/@ubuntudroid/rxjava-flattening-a-stream-of-iterables-ea26f593ba07)
- [IgnoreElements()](http://reactivex.io/documentation/operators/ignoreelements.html)
- [andThen()](http://reactivex.io/RxJava/javadoc/io/reactivex/Completable.html#andThen-io.reactivex.ObservableSource-)