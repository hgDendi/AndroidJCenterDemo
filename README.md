# AndroidJCenterDemo

[中文说明](https://github.com/hgDendi/AndroidJCenterDemo/blob/master/README_CN.md)

Manual on how to upload module to JCenter.

For further information , see [this blog](https://inthecheesefactory.com/blog/how-to-upload-library-to-jcenter-maven-central-as-dependency/en)

Briefly , you can take the following 4 steps to upload your code to JCenter.

## Project#build.gradle

```groovy
buildscript {
    dependencies {
        ...
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.6'
        classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1'
    }
}
```

## LibraryModule#build.gradle

```groovy
apply plugin: 'com.android.library'

ext {
    bintrayRepo = 'testMaven'
    bintrayName = 'mylib'

    publishedGroupId = 'com.hgDendi'
    libraryName = 'MyLib'
    artifact = 'mylib'

    libraryDescription = 'lib test demo'

    siteUrl = 'https://github.com/hgDendi/AndroidJCenterDemo'
    gitUrl = 'https://github.com/hgDendi/AndroidJCenterDemo.git'

    libraryVersion = '1.0.0'

    developerId = 'dendi'
    developerName = 'Dendi Chan'
    developerEmail = 'hg.dendi@gmail.com'

    licenseName = 'The MIT License'
    licenseUrl = 'https://rem.mit-license.org'
    allLicenses = ["MIT"]
}

...

apply from: 'https://raw.githubusercontent.com/hgDendi/AndroidJCenterDemo/master/bintray.gradle'
apply from: 'https://raw.githubusercontent.com/hgDendi/AndroidJCenterDemo/master/maveninstall.gradle'

```

## local.properties

Enter your information in [bintray.com](bintray.com)

```groovy
bintray.user=[...]
bintray.apikey=[...]
bintray.gpg.password=[...]
```

## Upload your code

```
./gradlew install
./gradlew bintrayUpload
```