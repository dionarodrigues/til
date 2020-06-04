# Consuming API on localhost

__Once the API is running correctly on localhost and your React Native project is already running on your device or some emulator (such as Android Virtual Device (AVD) or Genymotion Emulator, for instance), you´ll need to understand how to set the localhost url to consume the API.__

In this case I´m going to use [axios](https://github.com/axios/axios), but you can apply the same settings for others methods as well.

This is how axios looks like:

```
const api = axios.create({
  baseURL: 'http://localhost:3333/',
});
```

`` will be prepended to `url` unless `url` is absolute. It can be convenient to set `baseURL` for an instance of axios to pass relative URLs to methods of that instance. You can do the same with other approaches criating a global variable, for example.

`http://localhost:3333/` is the URL of the API, whose port is `3333`.

## Setting the correct URL depending on the device

- __iOS on emulator__: `http://localhost:3333/`
- __iOS on physical device__: [Machine IP](https://www.google.com/search?q=Get+your+LAN+IP+Address+in+Mac+OS+X&rlz=1C1CHBF_enBR843BR843&oq=Get+your+LAN+IP+Address+in+Mac+OS+X&aqs=chrome..69i57j69i60.399j0j9&sourceid=chrome&ie=UTF-8). Something like `192.168.1.102:3333`

- __Android on localhost__: you need to [execute this command](https://reactnative.dev/docs/running-on-device) `adb -s reverse tcp:3333 tcp:3333` and than continue using `http://localhost:3333/`
OR
- __Android on Android Studio__: `http://10.0.2.2:3333/`
- __Android on Genymotion Emulator__: `http://10.0.3.2:3333/`
- __Android on physical device__: [Machine IP](https://www.google.com/search?rlz=1C1CHBF_enBR843BR843&ei=PFvZXomzBYS-5OUPlOifcA&q=how+to+get+the+ipconfig+in+windows&oq=how+to+get+the+ipconfig+in+windows&gs_lcp=CgZwc3ktYWIQAzIECAAQRzIECAAQRzIECAAQRzIECAAQRzIECAAQRzIECAAQRzIECAAQRzIECAAQR1DLBFjLBGCjBmgAcAF4AIABAIgBAJIBAJgBAKABAaoBB2d3cy13aXo&sclient=psy-ab&ved=0ahUKEwiJwYbDgenpAhUEH7kGHRT0Bw4Q4dUDCAw&uact=5) Something like `192.168.1.102:3333`
