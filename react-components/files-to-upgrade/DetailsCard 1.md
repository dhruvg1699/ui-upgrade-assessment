*Path*: <b><ins>react-components/src/atoms/TopBar.js</b></ins>

*Change*: 

 *Code Changed in E4H*:   

```
<span className="name" style={{overflowWrap:"break-word", color:"black", paddingTop: "16px"}}>{name}</span>
```

Updated on Line 14

```
<style>
{`
 a{
   text-decoration:none
  }
`}
</style>
```

Added after Line 22

```
style={{textDecoration:"none !important", color:"black"}}
```

Added after Line 40

`span` has been replaced with div for class names `label (Line 11)` and `name (Line 14)`

Removed following props `mode="default",apiDetails`  (Line 19)

Added code in `data.map (Line 23)`

```
let key = Object.keys(object)
const incidentId = object[key[0]].props.children
```

`to` property in `link` is changed to:

```
to={window.location.href.includes("im/inbox") ? `/${window.contextPath}/employee/im/complaint/details/` + incidentId + "/" + object["TenantID"]
  : isTwoDynamicPrefix?
  `${linkPrefix}${typeof serviceRequestIdKey === "function"
	?
	serviceRequestIdKey(object)
	:
	`${getRedirectionLink(object["Application Type"] === "BPA_STAKEHOLDER_REGISTRATION" ? "BPAREG" : "BPA")}/${object[object["Application Type"] === "BPA_STAKEHOLDER_REGISTRATION" ? "applicationNo" : "Application Number"]}`}`
  :
  `${linkPrefix}${typeof serviceRequestIdKey === "function"
	?
	serviceRequestIdKey(object)
	  :
	object[serviceRequestIdKey]}`
}
```

The code block from line 72 `Object.keys(object)` is replaced with 

```
{Object.keys(object).filter(rowEle => !(typeof object[rowEle] == "object" && object[rowEle]?.hidden == true)).map((name, index) => {
	  return <Details label={name} name={object[name]} key={index} onClick={() =>handleClickEnabled && handleDetailCardClick(object)} />;
	})}
	{showCitizenInfoLabel ?<CitizenInfoLabel
	  style={{ margin: " 2rem 0px", padding: "10px", backgroundColor: "#FFE2B5", borderRadius: "0.25rem" }}
	  textStyle={{ color: "#CC7B2F" }}
	  info={t("ATM_INFO_LABEL")}
	  text={t(`ATM_INFO_TEXT`)}
	  fill={"#CC7B2F"}
	/>:null}
	{showActionBar ? 
	  <SubmitBar onSubmit={() => handleDetailCardClick(object)} label={submitButtonLabel} />
	:
	null
}
```
