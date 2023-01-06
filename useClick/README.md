```javascript
* usage
const useClick = onClick => {
  const element = useRef();
  useEffect(() => {
    if (element.current) {
      element.current.addEventListener("click", onClick); // element.current에 args 함수 실행하는 이벤트 지정
    }
  });
  return element;
};

const App = () => {
  const sayHello = () => console.log("sayHello");
  const h1Element = useClick(sayHello);
  return (
    <div className="App">
      <h1 ref={h1Element}>Hi</h1>
    </div>
  );
};
```

