# AGENT
Bifrost supports two modes: `direct mode` and `slave mode`.
- Direct mode: device install android agent, agent will connect to the server directly and receive commands from server
- Slave mode: PC install a bare metal agent, android device connect to the PC via USB cable, bare metal agent connect to the server and receive commands from server then dispatch commands to tether devices

### Common Support Commands
- `install_OTA` (agnet will download OTA from specific URL, then device will use HUpgrader to upgrade)

```json
{
    "type": "install_OTA",
    "parameters": [
        {
            "url": "http://artifactory.android.honeywell.com:8080/artifactory/android-weekly-build/Honeywell/Hon660Android/pie-release-stage/88.00.04-WB-(0004)/otas/user/HON660-P-88.00.04-WB-(0004).zip"
        }
    ]
}
```

- `reboot` (reboot device or tether device)

```json
{
    "type": "reboot",
    "parameters": [
        {
            "cmd": "reboot"
        }
    ]
}

```
- `factory_reset` (factory reset, erase IPSM {"IPSM": "1"} erase sdcard {"sdcard": "0"})

```json
{
    "type": "factory_reset",
    "parameters": [
        {
            "IPSM": "0",
            "sdcard": "0"
        }
    ]
}
```

- `adb_push` (download file and push to device specific path)

```json
{
    "type": "adb_push",
    "parameters": [
        {
            "path": "/storage/emulated/0/Download/",
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/ADCD/HON660/HMTS/01.00.00.0199/smoking/HMtsSmoking.apk"
        }
    ]
}
```

- `adb_run` (adb shell command)

```json
{
    "type": "adb_run",
    "parameters": [
        {
            "cmd": "pm install -t -r /storage/emulated/0/Download/HMtsSmoking.apk"
        }
    ]
}
```

### Bare metal Specific Support Command
- `certification_run`

```json
{
    "type": "certification_run",
    "parameters": [
        {
            "cmd": "run cts -s %s"
        }
    ]
}
```

## Android Agent
Download from code repo and Import into Android Studio
> [Repo](https://review.android.honeywell.com:8088/#/admin/projects/ADCD/Agent)

### Android Agent Architecture
Android Agent contains two module: 
- connect, auto connect to Wifi and connect to the server via WebSocket
 - status  `1:idle`  `50:running` `51:complete`
 - dispatch parse receive message and dispatch message via module name

- bifrost, deal with bifrost specific commands
 - module name(`CATS`), deal with message with modulw name `CATS`
 - parse commands and insert into sqlite
 - execute command step by step
 - upload test result and device log to server

## Bare metal Agent
### Download from code repo and Import into Eclipse
> [Repo](https://review.android.honeywell.com:8088/#/admin/projects/ADCD/bifrost-agent)

### Build
```bash
mvn install
```

### Run (Windows and Linux platform)
```bash
java -jar agent-0.0.1-SNAPSHOT.jar
```

