*Path*: <b><ins>react-components/src/atoms/UploadFile.js</b></ins>

*Change*: 

``` 
{props?.uploadedFiles.length === 0 && <h2 className="file-upload-status">{props.message}</h2>}
```

Replaced with:   

```
{props?.uploadedFiles?.length === 0 && <h2 className="file-upload-status">{props.message}</h2>}
```

*Digit Change*: Same change is present in latest Digit version