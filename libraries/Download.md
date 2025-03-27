*Path*: <b><ins>libraries/src/services/atoms/Download.js</b></ins>

*Change*: Code added

*Code changed in E4H*:

Code added after `Line 55`

```
const coulmncount= Object.keys(data[0]).length;
const uniformWidths={ wch: 20};
const coulmnWidths=new Array(coulmncount).fill(uniformWidths)
ws['!cols']= coulmnWidths;
const header=Object.keys(data[0]);
header.forEach((header, index)=>{
	const cellAddress=XLSX.utils.encode_cell({c: index, r: 0});
	if(!ws[cellAddress]) ws[cellAddress]={ t: 's', v:header};
	ws[cellAddress].s={
		font: { bold: true},
	}
});
```
