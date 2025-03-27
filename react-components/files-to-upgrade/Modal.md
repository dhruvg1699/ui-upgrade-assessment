*Path*: <b><ins>react-components/src/hoc/Modal.js</b></ins>

*Change*: Some CSS has been changed in E4H

 *Code Changed in E4H*:   

```
 <div className="popup-module-action-bar" style={isOBPSFlow?!mobileView?{marginRight:"18px"}:{position:"absolute",bottom:"5%",right:"10%",left:window.location.href.includes("employee")?"0%":"7%"}:{...popupModuleActionBarStyles, gap:"10px"}}>
```

in place of 

```
<div className="popup-module-action-bar" style={isOBPSFlow?!mobileView?{marginRight:"18px"}:{position:"absolute",bottom:"5%",right:"10%",left:window.location.href.includes("employee")?"0%":"7%"}:popupModuleActionBarStyles}>
```
 
 on `line 53`
 