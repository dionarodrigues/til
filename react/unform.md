# ReactJS & React Native forms with unform dependency

__[Unform](https://unform.dev/) is a performance focused library that helps you creating beautiful forms in React with the power of uncontrolled components performance and React Hooks.__

I'm doing some testing with this awesome library in [this project](https://github.com/diogorodrigues/appointment-scheduling-app) and it's super easy to handle forms with it.

It's possible to see this unform working at [ReactJS playground](https://codesandbox.io/embed/agitated-tdd-uf177?autoresize=1&expanddevtools=1&fontsize=14&hidenavigation=1&theme=dark) and [React Native playground](https://snack.expo.io/@diego3g/1e9fb3).

## Why Unform

- Performance - preventing inputs to rerender unnecessarily.
- Hooks - We can use useField hook exposed by unform to create our own form inputs
- ReactJS and React Native using the same API and structure

## How does it work?

Basicly there are thre packges in this dependency we can use:

- `@unform/core`: Core functionalities, needed in web and mobile;
- `@unform/web`: Web integration, used in ReactJS;
- `@unform/mobile`: Mobile integration, used in React Native;

Use the platform (web/mobile) package to import Form component, all the other functionalities can be imported directly from `@unform/core`.

More about how to use it with examples [here](https://unform.dev/guides/basic-form).