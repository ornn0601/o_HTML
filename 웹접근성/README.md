# 웹접근성  


## 원칙 1	인식의 용이성 (Perceivable) : 모든 콘텐츠는 사용자가 인식할 수 있어야 한다.  
### 1.1.1	(적절한 대체 텍스트 제공) 텍스트 아닌 콘텐츠는 그 의미나 용도를 이해할 수 있도록 대체 텍스트를 제공해야 한다.  
```html
<img src="일반 이미지" alt="이미지의 용도, 제목 등 정확하게 입력한다.">
<img src="콘텐츠 이미지" alt="이미지 콘텐츠를 사용하면 내부에 포함된 텍스트를 최대한 상세히 적는다.">
<div class="background-img">이미지 콘텐츠에 사용된 주요 텍스트 내용을 적어준 후 숨김 처리한다.</div>
```  

### 1.2.1	(자막 제공) 멀티미디어 콘텐츠에는 자막, 원고 또는 수화를 제공해야 한다.  

### 1.3.1	(색에 무관한 콘텐츠 인식) 콘텐츠는 색에 관계없이 인식될 수 있어야 한다.  
  - 모양이나 텍스트 등 색 이외에 다른 방법으로도 구분되어야 한다.  

### 1.3.2	(명확한 지시사항 제공) 지시사항은 모양, 크기, 위치, 방향, 색, 소리 등에 관계없이 인식될 수 있어야 한다.  
  - 예) 회원가입할때 비밀번호 입력 사항 등  

