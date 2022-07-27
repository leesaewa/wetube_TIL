# recorder


## <a href="https://www.npmjs.com/package/regenerator-runtime">regeneratorRuntime</a>
- 프론트엔드에서 `async/await`를 쓰려면 설치해야 함.

## HTMLMediaElement.srcObject
- html의 `src`와 다름.
- HTMLMediaElement 인터페이스의 srcObject 속성은 HTMLMediaElement와 연결된 미디어의 소스 역할을 하는 객체를 설정하거나 반환.
- 그 객체는 `MediaStream` `MediaSource` `Blob` `File`일 수 있음.
```
const stream = await navigator.mediaDevices.getUserMedia({
  audio: true,
  video: true,
});

video.srcObject = stream;
video.play();
```

## <a href="https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder">MediaRecorder</a>
- 비디오, 오디오 등 녹화하고 싶은 걸 녹화할 수 있음.
- `"video/webm"` or `"video/mp4"`)포맷으로 저장할 수도 있음.
- `MediaRecorder()` 생성자를 사용하여 생성
  - 기록할 MediaStream이 지정된 새 MediaRecorder 개체를 만듦.

### Events
#### MediaRecorder.start()
- 미디어 녹화를 시작함. 이 메서드는 선택적으로 밀리초 단위의 값을 가진 타임슬라이스 인수를 전달할 수 있음.

#### MediaRecorder.stop()
- 저장된 데이터의 최종 Blob을 포함하는 dataavailable 이벤트가 발생하는 시점에서 기록을 중지함.

#### <a href="https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder/dataavailable_event">dataavailable</a>
- `MediaRecorder.stop()`이 실행될 때 발생하는 이벤트


## URL.createObjectURL()
- 정적 메서드는 주어진 객체를 가리키는 URL을 DOMString으로 반환함.
- 해당 URL은 자신을 생성한 창의 document가 사라지면 함께 무효화됨.

<img src="https://user-images.githubusercontent.com/97646713/181209501-e9e0001d-05ea-46c4-b68e-24bcc9ae190a.png" width="80%">
- 브라우저에 만들어진 url, 오직 브라우저 상에서만 존재하며, 브라우저로 하여금 파일에 접근할 수 있게 함.


------

# 녹화한 영상 다운로드
```
const handleDownload = () => {
  const a = document.createElement("a");  //a태그 생성
  a.href = videoFile;  //'URL.createObjectURL(event.data);'로 생성된 링크를 a태그로 보냄
  a.download = "My_Recording.webm";  //a태그의 다운로드 속성
  document.body.appendChild(a);  //생성한 a태그를 body 안에 넣음
  a.click();  // 유저가 클릭할 수 있게 함.
};
```

# 다운로드 비디오 포맷 변환

## 변한하기 위한 프로그램

### FFmpeg
1. 비디오에 관한 것을 핸들링(비디오 압축, 포맷 변환, 오디오 제거 및 추출, 형식 변환, 비디오 스크린샷, 자막 추가 등등)할 수 있는 소프트웨어로, 컴퓨터에 설치할 수 있음.
2. FF를 실행하려면 백엔드에서 실행해야만 한다. 그래서 서버 비용이 발생하게 됨.

### WebAssembly
- 개방형 표준.
- WebAssembly(Wasm)는 스택 기반 가상 머신을 위한 이진 명령 형식
- 프로그래밍 언어를 위한 이식 가능한 컴파일 대상으로 설계되어 클라이언트 및 서버 응용 프로그램을 위해 웹에 배포할 수 있음.
- 빠른 코딩이 가능함.

### FFmpeg WebAssembly
- WebAssembly에서 제공하는 브라우저 및 노드용 FFmpeg
- ffmpeg.wasm은 FFmpeg의 순수한 Webassembly/Javascript 포트.
- 그것은 비디오 및 오디오 녹음, 변환, 스트리밍 등을 브라우저 내부에서 할 수 있도록 함.
- FFmpeg WebAssembly를 사용하는 이유는 FFmpeg를 사용해서 브라우저로 하여금 비디오 파일을 변환하기 위함.
- `npm install @ffmpeg/ffmpeg @ffmpeg/core`
https://github.com/ffmpegwasm/ffmpeg.wasm
https://www.npmjs.com/package/@ffmpeg/ffmpeg




