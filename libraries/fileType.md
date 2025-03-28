*Path*: <b><ins>libraries/src/utils/fileType.js</b></ins>

*Change*: Minor Code change

*Code changed in E4H*:

Code added after `Line 1`

```
if (typeof filestoreURL === "object") {
	if (filestoreURL?.master?.includes(".m3u8")) return "hls";
}
```
