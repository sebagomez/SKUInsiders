This is the simplest .NET Framework 4.7.1 console app to help Microsoft reproduce a bug deployed to #WindowsInsiders in build 17754 (and still happening at build 17758).

Clone this repo, build the project and run the app... do you see the "Hello World!" message? Congrats, you don't have the bug.

Do you see message dialog? bad news 😞

![](res/error.png?raw=true)

To work around this issue, remove the sku attribute of the supportedRuntime in the App.exe.config file.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7.1" />
    </startup>
</configuration>
```