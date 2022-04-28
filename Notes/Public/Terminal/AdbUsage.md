# Adb Usage

## pm

### list all packages
```
adb shell 'pm list packages -f' | grep '/data/app/' | sed -e 's/.*=//'
```

### list all packages and print custom log
```
adb shell 'pm list packages -f' | grep '/data/app/' | sed -e 's/.*=//' | while read comm; do echo "uninstall $comm"; adb uninstall $comm; done;
```

## battery manager
```
adb shell dumpsys package "com.netease.cloudmusic" | grep stopped
```
the result is :
![package battery](./images/batterymg.jpg)

if **stopped** is true , means will not receive in background .

## install ADB from Ubuntu
1. check ubuntu version
```
cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=20.04

DISTRIB_CODENAME=focal

DISTRIB_DESCRIPTION="Ubuntu 20.04.4 LTS"

2. check adb version with Windows pc
```
adb.exe version
```
Android Debug Bridge version 1.0.41

Version 29.0.5-5949299

3. find adb download url

[adb_download](https://androidsdkmanager.azurewebsites.net/Platformtools)

4. download to ubuntu
```
sudo mkdir -p /usr/local/thirdparty/android-sdk
cd /usr/local/thirdparty/android-sdk
sudo curl -OL https://dl.google.com/android/repository/platform-tools_r29.0.5-linux.zip
sudo unzip platform-tools_r29.0.5-linux.zip
sudo ln -s /usr/local/thirdparty/android-sdk/platform-to
ols/adb /usr/bin/adb
export PATH=/usr/local/thirdparty/android-sdk/platform-tools:${PATH}
```