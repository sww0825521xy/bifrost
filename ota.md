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

http://172.31.48.11:8087/upgrade/os/available/hon660/8/0/1/1/1/10
```