*Path*: <b><ins>react-components/src/atoms/NavBar.js</b></ins>

*Change*: Image with class name bannerLogo needs to be added + minor code changes

*Code Change in E4H*:

```
 <img className="bannerLogo" src={"https://selco-assets.s3.ap-south-1.amazonaws.com/TwoClr_horizontal_4X.png"} alt="Selco Foundation" style={{
  height: '40px',
  width: '100px',
  textAlign: 'center',
  marginRight: '70px',
  marginLeft: '70px',
  marginTop: '-30px',
  marginBottom: '-30px'
}} />
```

Removed line 188 `{isEmployee ? renderSearch() : null}`

Replaced with `<div style={{marginTop:"10px"}}>`. The div tag is closed after `menuItems.map`

