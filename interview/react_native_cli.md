# React Native 개발 환경 설정

## [개요]

React Native 실행 방법입니다 쉽게 따라할 수 있도록 내용을 공유합니다.

React Native는 아래와 같이 2가지 개발 방법이 있습니다.

1. Expo CLI
2. React Native CLI

## [설정 방법]

### Expo CLI \*\*\*\*

Expo를 개발하기 위해서는 Node.js가 설치가 되어있어야 합니다 [Node](https://nodejs.org/en/download/) 사이트 들어가서 Windows Installer 클릭 후 다운로드 받아서 인스톨 해주면 됩니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/775bf439-56c7-4946-9819-633e57038c19/1..png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/775bf439-56c7-4946-9819-633e57038c19/1..png)

그 다음 명령 프롬프트(cmd)에 들어가서 `node -v` 명령어를 입력하고 아래와 같이 뜬다면 설치가 잘 된 겁니다.이제 `npm install -g expo-cil`명령어를 입력 후 Expo-Cli를 설치합니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c9621a2e-ed66-4074-96a0-338f2a3e2c9f/2.node-v.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c9621a2e-ed66-4074-96a0-338f2a3e2c9f/2.node-v.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ba6a1649-83cb-428c-a708-e3927d46c5a3/3.expo-cli.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ba6a1649-83cb-428c-a708-e3927d46c5a3/3.expo-cli.png)

그 다음 React Native CLI명령어를 통해 프로젝트를 생성합니다

새 프로젝트가 완성이 되었으면 `cd MyProject`라는 명령어를 통해 해당 프로젝트 파일로 이동 후,

`npm start`라는 명령어를 입력하면 Expo가 시작이 됩니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80c21d95-1a25-4763-8908-ec0fe3ebf99e/5.expo-initcdstart.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80c21d95-1a25-4763-8908-ec0fe3ebf99e/5.expo-initcdstart.jpg)

5. 모든 준비가 끝났습니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dceeaa51-b344-4dcd-9862-ffa2e90a3416/expo-start.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dceeaa51-b344-4dcd-9862-ffa2e90a3416/expo-start.png)

### React Native CLI

React Native앱을 개발하기 위해서는 Node.js, JDK, Android Studio를 설치해야 합니다.

