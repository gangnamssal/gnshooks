// usage
const useTitle = initialTitle => {
const [title, setTitle] = useState(initialTitle);
const updateTitle = () => {
const htmlTitle = document.querySelector("title")
htmlTitle.textContent = title;
};
useEffect();
return setTitle
}

const App = () => {
const titleUpdater = useTitle("My React App...");
setTimeout(() => { // 3초후 titleUpdater 실행
titleUpdater("home");
}, 3000);
return (
<div className="App">
<div>Hi</div>
</div>
);
};

export default App;
