*Path*: <b><ins>react-components/src/molecules/DetailsCard.js</b></ins>

*Change*: Some CSS has been added in E4H

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

in place of 

```
_searchResults : <Link to={Digit?.Customizations?.[apiDetails?.masterName]?.[apiDetails?.moduleName]?.MobileDetailsOnClick(row.mapping, tenantId)}>
```
