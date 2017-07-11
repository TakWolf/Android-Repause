# Android - Repause #

[![Build Status](https://travis-ci.org/TakWolf/Android-Repause.svg?branch=master)](https://travis-ci.org/TakWolf/Android-Repause)
[![Download](https://api.bintray.com/packages/takwolf/maven/Android-Repause/images/download.svg)](https://bintray.com/takwolf/maven/Android-Repause/_latestVersion)
[![Platform](https://img.shields.io/badge/platform-Android-green.svg?style=flat)](https://www.android.com)
[![API](https://img.shields.io/badge/API-14%2B-brightgreen.svg?style=flat)](https://android-arsenal.com/api?level=14)
[![License](https://img.shields.io/github/license/TakWolf/Android-Repause.svg?style=flat)](http://www.apache.org/licenses/LICENSE-2.0)

A utility to help listen Android application level resumed or paused.

一个用于帮助监听 Android 应用级别恢复或者暂停的工具。

The application level paused, meaning that all of the `Activity` are paused.

This library implements the listening of the application level resumed and paused by adding a delay check task in the `Activity.onPause ()` callback.

The behavior is similar to iOS's `UIApplicationDelegate`.

However, note that the implementation uses the hack way.

Using this library, make sure you have understood the implementation principle.

应用级别暂停，意味着所有的 `Activity` 均处于暂停状态。

这个库通过在 `Activity.onPause()` 回调中添加一个延时检测任务的方式，来实现监听应用级别的恢复和暂停。

行为跟 iOS 的 `UIApplicationDelegate` 类似。

但是请注意，这个实现使用了非常规的方式（hack）。

使用该库，请务必确保您已经了解了实现方式。

Application resumed or paused, is different form application enter foreground or background in concept.

There is another library named [Android-Foreback](https://github.com/TakWolf/Android-Foreback), can listen application enter foreground or background.

If this library is not for you, try another library.

应用暂停恢复和应用前台后台切换，概念上是不同的。

这有另外一个库叫做 [Android-Foreback](https://github.com/TakWolf/Android-Foreback)，用于监听应用进入前台或者后台。

如果本库不适合你，请尝试另外一个库。

## Usage ##

### Gradle ###

``` gradle
compile 'com.takwolf.android:repause:0.0.1'
```

### Java ###

Initialize in `Application.onCreate()`, and register a listener:

请在 `Application.onCreate()` 中初始化，并注册一个监听器：

``` java
public class AppController extends Application implements Repause.Listener {

    @Override
    public void onCreate() {
        super.onCreate();
        Repause.init(this);
        Repause.registerListener(this);
    }

    @Override
    public void onApplicationResumed() {
        // TODO
    }

    @Override
    public void onApplicationPaused() {
        // TODO
    }

}
```

Notice, if register listener in `Activity`, don't forget to unregister to avoid memory leaks.

注意，如果你在 `Activity` 中注册监听器，请不要忘记反注册以避免内存泄露。

Also library provides the following api:

该库也提供下面的 API：

``` java
Repause.isApplicationResumed();
Repause.isApplicationPaused();
```

## Author ##

TakWolf

[takwolf@foxmail.com](mailto:takwolf@foxmail.com)

[http://takwolf.com](http://takwolf.com)

## License ##

```
Copyright 2017 TakWolf

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
