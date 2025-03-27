*Path*: <b><ins>libraries/src/hooks/pgr/useComplaintStatusWithCount.js</b></ins>

*Change*: Code changed at multiple places

*Code changed in E4H*:

`getCount` function deleted

Code added (before useEffect)

```
const [statusCount, setStatusCount]=useState();
   const appFilters=JSON.parse(sessionStorage.getItem("appFilters"));
   const searchParams=JSON.parse(sessionStorage.getItem("searchParams"));
   let wfFilters
     if(searchParams?.filters?.wfFilters?.assignee?.[0]?.code !=="")
     {
       wfFilters = { ...searchParams?.filters?.wfQuery,assignee:searchParams?.filters?.wfFilters?.assignee?.[0]?.code}
     }
     else {
       wfFilters = { ...searchParams?.filters?.wfQuery}
     }
     const { assignee }=wfFilters;
   const { limit, offset, incidentType, phcType, applicationStatus }=appFilters;
     const { data, isLoading, isFetching, isSuccess } = Digit.Hooks.useNewInboxGeneral({
       tenantId: Digit.ULBService.getCurrentTenantId(),
       ModuleCode: "Incident",
       filters: { ...appFilters, assignee, limit: limit, offset: offset,sortOrder: "DESC", services: ["Incident"]},
       config: {
         select: (data) => {
           return data;
         },
         enabled: Digit.Utils.pgrAccess(),
       },  
     });
         useEffect(() => { 
         if(data && data.items && data.items.length>0 && data.statusMap){
           const counts=data.statusMap.reduce((acc, item)=>{
               const status=item.statusid;
               if(status){
                 acc[status]=item.count;
               }
               return acc; 
             },{});
             setStatusCount(counts);
         }
         else{
           setStatusCount("-")
         }
       }, [data]);
```

`useEffect` function code Replaced with (`getStatusWithCount` function replaced)

```
const getStatusWithCount = async () => {
         let statusWithCount = complaintStatus.map(async (status) => {
           const count=statusCount[status.code]||0;
           return{
             ...status,
             count: count,
           }
         });
         setcomplaintStatusWithCount(await Promise.all(statusWithCount));
       }
     if(complaintStatus.length>0 && statusCount!==undefined){
       getStatusWithCount();
       }
```

`statusCount` added in `useEffect` dependencies