Following steps can be used to copy data to labelstudio from your local volume: 

1. Install s3cmd

2. Set up s3cmd config (`~/.s3cfg`): 

```
host_base = s3.waw3-1.cloudferro.com
host_bucket = 
access_key = xx
secret_key = xx
use_https = True
check_ssl_certificate = False
```

3. Create a new bucket using following naming convection: 
```
s3cmd mb s3://labelstudio-projectname-input
```
where _projectname_ is your project name in label studio. 

4. Set up CORS configuration for the bucket, first create following `cors.xml` file:
```
<CORSConfiguration>
    <CORSRule>
        <AllowedOrigin>*</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <AllowedHeader>*</AllowedHeader>
        <MaxAgeSeconds>3600</MaxAgeSeconds>
        <ExposeHeaders>x-amz-server-side-encryption</ExposeHeaders>
        <ExposeHeaders>x-amz-request-id</ExposeHeaders>
        <ExposeHeaders>x-amz-id-2</ExposeHeaders>
    </CORSRule>
</CORSConfiguration>
```
and then set it to the bucket: `s3cmd setcors cors.xml s3://labelstudio-projectname-input`

4. Copy data from your local disc to the bucket: 
```
s3cmd put --recursive source/ s3://labelstudio-projectname-input/
```

5. Configure your label studio project input following this guide: https://labelstud.io/guide/storage#Set-up-connection-in-the-Label-Studio-UI with following information: 

|field| Value |
| --------- | ----------|  
|S3 Endpoint | https://s3.waw3-1.cloudferro.com|
|Bucket name | The one created above|
|Bucket Prefix |  |
|Session Token | leave empty |
|Access Key Id & Secret Access Key | as in rclone config |
|Treat every bucket object as a source file | yes (unless you have configured the task configuration jsons)|
|Use pre-signed URLs| yes |


![label studio conf](images/ls-s3-1.png)

![label studio conf](images/ls-s3-2.png)

![label studio conf](images/ls-s3-3.png)



