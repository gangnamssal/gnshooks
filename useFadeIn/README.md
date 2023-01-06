```javascript
* usage
const usefadeIn = () => {
  const element = useRef();
  useEffect(() => {
    // element 안으로 들어가기 위해서 useEffect 사용
    if (element.current) {
      const { current } = element;
      current.style.transition = `opacity 1s`;
      current.style.opacity = 1;
    }
  }, []);
  return { ref: element, style: { opacity: 0 } }; 
};

const App = () => {
  const fadeInH1 = usefadeIn();
  return (
    <div className="App">
      <h1 {...fadeInH1}> Hello </h1>
    </div>
  );
};
```

