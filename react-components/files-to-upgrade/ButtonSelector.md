*Path*: <b><ins>react-components/src/atoms/ButtonSelector.js</b></ins>

*Change*: Code & CSS change in E4H

 *Code added in E4H*:   
 
```
const isMobile = window.Digit.Utils.browser.isMobile();
const language=JSON.parse(sessionStorage.getItem("Digit.locale"))?.value
```

Added after `line 5`
 
```
style={props.style ? {...props.style,height:"3rem", paddingLeft:isMobile && language==="ka_IN" ? "10px":"24px", paddingRight:isMobile && language==="ka_IN" ? "10px":"24px"} : null}
```

Replaced in `style` object on `line 21` (`<button>` tag)