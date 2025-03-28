*Path*: <b><ins>react-components/src/atoms/RemoveableTag.js</b></ins>

*Change*: Some CSS has been added in E4H

*Code Changed in E4H*:

```
 <div className="tag" style={{height:"auto"}} >
     <span className="text" style={{height:"auto"}}>{text}</span>
```

*Code Replaced*: 

```
<div className="tag" style={extraStyles?extraStyles?.tagStyles:{}} >
     <span className="text" style={extraStyles?extraStyles?.textStyles:{}}>{text}</span>
```

All `setStates` in `onSelect (Line 163)` moved out of `if statement` and added at top
*Code Added:*

```
setSelectedOption(val);
setDropdownStatus(false);
setFilterVal("")
```