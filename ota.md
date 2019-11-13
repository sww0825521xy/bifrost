# OTA
Service for query available OS images in Artifactoy

```http
	/**
	 * 
	 * @param device_name
	 * @param osVer
	 * @param branch 0:master 1:release 3:weekly build
	 * @param gmsFlag 0:non-gms 1:gms
	 * @param userFlag 0:userdebug 1:user
	 * @param page current page
	 * @param pageSize page display size
	 * @return
	 */
http://172.31.48.11:8087/upgrade/os/available/{device_name}/{android_version}/{branch}/{gms_flag}/{user_flag}/{page}/{pageSize}

```
http://172.31.48.11:8087/upgrade/os/available/hon660/8/0/1/1/1/10

```json
{
    "resultCode": "200",
    "resultDesc": "Success",
    "buildInfo": [
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0837)/otas/user/HON660-O-86.00.00-(0837).zip",
            "version": "86.00.00-(0837)",
            "brief": null,
            "createTime": "2019-11-13T05:18:33.612+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0834)/otas/user/HON660-O-86.00.00-(0834).zip",
            "version": "86.00.00-(0834)",
            "brief": null,
            "createTime": "2019-11-09T04:14:48.819+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0833)/otas/user/HON660-O-86.00.00-(0833).zip",
            "version": "86.00.00-(0833)",
            "brief": null,
            "createTime": "2019-11-08T06:13:11.154+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0832)/otas/user/HON660-O-86.00.00-(0832).zip",
            "version": "86.00.00-(0832)",
            "brief": null,
            "createTime": "2019-11-07T04:45:54.684+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0831)/otas/user/HON660-O-86.00.00-(0831).zip",
            "version": "86.00.00-(0831)",
            "brief": null,
            "createTime": "2019-11-06T04:26:34.605+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0830)/otas/user/HON660-O-86.00.00-(0830).zip",
            "version": "86.00.00-(0830)",
            "brief": null,
            "createTime": "2019-11-05T04:26:18.694+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0829)/otas/user/HON660-O-86.00.00-(0829).zip",
            "version": "86.00.00-(0829)",
            "brief": null,
            "createTime": "2019-11-03T04:37:37.351+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0828)/otas/user/HON660-O-86.00.00-(0828).zip",
            "version": "86.00.00-(0828)",
            "brief": null,
            "createTime": "2019-11-02T04:12:01.483+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0827)/otas/user/HON660-O-86.00.00-(0827).zip",
            "version": "86.00.00-(0827)",
            "brief": null,
            "createTime": "2019-11-01T04:43:38.037+08:00"
        },
        {
            "url": "http://172.31.48.19:8080/artifactory/libs-snapshot-local/Honeywell/Hon660Android/oreo-master/86.00.00-(0825)/otas/user/HON660-O-86.00.00-(0825).zip",
            "version": "86.00.00-(0825)",
            "brief": null,
            "createTime": "2019-10-31T04:05:42.787+08:00"
        }
    ],
    "pageInfo": {
        "totalPage": 6,
        "prePage": 1,
        "nextPage": 2,
        "totalRec": 52,
        "pageSize": 10,
        "pageIndex": 1,
        "pageNumbers": null
    }
}
```