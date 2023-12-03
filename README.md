Reproduce bug https://github.com/JetBrains/compose-multiplatform/issues/3840

To reproduce run script:
```bash
cd iosApp
pod install
open iosApp.xcodeproj
```
 - Product -> Archive
 - (Not use Xcode Cloud)
 - Product -> Archive again
 - Verification


Possible solution is to use `isStatic = false` in [build.gradle.kts](shared%2Fbuild.gradle.kts), or remove `pod 'FirebaseDatabase'` in [Podfile](iosApp%2FPodfile) 
