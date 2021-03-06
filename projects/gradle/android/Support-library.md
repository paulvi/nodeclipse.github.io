---
layout: gradle
title: Nodeclipse/Enide Gradle for Eclipse - Android
---

# Gradle for Eclipse - Android

<p></p>

Back to [Android](./) page

### Support library

While with gradle-based build system adding support library is as simple as adding

	compile 'com.android.support:appcompat-v7:19.0.+'
	
inside app's `build.gradle` dependencies block,  
for Eclipse with ADT it should be as referenced project listed in `project.properties`.

`E:\Android\sdk` below is example location specified in you `ANDROID_HOME` environment variable.

`sdk\extras\android\support\v7\appcompat` contains template for "appcompat_v7" (<name>android-support-v7-appcompat</name>) project,
that is copied into workspaces once you create a project,
that requires support library, e.g. by setting minSdk to 8.

Contrary to m2repository `extras\android\support` contains only one revision of the library.
So when you upgrade SDK, added "appcompat_v7" project will be copied from newer template.

#### Support library revision conflicts

1. If you have `android-support-v4.jar` in `libs` folder check that in your `dependencies` block 
`fileTree` has `exclude`:

	compile fileTree(dir: 'libs', include: '*.jar', exclude: 'android-support-*.jar')
	
2. Some gradle dependencies may have transitive dependency on support library of other revision 
(e.g. rev 19 while you using rev 21). Check with `gradle -q dependencies` and add
`{ exclude module: 'support-v4'}`, for example

	compile('com.company:superlib:1.0.0') { exclude module: 'support-v4'}

See [Multiple dex files define Landroid/support/v4/accessibilityservice/AccessibilityServiceInfoCompat](http://stackoverflow.com/questions/20989317/multiple-dex-files-define-landroid-support-v4-accessibilityservice-accessibility)

Other option is to to use `resolutionStrategy` at root `build.gradle` 
[ref](http://stackoverflow.com/questions/27965690/gradle-exclude-or-add-reference-for-jar-file-hard-included-inside-library-classe)

	allprojects {
	    configurations.all((Closure) {
	        resolutionStrategy {
	            force 'com.android.support:support-v4:21.0.2' // your version of support library
	        }
	    })	
	} 		

#### Adding sources

##### for Eclipse

`E:\Android\sdk\extras\android\support\v7\appcompat\libs`

add `android-support-v4.jar.properties`

> src=E:\\Android\\sdk\\extras\\android\\support\\v4\\src

and `android-support-v7-appcompat.jar.properties`

> src=E:\\Android\\sources\\platform_frameworks_support\\v7\\appcompat\\src

While v4 lib sources should be once you get "Extra / Android Support Library" via 
[SDK Manager](https://developer.android.com/tools/support-library/setup.html),
for v7 sources you should (from e.g. e:\\Android\\sources folder )

    git clone https://github.com/android/platform_frameworks_support.git

For Gradle usage get "Extra / Android Support Repository".

.aar files appear e.g. in `E:\Android\sdk\extras\android\m2repository\com\android\support`
but again without sources.

##### for Android Studio

Inside `app/build.gradle`

	apply plugin: 'idea'
	idea {
	    module{
	        sourceDirs += file("E:\\Android\\sdk\\extras\\android\\support\\v4\\src\\")
	        sourceDirs += file("E:\\Android\\sources\\platform_frameworks_support\\v7\\appcompat\\src")
	    }
	}

[1](http://stackoverflow.com/questions/27599536/android-studio-how-to-see-sources-for-android-support-v4-and-v7)
	