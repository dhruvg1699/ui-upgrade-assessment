*Path*: <b><ins>react-components/src/atoms/Table.js</b></ins>

*Change*: Code changes

*Code Change in E4H*:

Removed `customPageSizesArray = null` from props

Code Added after `line 135` (Initialization of toast useState)

```
const iPadMaxWidth=1024;
const iPadMinWidth=768
const tableWrapperRef = useRef(null); // Ref for the table wrapper
const paginationRef = useRef(null); // Ref for the pagination container
const [isIpadView, setIsIpadView] = React.useState(window.innerWidth <= iPadMaxWidth && window.innerWidth>=iPadMinWidth);
const onResize = () => {
	if (window.innerWidth >=iPadMinWidth && window.innerWidth <= iPadMaxWidth ) {
		if (!isIpadView) {
			setIsIpadView(true);
		}
	} else {
		if (isIpadView) {
			setIsIpadView(false);
		}
	}
};

React.useEffect(() => {
	window.addEventListener("resize", () => {
		onResize();
	});
	return () => {
		window.addEventListener("resize", () => {
			onResize();
		});
	};
});
```

Almost whole code is changed between th `<React.Fragment>` tags inside return

```
 <div style={{ marginTop: isIpadView ? "210px" : "none", marginLeft: isIpadView ? -20 : "none" }}>
      <div style={{ overflowX: "auto" }} ref={tableWrapperRef}>
        {/* Table */}
        <div style={{ display: "inline-block", minWidth: "100%" }}>
          <table
            className={className}
            {...getTableProps()}
            style={styles}
            ref={tableRef}
            {...getNoColumnBorder(noColumnBorder)}
          >
            <thead>
              {headerGroups.map((headerGroup) => (
                <tr {...headerGroup.getHeaderGroupProps()}>
                  {showAutoSerialNo && (
                    <th style={{ verticalAlign: "top" }}>
                      {showAutoSerialNo && typeof showAutoSerialNo == "string" ? t(showAutoSerialNo) : t("TB_SNO")}
                    </th>
                  )}
                  {headerGroup.headers.map((column) => (
                    <th
                      {...column.getHeaderProps(column.getSortByToggleProps())}
                      style={
                        column?.id === "selection"
                          ? { minWidth: "100px" }
                          : { verticalAlign: "top", textAlign: `${column?.headerAlign ? column?.headerAlign : "left"}` }
                      }
                    >
                      {column.render("Header")}
                      <span>{column.isSorted ? (column.isSortedDesc ? <SortDown /> : <SortUp />) : ""}</span>
                    </th>
                  ))}
                </tr>
              ))}
            </thead>
            <tbody {...getTableBodyProps()}>
              {page.map((row, i) => {
                prepareRow(row);
                return (
                  <tr {...row.getRowProps()} onClick={() => onClickRow(row)} className={rowClassName}>
                    {showAutoSerialNo && <td>{i + 1}</td>}
                    {row.cells.map((cell) => (
                      <td {...cell.getCellProps([getCellProps(cell)])}>
                        {cell.attachment_link ? (
                          <a style={{ color: "#1D70B8" }} href={cell.attachment_link}>
                            {cell.render("Cell")}
                          </a>
                        ) : (
                          <React.Fragment> {cell.render("Cell")} </React.Fragment>
                        )}
                      </td>
                    ))}
                  </tr>
                );
              })}
            </tbody>
          </table>
        </div>
      </div>
      {/* Pagination */}
      {isPaginationRequired && (
        <div
          className="pagination dss-white-pre"
          ref={paginationRef}
          style={{
            marginTop: "8px",
            overflow: "hidden",
            width:"0px !important"
          }}
        >
          {`${t("CS_COMMON_ROWS_PER_PAGE")} :`}
          <select
            className="cp"
            value={manualPagination ? pageSizeLimit : pageSize}
            style={{ marginRight: "15px" }}
            onChange={manualPagination ? onPageSizeChange : (e) => setPageSize(Number(e.target.value))}
          >
            {[10, 20, 30, 40, 50].map((pageSize) => (
              <option key={pageSize} value={pageSize}>
                {pageSize}
              </option>
            ))}
          </select>
          <span>
            <span>
              {pageIndex * pageSize + 1}
              {"-"}
              {manualPagination
                ? (currentPage + 1) * pageSizeLimit > totalRecords
                  ? totalRecords
                  : (currentPage + 1) * pageSizeLimit
                : pageIndex * pageSize + page?.length}{" "}
              {/* {(pageIndex + 1) * pageSizeLimit > rows.length ? rows.length : (pageIndex + 1) * pageSizeLimit}{" "} */}
              {totalRecords ? `of ${manualPagination ? totalRecords : rows.length}` : ""}
            </span>{" "}
          </span>
          {/* to go to first and last page we need to do a manual pagination , it can be updated later*/}
          {!manualPagination && pageIndex != 0 && <ArrowToFirst onClick={() => gotoPage(0)} className={"cp"} />}
          {canPreviousPage && manualPagination && onFirstPage && <ArrowToFirst onClick={() => manualPagination && onFirstPage()} className={"cp"} />}
          {canPreviousPage && <ArrowBack onClick={() => (manualPagination ? onPrevPage() : previousPage())} className={"cp"} />}
          {canNextPage && <ArrowForward onClick={() => (manualPagination ? onNextPage() : nextPage())} className={"cp"} />}
          {!manualPagination && pageIndex != pageCount - 1 && <ArrowToLast onClick={() => gotoPage(pageCount - 1)} className={"cp"} />}
          {rows.length == pageSizeLimit && canNextPage && manualPagination && onLastPage && (
            <ArrowToLast onClick={() => manualPagination && onLastPage()} className={"cp"} />
          )}
          {/* to go to first and last page we need to do a manual pagination , it can be updated later*/}
        </div>
      )}
  </div>
```


Only code from Line 268 onwards (`Object.keys(selectedRowIds)`) is unchanged