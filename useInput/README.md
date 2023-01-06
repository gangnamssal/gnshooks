```javascript
* usage
const useInput = (initialValue, validator) => { // validator 추가
  const [value, setValue] = useState(initialValue);
  const onChange = event => {
    const {
      target: { value }
    } = event;
    let willUpdate = true;
    if (typeof validator === "function") {
      willUpdate = validator(value); // validator 실행
    }
    if (willUpdate) {
      setValue(value);
    }
  };

  return { value, onChange };
};

const App = () => {
  const maxLen = value => value.length < 10; // maxLen 함수 선언
  const name = useInput("hj", maxLen); // maxLen을 args로 전달
  return (
    <div className="App">
      <h1>Hello</h1>
      <input placeholder="name" {...name} />
    </div>
  );
};
```

