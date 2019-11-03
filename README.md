# plop-react-ts
A [plop](https://plopjs.com/) generator for creating React components with specific structure.
It allows to create 2 kind of React components:
* React Component: Simple component with the following folder structure:
    * `<Component name>.{jsx|tsx}`
    * `<Component name>.{scss|css}`
    * `<Component name>.test.{jsx|tsx}`
    * `index.{jsx|tsx}`
* React Container (or View): Component with the boilerplate for mapping application state to component's props by using [Redux](https://redux.js.org/) (`mapStateToProps &  mapDispatchToProps`).
    * `<Component name>.container.{jsx|tsx}`
    * `<Component name>.{jsx|tsx}`
    * `<Component name>.test.{jsx|tsx}`
    * `index.{jsx|tsx}`

For each one of these 2 kind of component, you can choose:
* which React component to use: `PureComponent Class`, `Component Class` and `Stateless Function`
* to use [ReactI18n](https://react.i18next.com/) or not (multilingualism)
* to use [Typescript](https://www.typescriptlang.org/) or not (Type checker)
* to use [Storybook](https://storybook.js.org/) or not (Component Explorer)

See [Examples](./examples)

# Get Started

## Installation

1. Add Plop to your project

```
$ npm install --save-dev plop
```

2. Add Plop-react to your project

```
$ npm install --save-dev @sgfastit/plop-react
```

3. Create a plopfile.js at the root of your project
``` javascript
module.exports = function (plop) {
	// Load plop react here
  plop.load('plop-react');

  // You can load other plop module or define your own plop generators or helpers, here
};
```

4. Add script inside your `package.json`, for running `plop` generator
```
"plops":"plop --plopfile plopfile.js"
```

5. Now you can use it, by running

```
yarn plops
```

![yarn plop-react](./doc/plop-react.png)

## Configuration

### Default confguration

By default, Plop-react has default configurations:

``` javascript
{
  componentsPath: './source/components',    		// default location for components
  containersPath: './source/containers',    		// default location for containers
  defaultComponentName: 'Button',           		// default name for component
  defaultContainerName: 'Icon',             		// default name for containers
  defaultComponentType: 'PureComponent Class',  	// use PureComponent Class by default
  useReactI18nByDefault: true,              		// use ReactI18n by default
  useTypescriptByDefault: true,                   	// use Typescript by default
  useRedux: false,					// use Redux files by default  
  useScss: true,					// use SCSS files by default
};

```

### How to overwrite default configuration

You can overwrite the whole default configuration (or only some properties) by yours when you load `plop-react` inside your `plop-file.js`.

``` javascript
module.exports = function(plop) {
  // Load plop react here and overwrite default configuration
  plop.load('plop-react', {
    componentsPath: './src/components',
    containersPath: './src/views',
    defaultComponentName: 'Component',
    defaultComponentType: 'PureComponent Class',
    useTypescriptByDefault: false,
  });
};
```
