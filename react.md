# React

## Lifecycle Methods
### componentWillMount
- Shouldn't need this for 99% of components. 
- Exception is any setup that is only done at runtime (e.g., firebase). Use the root component to do this.
- Can call setState, but use default state instead.

### componentDidMount
- Use this for setup that couldn't be done without a DOM, like starting AJAX calls to load data.
- Can call setState.

### componentWillReceiveProps
- In this moment, you have access to the current props (this.props) and the next props (nextProps).
- Check which props will change.
- If the change is significant, act on it.
- Can call setState.

### shouldComponentUpdate
- Always returns a boolean - default is true.
- Use this to control when component re-renders.
- Can't call setState.

### componentWillUpdate
- Basically same as componentWillReceiveProps.
- Used on a component that also has shouldComponentUpdate (but no access to previous props).
- Can't call setState.

### componentDidUpdate
- Use to update DOM in response to prop or state changes.
- Can call setState.

### componentWillUnmount
- Clean up leftovers from component - cancel network requests, remove event listeners.
- Can't call setState.

#### Reference
[React lifecycle methods and when to use them](https://engineering.musefind.com/react-lifecycle-methods-how-and-when-to-use-them-2111a1b692b1)
