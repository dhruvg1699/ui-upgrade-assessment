*Path*: <b><ins>react-components/src/atoms/DisplayPhotos.js</b></ins>

*Change*: Added a '?' on `line 146`

*Code Change in E4H*:

```
(props?.option && props?.option?.filter((option) => t(option?.[props.optionKey])?.toUpperCase()?.indexOf(filterVal?.toUpperCase()) > -1)) || [];
```
