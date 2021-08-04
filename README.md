# Location Kit

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/dev.supasintatiyanupanwong.libraries.android.kits.location/location-core/badge.svg)](https://search.maven.org/search?q=g:dev.supasintatiyanupanwong.libraries.android.kits.location)
[![javadoc](https://javadoc.io/badge2/dev.supasintatiyanupanwong.libraries.android.kits.location/location-core/javadoc.svg)](https://javadoc.io/doc/dev.supasintatiyanupanwong.libraries.android.kits.location/location-core)
[![license](https://img.shields.io/github/license/SupasinTatiyanupanwong/location-kit-android.svg)](https://www.apache.org/licenses/LICENSE-2.0)

Location Kit is an abstraction wrapper that encapsulates Google Location Services and HUAWEI Location Kit.

## Architecture

The library consists of 3 artifacts; `location-core`, `location-google`, and `location-huawei`.

`location-core` artifact provides an abstraction interface to interact with Location APIs.

`location-google` artifact provides the Google Location Services integration to Location Kit.

`location-huawei` artifact provides the HUAWEI Location Kit integration to Location Kit.

Each artifact transitively depended on its corresponding [base](https://github.com/SupasinTatiyanupanwong/android-kits-base) artifacts.

## Declaring dependencies

To add a dependency on Location Kit, you must add the Maven Central repository together with the Google Maven repository and/or the Huawei Maven repository to your project.

Add the dependencies for the artifacts you need in the `build.gradle` file for your app or module:

```groovy
dependencies {
    // To use the Google Location Services via Location Kit
    implementation 'dev.supasintatiyanupanwong.libraries.android.kits.location:location-google:1.0.0'

    // To use the HUAWEI Location Kit via Location Kit
    implementation 'dev.supasintatiyanupanwong.libraries.android.kits.location:location-huawei:1.0.0'
}
```

If both of integration artifacts are included in your final build, the implementation will be selected based on API availability upon application startup.

However, it is recommended to separate builds between them as next:

```groovy
android {
    // ...
    flavorDimensions 'vendor'
    productFlavors {
        google
        huawei { applicationIdSuffix '.huawei' }
    }
}

dependencies {
    googleImplementation 'dev.supasintatiyanupanwong.libraries.android.kits.location:location-google:1.0.0'
    huaweiImplementation 'dev.supasintatiyanupanwong.libraries.android.kits.location:location-huawei:1.0.0'
}
```

But, make sure to have one of the integration artifacts included in your final build, otherwise an exception will be thrown at runtime.

For more information about dependencies, see [Add build dependencies](https://developer.android.com/studio/build/dependencies).

## Additional documentation

* [Build location-aware apps - Android Developer](https://developer.android.com/training/location/index.html)
* [Location Kit - HMS Core - HUAWEI Developer](https://developer.huawei.com/consumer/en/hms/huawei-locationkit/)

## Feedback

Your feedback helps make Location Kit better. Let us know if you discover new issues or have ideas for improving this library.
Please take a look at the [existing issues](https://github.com/SupasinTatiyanupanwong/location-kit-android/issues) or the [existing discussions](https://github.com/SupasinTatiyanupanwong/location-kit-android/discussions) in this library before you create a new one.

## License

```
Copyright 2020 Supasin Tatiyanupanwong

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

### Author:
[Adriano Pires](https://github.com/agspires/)