### 1.3.3	(텍스트 콘텐츠의 명도 대비) 텍스트 콘텐츠와 배경 간의 명도 대비는 4.5대 1 이상이어야 한다.  
  - 최소한의 색 대비 구현  
  - [contrast checker 바로가기](https://webaim.org/resources/contrastchecker/){:target="_blank"}

### 1.3.4	(자동 재생 금지) 자동으로 소리가 재생되지 않아야 한다.  
  ```html
  <video src="영상주소" autoplay muted></video>
  ```

### 1.3.5	(콘텐츠 간의 구분) 이웃한 콘텐츠는 구별될 수 있어야 한다.  
  - 서체의 가독성 : 비율, 공백, 굵기, 자간    
  - 단락 : 텍스트간의 간격, 행높이 : 황금높이 (x1.618)
  - 명조와 고딕 : 명조 - 제목 및 강조 일부, 고딕 - 일반 서체  
  - 텍스트 블록 : 뷰포트 기준 60% 정도  
  - 대소문자 : 강조글 및 보조글 구분  
  
<hr>
  
## 원칙 2	운용의 용이성(Operable) : 사용자 인터페이스 구성요소는 조작 가능하고 내비게이션 할 수 있어야 한다.  
### 2.1.1	(키보드 사용 보장) 모든 기능은 키보드만으로도 사용할 수 있어야 한다. (PC웹)  
``` html
<style>
  /* 키보드 탭 포커스 변경 */
  a { outline: none }
  a:focus { background: #000; color: #fff; }
</style>
```

### 2.1.1	(누르기 동작 지원) 터치(touch) 기반 모바일 기기의 모든 컨트롤은 누르기 동작으로 제어할 수 있어야 한다. (모바일웹)  
### 2.1.2	(초점 이동) 키보드에 의한 초점은 논리적으로 이동해야 하며 시각적으로 구별할 수 있어야 한다.  
### 2.1.3	(조작 가능) 사용자 입력 및 컨트롤은 조작 가능하도록 제공되어야 한다.  
### 2.2.1	(응답시간 조절) 시간제한이 있는 콘텐츠는 응답시간을 조절할 수 있어야 한다.  
### 2.2.2	(정지 기능 제공) 자동으로 변경되는 콘텐츠는 움직임을 제어할 수 있어야 한다.  
### 2.3.1	(깜빡임과 번쩍임 사용 제한) 초당 3~50회 주기로 깜빡이거나 번쩍이는 콘텐츠를 제공하지 않아야 한다.  
### 2.4.1	(반복 영역 건너뛰기) 콘텐츠의 반복되는 영역은 건너뛸 수 있어야 한다.  
``` html
<style>
  .skip_to_content {
    position: fixed;
    left: 0;
    top: 0;
    background: #000;
    color: #fff;
    text-decoration: none;
    display: none;
    transform: translateY(-100%);
    transition: 0.3s;
  }
  .skip_to_content:focus {
    display: block;
    transform: translateY(0);
  }
</style>

<body>
  <!-- 키보드 사용자를 위한 주요 서비스 바로가기 버튼 -->
  <a hef="#main_content" class="skip_to_content">Skip to Content</a>
  <!-- 콘텐츠 -->
  <div id="min_content"></div>
</body>
```
### 2.4.2	(제목 제공) 페이지, 프레임, 콘텐츠 블록에는 적절한 제목을 제공해야 한다.  
  - 디자인에서 보이지 않는 텍스트는 보이지 않도록 처리한다.  
```html
<style>
.d_hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    border: 0;
    clip: rect(0, 0, 0, 0);
    overflow: hidden;
}
</style>
```  

### 2.4.3	(적절한 링크 텍스트) 링크 텍스트는 용도나 목적을 이해할 수 있도록 제공해야 한다.  
  - 더보기 버튼 등 명확하게 어떤 내용인지 제공해야한다.  
  ```html
  <input type="image" src="주소" alt="메뉴 더보기">
  ```
  
<hr>
  
## 원칙 3	이해의 용이성(Understandable) : 콘텐츠는 이해할 수 있어야 한다.
### 3.1.1	(기본 언어 표시) 주로 사용하는 언어를 명시해야 한다.  
```html
<p>중국어로는 "안녕하세요"라고 인사할 때 <span lang="zh">你好</span> 라고 합니다.</p>
```  

### 3.2.1	(사용자 요구에 따른 실행) 사용자가 의도하지 않은 기능 (새 창, 초점 변화 등)은 실행되지 않아야 한다.  
### 3.3.1	(콘텐츠의 선형화) 콘텐츠는 논리적인 순서로 제공해야 한다.  
  - 더보기 등 디자인 상 위에 있더라도 구조상 아래에 배치해야한다.  
  ```html
  <ul>
    <li><a href="주소">news 1</a></li>
  <ul>
  <a href="주소">더보기</a>
  ```
    
### 3.3.2	(표의 구성) 표는 이해하기 쉽게 구성해야 한다.  
  - thead, tbody, tfoot, th, td 구분한다.  
```html
<table>
  <thead>
    <tr>
      <th scope="col">번호</th>
      <th scope="col">내용</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1<th>
      <td><td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">2</th>
      <td></td>
    </tr>
  </tfoot>
</table>
```
### 3.4.1	(레이블 제공) 사용자 입력에는 대응하는 레이블을 제공해야 한다.  
  - form에서 label의 for와 input의 id를 동일한 키워드로 연결하여 준다.  
```html
<form action="">
  <label for="userName">이름</label>
  <input type="text" id="userName">
</form>
```
### 3.4.2	(오류 정정) 입력 오류를 정정할 수 있는 방법을 제공해야 한다.  
  
<hr>
  
## 원칙 4	견고성(Robust) : 웹 콘텐츠는 미래의 기술로도 접근할 수 있도록 견고하게 만들어야 한다.  
### 4.1.1	(마크업 오류 방지) 마크업 언어의 요소는 열고 닫음, 중첩 관계 및 속성 선언에 오류가 없어야 한다.  
  - [WAVE 웹 접근성 평가 도구 바로가기](https://wave.webaim.org/){:target="_blank"}  
  
### 4.2.1	(웹 애플리케이션 접근성 준수) 콘텐츠에 포함된 웹 애플리케이션은 접근성이 있어야 한다.  
  
<hr>
  
## 참고  
- [웹 접근성 지침](http://www.websoul.co.kr/accessibility/WA_guide21.asp){:target="_blank"}  
- [네이버 웹 접근성](https://nuli.navercorp.com/guideline/s01/g01){:target="_blank"}  

