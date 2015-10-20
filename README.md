# react-whitebox

This component will render errors in your app in a white box.

This is a fork of [redbox-react](https://github.com/KeywordBrain/redbox-react). All credit goes to David Pfahler for implementing the component. I just couldn't take the red flash anymore and therefore changed some styles of the component.

<img src="http://i.imgur.com/9Jhlibk.png" alt="example" width="700" />

## Usage
Catch an error and give it to `react-whitebox`. Works with
* [react-transform-catch-errors](https://github.com/gaearon/react-transform-catch-errors) ([see example](https://github.com/amannn/react-whitebox/tree/master/examples/react-transform-catch-errors) or [react-transform-boilderplate](https://github.com/gaearon/react-transform-boilerplate/))
* [babel-plugin-react-hot](https://github.com/loggur/babel-plugin-react-hot) & [babel-plugin-react-error-catcher](https://github.com/loggur/babel-plugin-react-error-catcher) (see [example](https://github.com/amannn/react-whitebox/tree/master/examples/babel-plugin-react-hot))
* [react-hot-loader](https://github.com/gaearon/react-hot-loader) (deprecated! see [example](https://github.com/amannn/react-whitebox/tree/master/examples/react-hot-loader-example), relies on changes in unmerged [pull request](https://github.com/gaearon/react-hot-loader/pull/167) and will not be merged!)

or manually:

```javascript
const WhiteBox = require('react-whitebox')
const e = new Error('boom')
const box = <Whitebox error={e} />
```

Here is a more useful, full-fleged example:

```javascript
/* global __DEV__ */
import React from 'react'
import App from './components/App'

const root = document.getElementById('root')

if (__DEV__) {
  const Whitebox = require('react-whitebox')
  try {
    React.render(<App />, root)
  } catch (e) {
    React.render(<Whitebox error={e} />, root)
  }
} else {
  React.render(<App />, root)
}
```

## What is this good for?
An error that's only in the console is only half the fun. Now you can use all the wasted space where your app would be if it didn’t crash to display the error that made it crash. You should use this in development only.

## Will this catch errors for me?
No. As you can see above, this is only a UI component for rendering errors and their stack traces. It's works great with other solutions, that automate the error catching for you, see the [examples](https://github.com/amannn/react-whitebox/tree/master/examples).
