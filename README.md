
<p align="center">
  <a href="https://ifcjs.github.io/info/">ifc.js</a>
  |
  <a href="https://ifcjs.github.io/info/docs/Guide/web-ifc/Introduction">문서</a>
  |
  <a href="https://ifcjs.github.io/web-ifc/examples/viewer/index.html">데모</a>
  |
  <a href="https://discord.gg/FXfyR4XrKT">디스코드</a>
  |
  <a href="https://github.com/ifcjs/web-ifc/tree/main/examples/usage/src">사용법 예제</a>
  |
  <a href="https://www.npmjs.com/package/web-ifc">npm 패키지</a>
  |
  <a href="https://github.com/ifcjs/web-ifc/blob/main/contributing.md">기여(공헌)하기</a>
</p>

<img src="banner.png">
<h1>web-ifc <img src="https://ifcjs.github.io/info/img/logo.svg" width="32"></h1>

[![Build](https://github.com/tomvandig/web-ifc/actions/workflows/build.yml/badge.svg)](https://github.com/tomvandig/web-ifc/actions/workflows/build.yml)
![npm](https://img.shields.io/npm/dw/web-ifc)
![opencollective](https://opencollective.com/ifcjs/tiers/badge.svg)

**web-ifc**는 네이티브 속도로 ifc 파일을 읽고 쓰기 위한 JavaScript 라이브러리입니다. **web-ifc**는 [ifc.js](https://ifcjs.github.io/info/) 프로젝트의 일부로서 개방형 BIM 응용을 개발하기 위한 임계치를 낮추는 것을 목표로 합니다.

## 상태

web-ifc가 이미 상당히 안정적이고 빠르다 할지라도 충분한 ifc 지원까지는 **pre-alpha 상태**입니다. 현재 지원되는 ifc 요소 리스트나 서로 다른 ifc 타입들에 대한 지원 수준은 진행 중이며 문서화되지 않은 작업입니다.

당신의 모델에 따라 web-ifc는 빠르고 정확할 수도 있고 느리고 고장날 수도 있습니다. 문제가 있는 모델은 제가 볼 수 있도록 공유 부탁 드립니다 :)

## 설치

`npm install web-ifc`

## 빠른 설정

```JavaScript
const WebIFC = require("web-ifc/web-ifc-api.js");

// API 초기화
const ifcApi = new WebIFC.IfcAPI();

// 라이브러리 초기화
await ifcApi.Init();

// 데이터로부터 모델 열기
let modelID = ifcApi.OpenModel(/* string 또는 UInt8Array 형태의 IFC 데이터 */, /* 선택적인 설정 오브젝트 */, );

// 이제 모델이 로드되었습니다! 지오메트리 또는 프로퍼티를 가져오기 위해 modelID를 사용하십시오.
// IFC를 읽고 쓰는 방법을 더 자세히 알기 위해서는 예제/사용법을 확인하십시오.

// 모델을 닫습니다. 모든 메모리가 해제됩니다.
ifcApi.CloseModel(modelID);

```

web-ifc를 사용하는 방법을 더 자세히 알려면 [예제](https://github.com/tomvandig/web-ifc/tree/main/examples/usage/src)를 보십시오.

## WASM 모듈 빌드하기

### emscripten 설정하기

WASM 라이브러리는 emscripten을 통해 빌드됩니다. emscripten 설정에 대한 정보는 [emscripten 설치 가이드](https://emscripten.org/docs/getting_started/downloads.html)를 보십시오. 그 후에는 당신의 경로 안에 `emsdk_env`가 있어야합니다.

### WASM 라이브러리

모든 디펜던시(dependencies)를 설치하려면 `npm install`을 실행하십시오.

새로운 터미널을 열 때마다 `npm run setup-env`를 실행하십시오. 이렇게 하면 코드를 컴파일하기 위한 필수 emscripten 환경 변수들을 설정하게 됩니다.

wasm 바이너리와 web-ifc API의 릴리즈 버전을 빌드하기 위해 `npm run build-release-all`을 실행하십시오. 결과물은 `./dist`에 배치될 것입니다.

만약 WASM을 디버깅 활성화 상태로 빌드하고 싶으면 `npm run build-debug`를 실행하면 됩니다. 이렇게 하면 web-ifc를 실행할 때 디버깅 정보를 더 잘 검사할 수 있게 됩니다.

기본 ifc 파일 뷰어와 함께 개발 서버를 실행하려면 `npm run dev`를 실행하십시오.

## 독립형 C++

이 라이브러리는 기본적으로 browser/nodejs에서 WebAssembly를 통해 사용되기는 하지만, 이 프로젝트는 C++ 라이브러리 또는 실행파일로서 독립적으로 사용할 수도 있습니다. 시작하기 위한 간단한 엔트리 포인트에 대해서는 [여기](https://github.com/tomvandig/web-ifc/blob/main/src/wasm/web-ifc-test.cpp)를 보십시오.

## 기여(공헌)하기

도와주고 싶습니까? 훌륭해요!

[저희의 기여 의견](https://github.com/tomvandig/web-ifc/blob/main/contributing.md)을 확인해 주십시오.
