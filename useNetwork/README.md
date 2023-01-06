```javascript
* usage
const useNetwork = onChange => {
  const [status, setStatus] = useState(navigator.onLine); // true 또는 false 값
  const handleChange = () => {
    if (typeof onChange === "function") {
      onChange(navigator.onLine);
    }
    setStatus(navigator.onLine);
  };
  useEffect(() => {
    window.addEventListener("online", handleChange);
    window.addEventListener("offline", handleChange);
    () => { //componentWillUnMount 일 때 remove 실행
      window.removeEventListener("online", handleChange);
      window.removeEventListener("offline", handleChange);
    };
  }, []);
  return status;
};

const App = () => {
  const hanldeNetworkChange = online => { // 실행하는 change 함수
    console.log(online ? "It's Online state" : "It's Offline state");
  };
  const online = useNetwork(hanldeNetworkChange);
  return (
    <div className="App">
      <h1>{online ? "Online" : "Offline"} </h1>
      <p>Welcome</p>
    </div>
  );
};
```

