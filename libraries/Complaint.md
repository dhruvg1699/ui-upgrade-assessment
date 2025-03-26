*Path*: <b><ins>libraries/src/services/elements/Complaint.js</b></ins>

*Change*: Code added at multiple places

*Code added/changed in E4H*:

```
const tenants = Digit.SessionStorage.get("Tenants").map(item => item.code).join(',');
const codes = Digit.SessionStorage.get("Tenants").filter(item => item.code !== "pg")
.map(item => item.code)
.join(',');
const sessionTenantId = Digit.SessionStorage.get("Employee.tenantId");
const isCodePresent = (array, codeToCheck) =>{
return array.some(item => item.code === codeToCheck);
}
const userRoles = Digit.SessionStorage.get("User")?.info?.roles || [];
```

```
tenantId = sessionTenantId === "pg" ? isCodePresent(userRoles, "COMPLAINT_RESOLVER") ? codes:tenants : sessionTenantId;
```

'?' added at multiple places