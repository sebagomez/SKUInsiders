This is the simplest .NET Framework 4.7.1 console app to help Microsoft reproduce a bug deployed to #WindowsInsiders in build 17754 (and still happening at build 17758).

Clone this repo, build the project and run the app... do you see the "Hello World!" message? Congrats, you don't have the bug.

Do you see message dialog? bad news 😞

![](res/error.png?raw=true)

To work around this issue, remove the `sku` attribute of the `supportedRuntime` in the App.exe.config file.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.1" />
    </startup>
</configuration>
```

**Update 9/11/2018**: From the [Microsoft Developer](https://twitter.com/msdev) twitter handle, they said the bug was [fixed in 17759](https://twitter.com/msdev/status/1039654320034258947).

![](res/msdevtwit.png?raw=true)

**Update 9/12/2018**: This issue was finally added as a know issue in the realese notes for builds [17754](https://blogs.windows.com/windowsexperience/2018/09/05/announcing-windows-10-insider-preview-build-17754/), [17755](https://blogs.windows.com/windowsexperience/2018/09/07/announcing-windows-10-insider-preview-build-17755/) and [17758](https://blogs.windows.com/windowsexperience/2018/09/11/announcing-windows-10-insider-preview-build-17758/).