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

## multer
### .fields(fields)
- 필드로 지정된 혼합 파일을 허용.
- 파일 배열이 있는 객체는 req.files에 저장됨.
- 필드는 이름과 선택적으로 maxCount가 있는 객체의 배열이어야 함.
- `.post(videoUpload.fields([{ name: "video" }, { name: "thumb" }]), postUpload);`

## 썸네일 출력 안될 때
`fileUrl: video[0].path, thumbUrl: thumb[0].path,`
- 보통 위처럼 적는 경우가 많은데 저렇게 하면, 경로 문제가 남.
- `/`가 아니라 `\`로 되기 때문임... 원인은 자세히 모르겠지만 암튼 경로 문제가 많음.

### 해결

#### mongoose schema 추가
```
videoSchema.static("changePathFormula", (urlPath) => {
  return urlPath.replace(/\\/g, "/");
});
```

#### video controller에 schema 추가
```
fileUrl: Video.changePathFormula(video[0].path),
thumbUrl: Video.changePathFormula(thumb[0].path),
```

#### pug파일에 url추가
`background-image:url(${"/" + video.thumbUrl})`

