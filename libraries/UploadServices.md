*Path*: <b><ins>libraries/src/services/atoms/UploadServices.js</b></ins>

*Change*: Minor code changes

*Code changed in E4H*:

`isVideo = false` argument added in `MultipleFilesStorage` 

`url` field in `config` object for `MultipleFilesStorage` changed to 

```
url: isVideo ? `${Urls.VideoFileUpload}${tenantInfo}` : `${Urls.FileStore}${tenantInfo}`
```

from 

```
url:`${Urls.FileStore}${tenantInfo}`
```
