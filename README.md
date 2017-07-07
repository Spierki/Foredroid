# Foredroid

[ ![Download](https://api.bintray.com/packages/steveliles/maven/Foredroid/images/download.svg) ](https://bintray.com/steveliles/maven/Foredroid/_latestVersion)

Utility for detecting and notifying when your Android app goes background / becomes foreground.

API-level 14+.

![logo](https://github.com/steveliles/Foredroid/blob/master/logo_128x128.png?raw=true) 

### Usage:

Initialise Foreground as early as possible in the startup of your app:

    public void onCreate(Bundle savedInstanceState){
      Foreground.init(getApplication());
    }

Any time you want to check if you are foreground or background, just ask:

    Foreground.get().isForeground();
    Foreground.get().isBackground();

Or, if you want to trigger something as soon as possible when you go background or come back 
to foreground, implement Foreground.Listener and do whatever you want in response to the callback methods:

    Foreground.Listener myListener = new Foreground.Listener(){
      public void onBecameForeground(){
        // ... whatever you want to do
      }
      public void onBecameBackground(){
        // ... whatever you want to do
      }
    }
    
... then register your listener:
 
    listenerBinding = Foreground.get().addListener(listener);

Note that in registering the listener we recorded the Binding that was returned, so that we can unbind it again later:

    listenerBinding.unbind();
    
### Maven / Gradle

The .aar file is available from the jcenter repository. Check that you have the jcenter repository in your top-level
build.gradle like this:

    allprojects {
        repositories {
            jcenter()
        }
    }

Add the following dependency to your build.gradle:

    compile 'com.sjl:Foredroid:1.0.1'

