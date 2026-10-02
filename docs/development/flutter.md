---
icon: lucide/smartphone
---

# Flutter

## Initialize

```sh
flutter create --platforms=android,windows --org az21 appname
```

!!! warning

    Don't use uppercase char in organization name or app name.

### App Name

```sh
./android/app/src/main/AndroidManifest.xml
```

```r
android:label="appname"
```

## App Signature

### Key

```sh
./android/app/upload-key.jks
```

### Key Properties

```sh
./android/key.properties
```

```r
keyAlias=upload
storeFile=upload-key.jks
keyPassword=hunter2
storePassword=hunter2
```

### Gradle Config

```sh
./android/app/build.gradle
```

```groovy
def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties')
if (keystorePropertiesFile.exists()) {
   keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}

android{
  // ...
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
  // ...
}
```
