# HMTS {docsify-ignore-all}

HMTS(Honeywell Mobility Test Suit), Honeywell customized test suit including:
- functional
- smoking
- performance
- stability
- commonES
- MDM
- certification

## HMTS repo 
> [HMTS](https://review.android.honeywell.com:8088/#/admin/projects/ADCD/AndroidAutomationTest)

```bash
git clone ssh://EID@review.android.honeywell.com:29426/ADCD/AndroidAutomationTest
```

## AndroidTest.xml
### target preparer
```xml
    <target_preparer>
        <option name="cleanup-apks" value="true" />
        <option name="test-file-name" value="HMtsFunctional.apk" package="com.honeywell.hmts.functional"/>
        <option name="test-file-name" value="HMtsFunctionalTestCases.apk" package="com.honeywell.hmts.functional.test"/>
    </target_preparer>
```
> - cleanup-apks : whether uninstall apks after test complete
> - test-file-name : test apk to install



### case config
```xml
    <!--Wifi Scan L1 Test-->
    <test name="Wifi Scan Test" caselevel="L2" runtime="60" component="WLAN" class="com.honeywell.hmts.functional.test/android.support.test.runner.AndroidJUnitRunner">
        <option name="package" value="com.honeywell.hmts.functional.wifiscan" />
    </test>
```

### case config with device tag
```xml
   <!--Ebase L1 Test-->
    <test name="Ebase Test" caselevel="L2" runtime="120" component="Ebase" deviceTags="2-222-222212" class="com.honeywell.hmts.functional.test/android.support.test.runner.AndroidJUnitRunner">
        <option name="package" value="com.honeywell.hmts.functional.Ebase" />
    </test>
```
> - deviceTags : default is null or "2-222-222222", test case can be dispatched to any connected device
> - deviceTags pattern : hwFlag - gmsFlag userFlag wwanFlag - simFlag sdFlag IPSMFlag dockFlag ethernetFlag ACFlag
> - hwFlag	EVT1 DVT1 
> - gmsFlag	0:non-gms   1:gms
> - userFlag	0:debug        1:user
> - wwanFlag	0:no wwan   1:wwan
> - simFlag	0:no sim       1:sim
> - sdFlag	0:no sd          1:sd card
> - IPSMFlag	0:no IPSM    1:IPSM
> - dockFlag	0:undock      1:docked
> - ethernetFlag	0:no eth        1:eth
> - ACFlag	0:no AC         1:AC


### stress test case config
```xml
    <!--Cold Reset Test-->
    <test name="ColdReset" caselevel="L5" runtime="86400" component="Reset" deviceTags="" class="com.honeywell.action.hmts.RUN_STRESS">
        <option name="param" value="{'package': 'coldrest','runtime': '24','interval': '10'}" />
    </test>
```
> - value : value in JSON format, field package and runtime is mandatory

### module certification test case config
trigger CTS single module
```xml
    <!--CtsKeystoreTestCases for Android P-->
    <test name="CtsKeystoreTestCases" caselevel="L8" runtime="86400" component="Certification-CTS" platform="P" type="trigger">
        <option name="cmd" value="run cts --module CtsKeystoreTestCases -s %s " />
    </test>
```

### single certification test case config
```xml
        <!--HardwareAccelerationTest#testIsHardwareAccelerated for Android P-->
    <test name="IsHardwareAccelerated" caselevel="L8" runtime="86400" component="Certification-CTS" platform="P" type="trigger">
        <option name="cmd" value="run cts --module CtsAccelerationTestCases --test android.acceleration.cts.HardwareAccelerationTest#testIsHardwareAccelerated -s %s " />
    </test>
```


### certification test case config
```xml
    <!--CTS for Android P arm64-v8a -->
    <test name="CTS_P_arm64-v8a" caselevel="L8" runtime="86400" component="Certification-CTS" platform="P" type="trigger">
        <option name="cmd" value="run cts -a arm64-v8a -s %s " />
    </test>
```


### certification retry config
```xml
    <!--CTS retry for Android P-->
    <test name="CTS_Retry_P" caselevel="L8" runtime="86400" component="Certification-CTS" platform="P" type="retry">
        <option name="cmd" value="run retry --retry %s -s %s" />
    </test>
```

### certification shard config
```xml
    <!--CTS shard for Android P-->
    <test name="CTS_Shard_P" caselevel="L8" runtime="86400" component="Certification-CTS" platform="P" type="shard">
        <option name="cmd" value="run cts --shard-count %s -s %s" />
    </test>
```



