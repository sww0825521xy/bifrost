# PIPELINE

### Pipeline glossary

- `Job`: Instructions that a runner has to execute(single test case).
- `Pipeline`: A collection of jobs split into different stages.
- `Runner`: An agent or server that executes each job individually that can spin up or down as needed.
- `Stages`: A keyword that defines certain stages of a job, such as `Verify` and `Stability_Filesystem`. Jobs of the same stage are executed in parallel.

![pipeline](_images/pipeline.png)

### `cats.pipeline`
| PIPELINE_ID| PIPELINE_NAME| STATUS| BRANCH_ID| STAGE_LIST| PIPELINE_EXTRA |
| :----- | :----- | :----- | :----- | :----- | :----- |
|901| P(WB Colderest)| 1| 5| 1,21,2| WB_P |
|902| P(WB Factoryrest)| 1| 5| 1,22,2| WB_P |
|903| P(WB FTP)| 1| 5| 1,23,2| WB_P |
|904| P(WB CameraImage)| 1| 5| 1,24,2| WB_P |
|905| P(WB Filesystem)| 1| 5| 1,25,2| WB_P |
|906| P(WB WWAN)| 1| 5| 26,2| WB_P |
|907| P(WB RadioPower)| 1| 5| 1,27,2| WB_P |
|908| P(WB Speaker)| 1| 5| 1,28,2| WB_P |
|909| P(WB Ebase)| 1| 5| 1,29,2| WB_P |
|910| P(WB Monkey)| 1| 5| 1,31,2| WB_P |
|911| P(WB Camera)| 1| 5| 1,32,2| WB_P |
|912| P(WB Scanner)| 1| 5| 1,33,2| WB_P |
|913| P(WB Battery)| 1| 5| 1,34,2| WB_P |
|914| P(WB OTA)| 1| 5| 1,35,2| WB_P |

### `cats.stage`
| STAGE_ID| STAGE_NAME| STATUS| IS_PARALLEL| PARALLEL| RETRY| ALLOW_FAILURE| BY_CASE_LEVEL| CASE_LEVEL| JOB_LIST| NEED_COMPLETE| STAGE_EXTRA |
| :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- |
| 1| Verify| 1| 0| 1| 0| 0| 1| L0| NULL | 1| NULL |
| 2| Functional| 1| 1| 1| 0| 1| 1| L1,L2| NULL | 1| NULL |
| 21| Stability_ColdReset| 1| 1| 1| 0| 1| 0| L5| ColdReset| 0| NULL |
| 22| Stability_FactoryReset| 1| 1| 1| 0| 1| 0| L5| FactoryReset| 0| NULL |
| 23| Stability_FTP| 1| 1| 1| 0| 1| 0| L5| FTP| 0| NULL |
| 24| Stability_CameraImage| 1| 1| 1| 0| 1| 0| L5| CameraImage| 0| NULL |
| 25| Stability_Filesystem| 1| 1| 1| 0| 1| 0| L5| Filesystem| 0| NULL |
| 26| Stability_WWAN| 1| 1| 1| 0| 1| 0| L5| Wwan Stress Test| 0| NULL |
| 27| Stability_RadioPower| 1| 1| 1| 0| 1| 0| L5| RadioPower| 0| NULL |
| 28| Stability_SpeakerTest| 1| 1| 1| 0| 1| 0| L5| SpeakerTest| 0| NULL |
| 29| Stability_EBase| 1| 1| 1| 0| 1| 0| L5| EBase| 0| NULL |
| 31| Stability_Monkey| 1| 1| 1| 0| 1| 0| L5| Monkey| 0| NULL |
| 32| Stability_Camera| 1| 1| 1| 0| 1| 0| L5| CAMERA L5 Test| 0| NULL |
| 33| Stability_Scanner| 1| 1| 1| 0| 1| 0| L3| Scanner Test| 0| NULL |
| 34| Stability_Battery| 1| 1| 1| 0| 1| 0| L3| Battery Life Test| 0| NULL |
| 35| Stability_OTA_WB| 1| 1| 1| 0| 1| 0| L5| WeeklyOtaUpdate| 0| NULL |
| 180| CTS_O_armeabi-v7a| 1| 0| 1| 0| 0| 0| L8| CTS_O_armeabi-v7a| 1| NULL |
| 181| CTS_Retry_O| 1| 0| 1| 0| 0| 0| L8| CTS_Retry_O| 1| NULL |
| 190| CTS_P_armeabi-v7a| 1| 0| 1| 0| 0| 0| L8| CTS_P_armeabi-v7a| 1| NULL |
| 191| CTS_Retry_P| 1| 0| 1| 0| 0| 0| L8| CTS_Retry_P| 1| NULL |
| 192| CTS_P_arm64-v8a| 1| 0| 1| 0| 0| 0| L8| CTS_P_arm64-v8a| 1| NULL |

### Stage configuration parameters
| Keyword| Description|
| :----- | :----- |
| `IS_PARALLEL`|Parallel dispatch jobs in current stage. `1:true 0:false`|
| `PARALLEL`|How many instances of a job should be run in parallel.|
| `RETRY`|When and how many times a job can be auto-retried in case of a failure. `TODO`|
| `ALLOW_FAILURE`| Allow job to fail. |
| `BY_CASE_LEVEL`| Select jobs by test case level. `1:true 0:false` |
| `CASE_LEVEL`| Test case level. `L0:Platform L1:Smoking L2:Functional L3:Performance L4:NULL L5:Stress L6:CommonES L7:MDM L8:Certification` |
| `JOB_LIST`| Test case name when BY_CASE_LEVEL=0. |
| `NEED_COMPLETE`|  Whether dispatch following stage if current stage fails. `1:true 0:false` |


