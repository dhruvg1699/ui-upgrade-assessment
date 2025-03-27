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

Almost whole code is changed between th `<React.Fragment>`