# thumbnail
- 영상을 캡쳐해서 썸네일로 사용.

```
await ffmpeg.run(
  "-i",
  "recording.webm",
  "-ss",
  "00:00:01",
  "-frames:v",
  "1",
  "thumbnail.jpg"
);

const thumbFile = ffmpeg.FS("readFile", "thumbnail.jpg");
const thumbBlob = new Blob([thumbFile.buffer], { type: "image/jpg" });
const thumbUrl = URL.createObjectURL(thumbBlob);

// thumbnail 출력
const thumbA = document.createElement("a");
thumbA.href = thumbUrl;
thumbA.download = "My_Thumbnail.jpg";
document.body.appendChild(thumbA);
thumbA.click();
```

## 불필요한 url제거 -> 속도 향상

```
//메모리에서 삭제
ffmpeg.FS("unlink", "recording.webm");
ffmpeg.FS("unlink", "output.mp4");
ffmpeg.FS("unlink", "thumbnail.jpg");

URL.revokeObjectURL(mp4Url);
URL.revokeObjectURL(thumbUrl);
URL.revokeObjectURL(videoFile);
```
