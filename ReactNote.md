
1. Alert When Close Tab
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
2. Change Title Tab
```code
document.title = "Amazing Page";
```
3. Detect Tab Active / UnActive
```code
class MyComponent extends Component {
    useEffect(() => {
        const handleVisibilityChange = () => {
            if (window.ENV.SOCKET_ENABLE) {
                if (document.visibilityState === 'hidden') {
                    // highlight-start
                    console.log(document.visibilityState);
                    // highlight-end
                } else {
                    // highlight-start
                    console.log(document.visibilityState);
                    // highlight-end
                }
            }
        };
        document.addEventListener('visibilitychange', handleVisibilityChange);

        return () => {
            document.removeEventListener('visibilitychange', handleVisibilityChange);
        };
        // eslint-disable-next-line react-hooks/exhaustive-deps
    }, [document.visibilityState]);

    // Render method.
    render() {
        return (
            <div>My component</div>
        )
    }
}
```
