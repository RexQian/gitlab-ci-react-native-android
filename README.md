# gitlab-ci-react-native-android
## Android 27.0.2 and Fastlane 2.91.0
This Docker image contains react-native and the Android SDK and most common packages necessary for building Android apps in a CI tool like GitLab CI. 

A `.gitlab-ci.yml` with caching of your project's dependencies would look like this:

```
image: InteractiveObject/gitlab-ci-react-native-android

stages:
- build

cache:
  key: ${CI_PROJECT_ID}
  paths:
  - android/.gradle/

build:
  stage: build
  script:
  - yarn
  - cd android && ./gradlew assembleDebug
  artifacts:
    paths:
    - android/app/build/outputs/apk/
```


## Detached testing
Build locally
```
docker build -t InteractiveObject/gitlab-ci-react-native-android:android-27.0.2 .
```
or run from remote
```
	docker run -it -d InteractiveObject/gitlab-ci-react-native-android /bin/bash
	docker attach HASH
	docker stop 3c854ac65f64d424c097e639c002b50431454e839b5c551ec2a929dcbecb7176
	
````
