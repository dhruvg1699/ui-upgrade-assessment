*Path*: <b><ins>libraries/src/hooks/pgr/useComplaintStatus.js</b></ins>

*Change*: Code Added
*Code added in E4H*:

```
let assignee="";
const appFilters=JSON.parse(sessionStorage.getItem("appFilters"));
const { data, isLoading, isFetching, isSuccess } = Digit.Hooks.useNewInboxGeneral({
    tenantId: Digit.ULBService.getCurrentTenantId(),
    ModuleCode: "Incident",
    filters: { limit: 10, offset: 0, services: ["Incident"] },
    config: {
	      select: (data) => {
	        return {data:data};
	    },
    enabled: Digit.Utils.pgrAccess(),
	},  
});
```

Added after line 7 (After tenantId is initialised)