# Using jsconfig.json to improve VS Code IntelliSense

__This is really useful when working on a React.js project and, generally, on a webpack project, because it provides us with a way to work with absolute paths instead of relative paths.__

`import MyComponent from '~/components/MyComponent.js'`

instead of

`import MyComponent from '../../../components/MyComponent.js'`

These relative imports are not recommended because they are difficult to maintain in case of refactoring. 

![Using jsconfig.json to improve VS Code IntelliSense](https://user-images.githubusercontent.com/2319449/70345363-a72aef00-183a-11ea-83d5-24bcbb09bbfd.gif)

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

One more example with multiple paths from root directory:

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

[More information about jsconfig.json](http://https://code.visualstudio.com/docs/languages/jsconfig "adding a jsconfig.json").
