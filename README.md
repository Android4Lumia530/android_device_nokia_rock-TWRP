# TWRP tree for Nokia Lumia 530 (2014)

## Dependencies:
(you probably don't need most of these)
```
sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-6-jdk openjdk-6-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev
sudo apt-get install g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
You also need the repo tool for cloning Android source trees.

## Set up and get the repo:
```
mkdir ~/omni-twrp-tree
cd ~/omni-twrp-tree
repo init -u https://github.com/sultanqasim/twrp_recovery_manifest.git -b android-7.1
mkdir -p .repo/local_manifests
```

Create a file .repo/local\_manifests/rock.xml and paste this in
```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
    <project name="sonic011gamer/android_device_microsoft_chakra-TWRP" path="device/nokia/rock" remote="github" revision="twrp" />
    <project name="Android4Lumia530/linux-next" path="kernel/nokia/rock" remote="github" revision="530" />
</manifest>
```

Now fetch the code
```
repo sync
```

## Building:
```
source build/envsetup.sh
lunch omni_rock-userdebug
make clean
make installclean
make -j10 recoveryimage
```
