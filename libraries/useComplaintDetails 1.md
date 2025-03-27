*Path*: <b><ins>libraries/src/hooks/pgr/useComplaintDetails.js</b></ins>

*Change*: Code changed at multiple places

*Code changed in E4H*:

```
CS_ADDCOMPLAINT_HEALTH_CARE_CENTRE: `TENANT_TENANTS_PG_${incident?.phcType.replace(/\s+/g,'').toUpperCase()}`,
```

Replaced with 

```
CS_ADDCOMPLAINT_HEALTH_CARE_CENTRE: `${incident?.phcType}`,
```
