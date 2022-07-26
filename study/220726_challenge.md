# Fullscreenchange 이벤트
- `fullscreenchange` 이벤트 는 브라우저가 전체 화면 모드로 전환되거나 전환된 직후에 시작됩니다.
- 이벤트는 전체 화면 모드로 전환되거나 전환되는 `Element Document` 까지 버블링됩니다.
- `Element` 가 전체 화면 모드로 들어가거나 종료 하는지 알아보려면 `Document.fullscreenElement` 값을 확인하십시오.
- 이 값이 `null` 이면 요소는 전체 화면 모드를 종료하고, 그렇지 않으면 전체 화면 모드로 전환합니다.
- 이 이벤트는 취소할 수 없습니다.

## Syntax
- `addEventListener()` 와 같은 메서드에서 이벤트 이름을 사용 하거나 이벤트 핸들러 속성을 설정합니다.

```
addEventListener('fullscreenchange', event => { });

onfullscreenchange = event => { };
```

## Examples
- 이 예제에서는 `fullscreenchange` 이벤트에 대한 핸들러 가 `Document` 에 추가됩니다.
- 사용자가 "전체 화면 모드 전환" 버튼을 클릭하면 `click` 핸들러가 `div` 에 대한 전체 화면 모드를 전환합니다.
- `document.fullscreenElement` 에 값이 있으면 전체 화면 모드를 종료합니다. 그렇지 않은 경우 div는 전체 화면 모드로 전환됩니다.
- `fullscreenchange` 이벤트가 처리 될 즈음에는 요소의 상태가 이미 변경되었음을 기억하십시오.
- 따라서 변경 사항이 전체 화면 모드인 경우 `document.fullscreenElement` 는 현재 전체 화면 모드에 있는 요소를 가리킵니다.
- 반면 `document.fullscreenElement` 가 null이면 전체 화면 모드가 취소됩니다.
- 예제 코드에서 이것이 의미하는 바는 요소가 현재 전체 화면 모드인 경우 `fullscreenchange` 핸들러가 전체 화면 요소의 id 를 콘솔에 기록한다는 것입니다.
- `document.fullscreenElement` 가 null인 경우 코드는 변경 사항이 전체 화면 모드를 종료한다는 메시지를 기록합니다.

### HTML
```
<h1>fullscreenchange event example</h1>
 <div id="fullscreen-div">
   <button id="toggle-fullscreen">Toggle Fullscreen Mode</button>
 </div>
```

### JavaScript
```
function fullscreenchanged = (event) => {
  // document.fullscreenElement는
  //있는 경우 전체 화면 모드입니다. 하나가 없으면
  // 속성 값이 null입니다.
  if (document.fullscreenElement) {
    console.log(`Element: ${document.fullscreenElement.id} entered fullscreen mode.`);
  } else {
    console.log('Leaving fullscreen mode.');
  }
}

document.addEventListener('fullscreenchange', fullscreenchanged);
// or
document.onfullscreenchange = fullscreenchanged;

// 토글 버튼 클릭 시 전체화면 진입/종료
document.getElementById('toggle-fullscreen').addEventListener('click', (event) => {
  if (document.fullscreenElement) {
    // exitFullscreen은 Document 객체에서만 사용할 수 있습니다.
    document.exitFullscreen();
  } else {
    el.requestFullscreen();
  }
});
```

-------

# <a href="https://runebook.dev/ko/docs/dom/htmlmediaelement/readystate">readyState</a>
