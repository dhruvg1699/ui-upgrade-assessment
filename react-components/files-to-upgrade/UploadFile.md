*Path*: <b><ins>react-components/src/atoms/UploadFile.js</b></ins>

*Change*: 

``` 
{props?.uploadedFiles.length === 0 && <h2 className="file-upload-status">{props.message}</h2>}
```

Replaced with:   

```
{!props?.isUploading && props?.uploadedFiles?.length === 0 && <h2 className="file-upload-status">{props.message}</h2>}
```

`ButtonSelector` label updated with `loader`

```
label={
	props?.isUploading ? (
	 <div className="upload-loader-container">
	   <Loader /> Uploading...
	 </div>
	) : (
	 t("CS_COMMON_CHOOSE_FILE")
	)
}
```
