Reproduce bug https://github.com/JetBrains/compose-multiplatform/issues/3840

 - Set your TEAM_ID in file [Config.xcconfig](iosApp%2FConfiguration%2FConfig.xcconfig)
 - Run project in AndroidStudio and run iOS App once
 - Run script:
    ```bash
    cd iosApp
    pod install
    open iosApp.xcworkspace
    ```
 - You need to register this app in Apple Dev portal, or use bundle ID from existing once
 - Product -> Archive
 - (Not use Xcode Cloud)
 - Product -> Archive (again)
 - Validate App 
 - Use default settings for validation

![img.png](img.png)

```
The app references non-public symbols in Payload/My application.app/My application: _ubidi_close, _ubidi_getDirection, _ubidi_getLength, _ubidi_getLevelAt, _ubidi_openSized, _ubidi_reorderVisual, _ubidi_setPara, _ubrk_clone, _ubrk_current, _ubrk_first, _ubrk_getRuleStatus, _ubrk_isBoundary, _ubrk_next, _uloc_getDefault, _uloc_toLanguageTag, _uscript_getScript (ID: f1f68af3-13c8-4525-a24e-bcee2d299765)
```

Possible solution is to use `isStatic = false` in [build.gradle.kts](shared%2Fbuild.gradle.kts), or remove `pod 'FirebaseDatabase'` in [Podfile](iosApp%2FPodfile) 
