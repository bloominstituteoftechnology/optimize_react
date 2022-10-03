# Memoization Example in React

The purpose of this repository is to help learners understand when to use Memoization in React. Specifically how we can use the `useMemo` to optimize the performance of our components.

### How to install

1. clone and download all npm modules
2. get an [API key from emoji-api.com](https://emoji-api.com)
3. npm start

**Environment Variables**

```
REACT_APP_EMOJI_API_KEY=
```

### Steps to solving the problem

**The Problem**: The `main` branch of this repository is set up to show how it can be really easy to code yourself into a corner in React, especially when using the React Hooks pattern.

- Inside of `App.js` you'll find that there is a simple button that, when pressed, fetches emojis and displays them to the user. There is also a 'doubler' function that takes a number value from an input and doubles it output and prints it to the DOM.
- If you look at the `console` you'll see that when clicking the `Get Emojis <button>` our logs inside the 'double function' get called as well.
- `double` is an expensive algorithm (not really but it's faking it for the example) and we don't want to run it every time we call the API at the press of a button.
- This is what we aim to fix. We don't want to make any unnecessary calls to an API if we don't have to.

![bad loggin](./src/assets/bad_logs.gif)

**The Solution**

- Wrapping `double` in a `useMemo` hook and adding `number` to it's dependency array will solve our problem for us.

```js
const doubledNumber = useMemo(() => {
  return double(number);
}, [number]);
```

- Be sure to import `useMemo` from react and be sure to return the `output of double` from within your useMemo.
- Now your logs should not log a call to `double` when you're fetching the emoji data.
