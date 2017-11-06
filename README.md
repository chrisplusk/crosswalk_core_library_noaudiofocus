### Set up chromium depot tools:
http://commondatastorage.googleapis.com/chrome-infra-docs/flat/depot_tools/docs/html/depot_tools_tutorial.html#_setting_up

      git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
      export PATH=$PATH:/path/to/depot_tools

### Then follow these instructions to get and build crosswalk for android:
https://crosswalk-project.org/contribute/building_crosswalk/android_build.html

### Apply code changes from this repo to crosswalk src.

### Build and include the resulting xwalk_core_library.aar in your project instead of the [maven repository](https://download.01.org/crosswalk/releases/crosswalk/android/maven2)

For Cordova projects I put it in

      /platforms/android/libs/
      
and modified

      /platforms/android/cordova-plugin-crosswalk-webview/hellocordova-xwalk.gradle
```
repositories {
      //maven {
        //url xwalkMavenRepo
      //}
        flatDir { 
         dirs '/libs'
        }
    }
    
...

dependencies {
        //compile xwalkSpec
        compile(name:'xwalk_core_library', ext:'aar')
    }
```
