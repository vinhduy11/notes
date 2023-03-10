```React Note
`1. Alert When Close Tab
```code
class MyComponent extends Component {
    // Things to do before unloading/closing the tab
    doSomethingBeforeUnload = () => {
        // Do something
    }

    // Setup the `beforeunload` event listener
    setupBeforeUnloadListener = () => {
        window.addEventListener("beforeunload", (ev) => {
            ev.preventDefault();
            return this.doSomethingBeforeUnload();
        });
    };

    componentDidMount() {
        // Activate the event listener
        this.setupBeforeUnloadListener();
    }

    // Render method.
    render() {
        return (
            <div>My component</div>
        )
    }
}
```