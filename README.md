# android-shared-preference-utils

Extension of android native Shared Preference Library with support for <strong>Serializable</strong> and <strong>Parcelable</strong> data types.

[![](https://jitpack.io/v/dasBikash84/android-shared-preference-utils.svg)](https://jitpack.io/#dasBikash84/android-shared-preference-utils)

## Dependency

Add this in your root `build.gradle` file (**not** your module `build.gradle` file):

```gradle
allprojects {
	repositories {
        maven { url "https://jitpack.io" }
    }
}
```

Then, add the library to your module `build.gradle`
```gradle
dependencies {
    implementation 'com.github.dasBikash84:android-shared-preference-utils:latest.release.here'
}
```

## Features/Notes
- Support added for `Serializable` and `Parcelable` types.
- Interface for accessing Shared preferences simplified.
- If saved object implements both Serializable & Parcelable then use [`getSerializableData`](https://github.com/dasBikash84/android-shared-preference-utils/blob/master/android-shared-preference-utils/src/main/java/com/dasbikash/android_shared_preference_utils/SharedPreferenceUtils.kt) method to read object from Shared Preferences.

## Usage example

##### Get utils instance for default `Shared Preferences` file:
```
val defaultUtils: SharedPreferenceUtils = SharedPreferenceUtils.getDefaultInstance()
```
##### Get utils instance for custom `Shared Preferences` file:
```
val utils: SharedPreferenceUtils = SharedPreferenceUtils.getInstance("file_name")
```
##### Save and retrieve `primitive(and Wrapper)` data types:
```
    val defaultUtils: SharedPreferenceUtils = SharedPreferenceUtils.getDefaultInstance()
    val INT_SP_KEY = "INT_SP_KEY"
    val DOUBLE_SP_KEY = "DOUBLE_SP_KEY"
    val intData = 10
    val doubleData = 10.0
    
    //save data
    defaultUtils.saveData(context,intData,INT_SP_KEY)
    defaultUtils.saveData(context,doubleData,DOUBLE_SP_KEY)
    
    //read and print data
    defaultUtils.getPrimitiveData(context,INT_SP_KEY,Int::class.java)?.let {
        println(it)
    }
    defaultUtils.getPrimitiveData(context,DOUBLE_SP_KEY,Double::class.java)?.let {
        println(it)
    }
```

##### Save and retrieve `Serializable` data types:

```
    val defaultUtils: SharedPreferenceUtils = SharedPreferenceUtils.getDefaultInstance()
    val SER_SP_KEY = "SER_SP_KEY"
    val student = Student() //Student class implements Serializable

    //save data
    defaultUtils.saveData(context,student,SER_SP_KEY)

    //read and print data
    defaultUtils.getSerializableData(context,SER_SP_KEY,Student::class.java)?.let {
        println(it)
    }
```
##### Save and retrieve `Parcelable` data types:

```
    val defaultUtils: SharedPreferenceUtils = SharedPreferenceUtils.getDefaultInstance()
    val PARCELABLE_SP_KEY = "SER_SP_KEY"
    val student = Student() //Student class implements Parcelable

    //save data
    defaultUtils.saveData(context,student,SER_SP_KEY)

    //read and print data
    defaultUtils.getParcelableData(context,SER_SP_KEY,Student::class.java)?.let {
        println(it)
    }
```
License
--------

    Copyright 2020 Bikash Das(das.bikash.dev@gmail.com)

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
