*Path*: <b><ins>react-components/src/atoms/UploadImages.js</b></ins>

*Change*: 

``` 
{props.thumbnails.length < 5 ? <MiniUpload onUpload={props.onUpload} /> : null}  
```

Replaced with:   

```
{props.thumbnails.length < 3 ? <MiniUpload onUpload={props.onUpload} /> : null}
```

*Digit Change*: Same change is present in latest Digit version