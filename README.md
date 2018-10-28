# SampleCalculator

### Introduction
This is simply four(arithmatic operations) functions based calculator for the completion of test task.

### Contains:
- Material Design Framework: `react-native-material-ui`
- JS Framework: `react and react-native`
- State Container: `redux`
- Linting: `eslint`

### Get started
_It requires [Node.js](https://nodejs.org/) `react-native-cli, yarn, node, npm, jdk, android, xcode` installed to run._

If you have not yet installed React Native, you can use [this tutorial](https://facebook.github.io/react-native/docs/getting-started.html).

1. Clone the project 
    ```sh
    $ git clone https://github.com/samwonder/SampleCalculator.git
    ```
2. Install dependencies with `yarn`
    ```sh
    $ yarn
    ```
3. Start the dev server with ```yarn start```

### Run on Android

1. You have to connect hardware device using [ADB](https://developer.android.com/studio/command-line/adb.html) or run [emulator](https://developer.android.com/studio/run/emulator-commandline.html).
2. Invoke ```react-native run-android``` command.

### Run on iOS

1. You have to get  [Xcode](https://developer.apple.com/xcode/) installed on your machine.
2. Invoke ```react-native run-ios``` command.

## Frameworks we suggest using if you need this in your app

1. Navigator: https://reactnavigation.org/

2. Strings localization: https://github.com/stefalda/ReactNativeLocalization

3. Networking: rx-fetch + rxjs

4. Maps: https://github.com/airbnb/react-native-maps

5. Permissions: https://github.com/yonahforst/react-native-permissions

6. Image picker: https://github.com/ivpusic/react-native-image-crop-picker

7. OpenGL: https://github.com/ProjectSeptemberInc/gl-react-native

8. Fabric: https://www.npmjs.com/package/react-native-fabric

9. Icons: https://oblador.github.io/react-native-vector-icons/

10. UI components: https://nativebase.io/

11. Dialogs: https://www.npmjs.com/package/react-native-popup-dialog

## Our guidelines and some recommendations

1. Architecture: Redux + saga https://github.com/redux-saga/redux-saga

2. Code style: https://github.com/airbnb/javascript

3. Versioning: packadge.json - we freeze versions of the libraries during project development,  unless we really need the feature or bugfix from newer version

4. Use formatting tabulation of 2. Needs to be changed in WebStorm settings
![](https://lh6.googleusercontent.com/05rcRv9E2RN1emBzVDOQEdrj_YSe1Jj90ILoCgOyUms73JPcO9qWcTy0CGg-d_o-AHMbYB2w_pId_9_b5E7UV3kTcuUtFMA6gHTBDRZ2_YUug26aFSVx-9nnU70-QU6XMm1TAjJN)

5. Add all component props to propTypes. It adds safety, shows you what props available, and allows IDEA/WebStorm to autocomplete them. https://facebook.github.io/react/docs/typechecking-with-proptypes.html

6. Use ```redux-immutable``` to create immutable store.
    [Redux FAQ: Immutable Data](http://redux.js.org/docs/faq/ImmutableData.html#redux-faq-immutable-data)

    ```js
    import { combineReducers } from 'redux-immutable';
    import loginReducer from "../reducers/loginReducer";
    import rootReducer from "../reducers/rootReducer";
    import listReducer from "../reducers/listReduser";

    const combinedReducers = combineReducers({
        root: rootReducer,
        login: loginReducer,
        list: listReducer,
    });
    ```
    ```redux-persist``` can't work with immutable state. So, we have to use ```redux-persist-immutable```.
    ```js
    import { autoRehydrate, persistStore } from 'redux-persist-immutable'
    import { applyMiddleware, compose, createStore } from "redux";
    const sagaMiddleware = createSagaMiddleware();
    const store = createStore(
        combinedReducers,
        initialState,
        compose(applyMiddleware(sagaMiddleware), autoRehydrate({log: true})));
    persistStore(
        store,
        {
            storage: AsyncStorage,
            blacklist: ['root'],
        }
    );
    ```
7. Antipatterns:
      - Do not use setState() in componentWillMount()
      - Do not perform any logic in render() function
      - Do not use indexes of an array as its keys
      - Do not validate forms with redux store
      - Do not perform any logic in reducers
      - Do not perform too much dispatches
      - Do not rely on JS single thread
      - Do not use x-index a lot
      - Do not use ListView, use FlatList instead
      - Remove console.log() calls
      - Do not use object literals in render()
      - Reduce render() function calls
      - Use InteractionManager.runAfterInteractions() to perform any hard stuff
      - Use requestAnimationFrame to perform animations
      - Extend React.PureComponent as much as possible
      - Use shouldRasterizeIOS
      - Use renderToHardwareTextureAndroid
      - Do not perform any logic in componentWillMount()
      - Use useNativeDriver
      - Don't use ```toJS()``` with immutable to avoid creation unnecessary object.

8. Project structure:
   - android
   - ios
   - node_modules
   - index.android.js
   - index.ios.js
   - …
   - app
    - actions
     - login-actions.js
     - sign-up-actions.js
     - …
    - components
     - Login.js
     - SignUp.js
     - …
    - reducers
     - loginReducer.js
     - signUpReducer.js
     - …
    - resources
     - strings.js
     - colors.js
     - dimens.js
     - styles.js
    - store
     - configureStore.js
    - api.js
    - app.js
    - const.js
    
    
    ## The screenshots of our project
    <p>
      <img src="https://static.collectui.com/shots/2311064/calculator-large" width="200"/>
    </p>