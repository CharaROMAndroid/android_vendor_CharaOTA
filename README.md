# CharaROM OTA repo
In order for a device to be officially supported by CharaROM, OTA information needs to be added.
Please refer to the following "Readme" to get started

## 1. Introduction ##
In order for a device to be OTA compliant, there are a few things to know.

### 1.1 JSON structure ###
```
{
  "response": [
    {
        "maintainer": "Name (nickname)",
        "oem": "OEM",
        "device": "Device Name",
        "filename": "CharaROM-v<chararom-version>-<date>-<build-type>-Android<android-version>-<chararom-state>-<device>.zip", // example: CharaROM-v1.0-20260401-UNOFFICIAL-Android16-Alpha-dre.zip
        "download": "https://github.com/chararomandroid/android_vendor_CharaOTA/releases/downloads/<code-reference-tag>/CharaROM-v<chararom-version>-<date>-<build-type>-Android<android-version>-<chararom-state>-<device>.zip", // example: https://github.com/CharaROMAndroid/android_vendor_CharaOTA/releases/download/pa2t2/CharaROM-v1.0-20260402-UNOFFICIAL-Android16-Alpha-milanf.zip
        "timestamp": 0000000000,
        "md5": "abcdefg123456",
        "sha256": "abcdefg123456",
        "size": 123456789,
        "version": "<chararomversion>",
        "buildtype": "Experimental/Nightly/Snapshot/Release",
        "forum": "https://forum link", #(mandatory)
        "gapps": "https://gapps link", #(suggested)
        "firmware": "https://firmware link",
        "modem": "https://modem link",
        "bootloader": "https://bootloader link",
        "recovery": "https://recovery link",
        "paypal": "https://donation link",
        "telegram": "https://telegram link",
        "stoat": "https://stoat link", #(optional)
        "dt": "https://github.com/chararomandroid/android_device_<oem>_<device_codename>", #(mandatory)
        "common-dt": "https://github.com/chararomandroid/android_device_<oem>_<SOC>-common", #(mandatory)
        "kernel": "https://github.com/chararomandroid/android_kernel_<oem>_<SOC>" #(mandatory)
    }
  ]
}
```

### 1.2 changelog.txt structure ### 
```
Do NOT change from the automatically generated one.
```

## 2 Guidelines ##
* Check if manufacturer is already existing
* Check if published link is official
* Check if JSON is intact with help of online validator tools like [https://jsonformatter.curiousconcept.com](https://jsonformatter.curiousconcept.com) or [https://jsonformatter.org](https://jsonformatter.org)
* Check if no extra / missing spaces

## 3. How to ##
For following below description, replace *codename* with your device codename. 
### 3.1 Initial support ###
After you contacted [The team on Telegram](https://telegram.me/bunnypaddev), and have the approval, follow the below steps.
1. Fork this repo to your own GitHub.
2. A file named *codename*.json is created in OUT dir after you built.
3. Copy it to where this repo was cloned.
4. Open the file and modify needed entries (see 1.1 for mandatory entries).
5. Create a file named *codename*_changelog.txt based on changelog structure from point 1.2, and add your changelog in it.
6. Submit a pull request to this repo (this way we validate that you understood the requirements and if all is good you'll be granted direct push access to this repo)

### 3.2 Update build ###
1. Clone this repo locally
```
git clone git@github.com:chararomandroid/android_vendor_CharaOTA.git -b hershey
```
2. Change to the directory where you cloned this repo (android_vendor_CharaOTA) and fetch updates from repo.
```
cd android_vendor_CharaOTA
git fetch --all
git pull
```
3. Copy *codename*.json and *codename*_changelog.txt file from OUT dir over to this repo).
3. Now with the files updated, commit your update to this repo.
```
git add .
git commit #(this opens up your prefered text editor, so write a nice description like "<device codename>: update build". If updating multiple devices, write something like *Preferred Name*: Update builds for *codename1* and *codename2*)
git push #you may be prompted for your github username and password
```
