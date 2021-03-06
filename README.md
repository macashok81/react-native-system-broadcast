# react-native-system-broadcast
Send/Listen broadcast from native with emiter.
NOTICE:
- for React Native > 0.21 use
- for React Native < 0.21 do NOT use

## Setup

Fast and easy:
```bash
npm install react-native-system-broadcast --save
react-native link react-native-system-broadcast
```

Or manual: add the latest version as dependeny to your package.json.

```javascript
{
  "name": "YourProject",
  ...
  },
  "dependencies": {
    ...
    "react-native-system-broadcast": "^0.1.20",
    ...
  }
```

#### iOS
NOT support
#### Android
* In the settings.gradle
  ```
    include ':react-native-system-broadcast', ':app'
    project(':react-native-system-broadcast').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-system-broadcast/android')
  ```
* In the build.gradle
  ```
    compile project(':react-native-system-broadcast')
  ```
* In MainApplication.java
  ```
    import top.litop.RroadCast;
    ...
    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
        ...
        new RroadCastReactPackage(),
        ...
      );
    }
    ...
  ```
## Usage

```javascript
import RroadCast from 'react-native-system-broadcast';
...
RroadCast.sync();//You can reveice all native system broadcast in react event system
RroadCast.unSnyc();//Place use it on APP has stopped
RroadCast.sendBroadCast(action,json);//json need to like this.eg. {key:value,nokey:novalue}
RroadCast.on(action);//Connect action from native to react event system
RroadCast.remove(action);//Disconnect action from native to react event system
RroadCast.removeAll();//Place use it on APP has stopped
...
DeviceEventEmiter.addEventListener(action,(dataFromExtras)=>{
    //do something
})
...
```
## Warning

This plugin NOT safe for something like broadcast with permission.

## Versioning

This project uses semantic versioning: MAJOR.MINOR.PATCH.
This means that releases within the same MAJOR version are always backwards compatible. For more info see [semver.org](http://semver.org/).