윈도우에서 필요한 패키지를 설치하고 관리하는 [Chocolatey](https://docs.chocolatey.org/en-us/choco/setup#more-install-options)를 통해서 Node.js, JDK를 설치하겠습니다.

명령 프롬프트(cmd)를 통해서 Chocolatey를 설치하겠습니다 설치하려면 관리자 권한으로 실행하고 아래의 명령어를 실행합니다.

```jsx
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

명령 프롬프트(cmd) 재실행 하여서 `choco -version` 명령어를 입력하고 아래와 같이 뜬다면 설치가 잘 된 겁니다.

```jsx
choco - version;
// Chocolatey v0.10.15
```

명령 프롬프트(cmd) 관리자권한으로 Node.js, JDK를 설치하겠습니다. (Node.js가 이미 설치되어 있다면`node -v` 명령어를 통해 버전이 12이상인지 확인해주세요.)
`choco`명령어를 통해서 Node.js, JDK를 설치하겠습니다.

```jsx
choco install -y nodejs.install openjdk8
```

**Android Studio 설치**

안드로이드 스튜디오를 설치하겠습니다. 아래에 링크로 이동 하고 설치를 진행하겠습니다.

안드로이드 스튜디오: [https://developer.android.com/studio/index.html](https://developer.android.com/studio/index.html)

다운로드가 완료되었으면 설치 파일을 실행하여서 설치를 진행 합니다.

설치가 완료되면 안드로이드 스튜디오가 실행되는 것을 확인 할 수 있습니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9a76a03b-b64b-419b-8ba1-84bd5c4d0d2d/.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9a76a03b-b64b-419b-8ba1-84bd5c4d0d2d/.png)

밑에 Configure를 선택한 후 SDK Manager로 들어갑니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76e8cd46-d6c6-4aba-a181-8879d41c5624/Group_8.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76e8cd46-d6c6-4aba-a181-8879d41c5624/Group_8.png)

Android10.0(Q)가 설치되었는지 확인 후, 오른쪽 하단에 Show Packages Details 선택하면 아래와 같이 상세하게 나옵니다 다음 항목이 선택되어 있는지 확인해주세요.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8b5a960-40cb-4236-a4de-758ea8f1b727/Group_11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8b5a960-40cb-4236-a4de-758ea8f1b727/Group_11.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd27f91a-8e9a-4412-8e87-6b322cee853d/Group_15.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fd27f91a-8e9a-4412-8e87-6b322cee853d/Group_15.png)

확인 후 SDK Tools탭을 선택 후, 오른쪽 하단에 Show Packages Details를 선택하면 아래와 같이 상세하게 나옵니다 29.0.2가 선택되었는지 확인해주세요 선택이 되었다면 OK버튼을 눌러주세요.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/117eaa58-fb05-4cd4-a38f-0b12d9887ab8/Group_16.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/117eaa58-fb05-4cd4-a38f-0b12d9887ab8/Group_16.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fc988e7-19c0-40a1-8cfe-7f4f5b618080/Group_18.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fc988e7-19c0-40a1-8cfe-7f4f5b618080/Group_18.png)

다음으로 안드로이드 스튜디오 환경 변수 설정을 하겠습니다**(**React native앱으로 빌드하려면 일부 환경 변수를 설정해야 합니다.**)**

- 내 PC를 우클릭 하고 속성 메뉴를 선택합니다
- 정보 탭을 선택하고 고급 시스템 설정을 선택합니다.
- 고급 탭을 선택하고 고급탭 하단에 있는 환경 변수를 선택합니다.

사용자 변수 항목에서 새로 만들기 버튼을 선택하고 변수 이름은 ANDROID_HOME으로 입력하고,
변수 값에는 자신의 안드로이드 스튜디오의 SDK 위치를 입력합니다. 확인 버튼을 선택 합니다 ANDROID_HOME이 사용자 변수에 등록이 되었습니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5404c272-91b2-4f6d-89b8-74e75ce01dc9/Group_20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5404c272-91b2-4f6d-89b8-74e75ce01dc9/Group_20.png)

(자신의 안드로이드 SDK 위치가 어디에 있는지 모르는 경우, 안드로이드 스튜디오 SDK Manager 설정 화면으로 이동합니다. 위에 상단에 보시면 Android SDK Location 항목에서 자신의 안드로이드 SDK 위치를 확인 할 수 있습니다.)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/af32f17d-a412-4014-9bf6-40f9ec29ebe5/Group_21.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/af32f17d-a412-4014-9bf6-40f9ec29ebe5/Group_21.png)

사용자 변수 항목에서 JAVA_HOME 설정 부분을 확인해줍니다. JAVA_HOME 있으면 이 단계는 넘어가도 됩니다.

없다면 변수 이름에 JAVA_HOME을 입력하고 변수 값에는 자신의 안드로이드 스튜디오의 JRE 위치를 입력해줍니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ba0861cb-1840-42f9-9fa3-11892e81f307/__2021-03-30_120129.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ba0861cb-1840-42f9-9fa3-11892e81f307/__2021-03-30_120129.png)

이제 안드로이드 스튜디오의 platform-tools를 설정해야 합니다.

- 사용자 변수 리스트에서 Path를 선택 합니다.
- 편집 버튼을 선택 합니다.
- 새로 만들기 버튼을 선택 하고,
- `%LOCALAPPDATA%\Android\Sdk\platform-tools` 경로를 추가합니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8070af1-0e65-42c0-824d-543d09a1cb16/Group_22.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8070af1-0e65-42c0-824d-543d09a1cb16/Group_22.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/828c8336-c468-4bd2-a947-0208df6ebfd3/Group_23.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/828c8336-c468-4bd2-a947-0208df6ebfd3/Group_23.png)

이제 환경 설정은 끝났습니다 새로운 프로젝트를 만들어 보겠습니다.

명령 프롬프트(cmd)에 들어가서 React Native CLI명령어를 통해 프로젝트를 생성합니다.

새 프로젝트가 완성이 되었으면 `cd 자신의 프로젝트 이름` 명령어를 통해 해당 프로젝트 파일로 이동 후, `npx react-native run-android` 명령어를 입력하면 React Native가 시작이 됩니다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd5a3f49-39ea-4d28-9418-65ecc170d875/__2021-03-30_123344.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd5a3f49-39ea-4d28-9418-65ecc170d875/__2021-03-30_123344.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e233fd73-71af-4de7-834b-6cf2e0fea153/__2021-03-30_135847.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e233fd73-71af-4de7-834b-6cf2e0fea153/__2021-03-30_135847.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfe714d3-364c-4c0a-b071-d5be992dd0ac/__2021-03-30_134233.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfe714d3-364c-4c0a-b071-d5be992dd0ac/__2021-03-30_134233.png)
