# CASE MANAGEMENT {docsify-ignore-all}

## Case Import Interface
```http
http://cd.android.honeywell.com:8080/cats/testcase/auto/import/{hmts_version}
hmts_version : 01.00.00.0199
```
## Case Auto Import Process
1. Jenkins build HMTS and push to Artifactory [HMTS](http://artifactory.android.honeywell.com:8080/artifactory/list/libs-snapshot-local/Honeywell/ADCD/HON660/HMTS/)
2. Jenkins call the auto import interface and pass the hmts version parameter
3. Bifrost service will download `AndroidTest.xml` from Artifactory
4. Parse `AndroidTest.xml` and generate test case command then insert into database

## Test Case Command Example
```json
[
    {
        "type": "adb_push",
        "parameters": [
            {
                "path": "/storage/emulated/0/Download/",
                "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/ADCD/HON660/HMTS/01.00.00.0199/smoking/HMtsSmoking.apk"
            }
        ]
    },
    {
        "type": "adb_push",
        "parameters": [
            {
                "path": "/storage/emulated/0/Download/",
                "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/ADCD/HON660/HMTS/01.00.00.0199/smoking/HMtsSmokingTestCases.apk"
            }
        ]
    },
    {
        "type": "adb_push",
        "parameters": [
            {
                "path": "/storage/emulated/0/Download/",
                "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/ADCD/HON660/HMTS/DeviceInit.jar"
            }
        ]
    },
    {
        "type": "adb_run",
        "parameters": [
            {
                "cmd": "pm install -t -r /storage/emulated/0/Download/HMtsSmoking.apk"
            }
        ]
    },
    {
        "type": "adb_run",
        "parameters": [
            {
                "cmd": "pm install -t -r /storage/emulated/0/Download/HMtsSmokingTestCases.apk"
            }
        ]
    },
    {
        "type": "adb_run",
        "parameters": [
            {
                "cmd": "am instrument -w -r  -e debug false  -e package com.honeywell.hmts.smoking.bluetooth.l1 com.honeywell.hmts.smoking.test/android.support.test.runner.AndroidJUnitRunner"
            }
        ]
    },
    {
        "type": "adb_run",
        "parameters": [
            {
                "cmd": "pm uninstall com.honeywell.hmts.smoking"
            }
        ]
    },
    {
        "type": "adb_run",
        "parameters": [
            {
                "cmd": "pm uninstall com.honeywell.hmts.smoking.test"
            }
        ]
    }
]
```