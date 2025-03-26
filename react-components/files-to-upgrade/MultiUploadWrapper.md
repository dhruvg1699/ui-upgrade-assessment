*Path*: <b><ins>react-components/src/molecules/MultiUploadWrapper.js</b></ins>

*Change*: Some code has been added in E4H

 *Code Changed in E4H*:   
 
```
disabled, ulb
```

Added in props

```
 e.preventDefault()
```

Added in onUploadMultipleFiles function

```
const { data: { files: fileStoreIds } = {} } = await Digit.UploadServices.MultipleFilesStorage(module, e.target.files, tenantId)
```

Replaced with 

```
let tenant = ulb || Digit.SessionStorage.get("Employee.tenantId")
const { data: { files: fileStoreIds } = {} } = await Digit.UploadServices.MultipleFilesStorage(module, e.target.files, tenant)
```
 
 On Line 101

```
disabled={disabled}
ulb={ulb}
```

Added in UploadFile Component Call