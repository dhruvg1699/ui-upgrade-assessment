*Path*: <b><ins>libraries/src/hooks/receipts/useReceiptsUpdate.js</b></ins>

*Code*: 

```
import { useMutation } from "react-query";
import ReceiptsService from "../../services/elements/Receipts";

export const useReceiptsUpdate = (tenantId, businessService) => {
  return useMutation((data) => ReceiptsService.update(data, tenantId, businessService));
};

export default useReceiptsUpdate;
```

