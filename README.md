# iOS-Build-Number-Overlay
Overlay version and build numbers in your release builds.

This is a simple bash script usage demostration to auto tag your app icons with version and build number in the format like.

    VersionNumber(BuildNumber)
    ex: 1.0(2)
    
![alt tag](https://raw.githubusercontent.com/madnik/iOS-Build-Number-Overlay/master/screenshot.png)

## Setting Up
This depends on the popular image processing library `ImageMagick`. You can use homebrew to install it.
If you don't have homebrew installed have [HomeBrew](http://brew.sh/) first.

Lets brew it.

    brew install ImageMagick
    brew install ghostscript
    
If anything go wrong. Try

    brew doctor
    
Clone the repository and open build phases for your target. Wait a minute if you know what you are doing and lazy to clone here you got a gist for scripts. [Overlay Gist](https://gist.github.com/3ec45a168247fcc616c0.git)

If you cloned it already. Let me explain you. You will see 2 run scripts at build phases. 1 before copy bundle resources build phase and one after.

Please select you shell properly. I'm using zsh thats make it `/bin/zsh`. Most probably it will be `/bin/sh` for you. Very important to change it. 

If all set. When you archive project. It will change your AppIcons to have build and version number overlay on it. I made it only for release builds because when you debug it is not necessary to do this. When you do archive the build configuration will be `Release`. So the function get executed. 

First script will take images from reference icon set and replace actual icons. 
Second script will increase the build number after a release is made. This prepare the build number for next release. 
Note that reference icon set `AppIconReference.xcassets` in not added to our target. Not to any target. Its whole purpose is to have original icons for us. 

There are many ways to do this. You can also avoid having a reference icon set and directly convert icons to build product target. Play with it and adjust to your needs.


