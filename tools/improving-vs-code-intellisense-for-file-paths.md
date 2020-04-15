# Using jsconfig.json to improve VS Code IntelliSense

__This is really useful when working on a React.js project and, generally, on a webpack project, because it provides us with a way to work with absolute paths instead of relative paths.__

`import MyComponent from '~/components/MyComponent.js'`

instead of

`import MyComponent from '../../../components/MyComponent.js'`

These relative imports are not recommended because they are difficult to maintain in case of refactoring. 

**We can use this IntelliSense in VS Code by adding a `jsconfig.json` file to our project.**

```json
{
  "compilerOptions": {
    "baseUrl": "src",
    "paths": {
      "~/*": ["*"]
    }
  }
}
```
It should now work with absolute import support using the ~/ prefix. Eg.: `import MyComponent from '~/components/MyComponent.js'`.

![Using jsconfig.json to improve VS Code IntelliSense](https://user-images.githubusercontent.com/2319449/70345363-a72aef00-183a-11ea-83d5-24bcbb09bbfd.gif)

Another example with multiple paths from root directory:

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "~/*": ["src/*"],
	  "components/*": ["src/components/*"],
	  "configs": ["configs/"]
    }
  },
  "exclude": ["node_modules", "dist"]
}
```

The `exclude` property allows to improve the performance of IntelliSense by specifying folders which are not part of the project's source code.

[More information about jsconfig.json](https://code.visualstudio.com/docs/languages/jsconfig).


## Fixing Absolute paths in eslint

If you are using eslint in your project, it will receive many complaints about the imports with the prefix '~'.

Fortunately, there is a library that serves to let eslint knows that everything is right.

We can solve this problem adding the `eslint-import-resolver-babel-plugin-root-import` dependency.

`babylu@Project: ~$ yarn add eslint-import-resolver-babel-plugin-root-import -D`

And in the eslint configuration file include the following properties:

```json
"settings": {
    "import/resolver": {
      "babel-plugin-root-import": {}
    }
  }
```