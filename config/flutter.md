# Flutter
## Initialize
```ps
flutter create --platforms=android,windows --org az21 appname
```

> [!WARNING]
> Don't use uppercase char in organization name or app name.

### App Name
```ps
./android/app/src/main/AndroidManifest.xml
```
```r
android:label="appname"
```

## App Signature

### Key
```ps
./android/app/key.jks
```

### Key Properties
```ps
./android/key.properties
```
```r
keyAlias=key
storeFile=key.jks
keyPassword=hunter2
storePassword=hunter2
```

### Gradle Config
```ps
./android/app/build.gradle
```
```groovy
android{
  signingConfigs {
    release {
      keyAlias keystoreProperties['keyAlias']
      keyPassword keystoreProperties['keyPassword']
      storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
      storePassword keystoreProperties['storePassword']
    }
  }
  buildTypes {
    release {
      signingConfig signingConfigs.release
    }
  }
}
```
