# Adding routes in React Native using React Navigation 

__React Navigation is officially promoted by both Facebook and the React Native documentation as the primary solution for routing.__

So [react-navigation/native](https://reactnavigation.org/) is the best solution for routing and navigation in a React Native app as just like [react-router-dom](https://reacttraining.com/react-router/web/guides/quick-start) is the most famous library for react web apps.

## Why React Navigation

When creating mobile apps, the first thing that pops into our minds is how we handle a user's navigation through the app, since mobile apps are made up of multiple screens.

[React Navigation](https://reactnavigation.org/) is a javaScript-based library for routing that does not directly use the native navigation APIs on iOS and Android. It means, we don't need to learn Objective-C, Swift, Java, Kotlin, etc, to create awesome navigations on mobile app because this library already provides to us all we need for that.

We can build different navigators as they said in [their documentation](https://reactnavigation.org/docs/custom-navigators/):

- `createStackNavigator` - Renders one screen at a time and provides transitions between screens. When a new screen is opened it is placed on top of the stack.
- `createDrawerNavigator` - Provides a drawer that slides in from the left of the screen by default.
- `createBottomTabNavigator` - Renders a tab bar that lets the user switch between several screens.
- `createMaterialTopTabNavigator` - Renders tab view which lets the user switch between several screens using swipe gesture or the tab bar.
- `createMaterialBottomTabNavigator` - Renders tab view which lets the user switch between several screens using swipe gesture or the tab bar.

## How to use

We can check all the necessary settings in their [complete documentation](https://reactnavigation.org/). Please note that some settings depend on OS we are using to work on (iOS or Android).

If you want to start a mobile app from scratch that already contains this navigation library and other good settings, take a look at my [starter for react native application with typescript](https://github.com/diogorodrigues/react-native-typescript-starter).






