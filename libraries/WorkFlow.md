*Path*: <b><ins>libraries/src/services/elements/WorkFlow.js</b></ins>

*Change*: Code changed 

*Code changed in E4H*:

Code replaced from `Lines 7-18`

```
  const res = await Digit.UploadServices.Filefetch(ids, tenantId);

  if (res.data.fileStoreIds && res.data.fileStoreIds.length !== 0) {
    // Create a Map to store file URLs by fileStoreId
    const urlMap = new Map(res.data.fileStoreIds.map((file) => [file.id, file.url]));

    // Separate images and videos based on documentType (matching by fileStoreId)
    const images = [];
    const videos = new Map();

    documents.forEach((doc) => {
      const fileUrl = urlMap.get(doc.fileStoreId);
      if (fileUrl) {
        if (doc.documentType === "HLS" || doc.documentType.toLowerCase().startsWith("video")) {
          const videoKey = doc.documentUid;

          if (!videos.has(videoKey)) {
            videos.set(videoKey, { master: null, original: null, fileStoreId: null });
          }

          if (doc.documentType === "HLS") {
            videos.get(videoKey).master = Digit.Utils.getFileUrl(fileUrl);
          } else {
            videos.get(videoKey).fileStoreId = doc.fileStoreId;
            videos.get(videoKey).original = Digit.Utils.getFileUrl(fileUrl);
          }
        } else {
          images.push(Digit.Utils.getFileUrl(fileUrl));
        }
      }
    });

    return {
      thumbs: Array.from(urlMap.values()).map((url) => url.split(",")[3] || url.split(",")[0]),
      images,
      videos: Array.from(videos.values()),
    };
  } else {
    return null;
  }
};
```

`params` in `WorkflowService` updated:

in `init`: `{ tenantId: Digit.SessionStorage.get("Employee.tenantId"), businessServices },`

in `getByBusinessId`:  `{ tenantId: stateCode, isStateLevelCall: window.location.href.includes("complaint/details")?false :Digit.SessionStorage.get("Employee.tenantId") == "pg"?true :false,businessIds: businessIds, ...params, history },`

`getDetailsByIdV2` arguments changed to `{ tenantIdNew, idNew, moduleCode }`

`getDetailsById` arguments changed to `{ tenantIdNew, idNew, moduleCode, role, getTripData }`

Code added after `line 212`

```
let tenantId = window.location.href.split("/")[9]
let id = window.location.href.split("/")[8]
```

Code changed on `line 273`

```
thumbnailsToShow: { thumbs: instance?.thumbnailsToShow?.thumbs, fullImage: instance?.thumbnailsToShow?.images, videos: instance?.thumbnailsToShow?.videos },
```

