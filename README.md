# [뉴로클] 사전 과제 (Frontend)
### 주제 : 벡터(SVG) 기반의 드로잉 툴 구현
<br />

#### 프로젝트 기간
- 2024.12.19(목) 15:30 ~ 2024.12.22(일) 24:00 (총 4일)
<br />

#### 과제 진행 node 버전
- Node.js v20.13.1
- Npm 10.5.2
<br />

#### 실행 방법
``` jsx
$ cd neurocle-frontend-drawing-tool
$ npm run dev
```
<br />

#### 배포 링크
🌐 [드로잉 툴 바로가기](https://neurocle-frontend-drawing-tool.vercel.app/)

<br />

#### 과제 세부 내용
- React, typescript와 드로잉 라이브러리 Konva(https://konvajs.org/)를 사용해 프로젝트를 구현해주세요.
- 드로잉 라이브러리는 Konva가 아닌 본인이 더 편한 라이브러리를 사용해도 감점요인은 아닙니다.
- 참고로 윈도우 그림판은 비트맵 방식의 툴입니다. 이와 다르게 벡터 방식으로 동작하는 드로잉 툴을 구현해주세요.
- 코드는 직접 작성해주세요. 타인의 코드를 그대로 복사-붙여넣기 하는 경우 배점이 없습니다.
- 아래 필수 사항/선택 사항을 구현 가능한 수준에서 사용자의 입장을 고려하여 자유롭게 구현해주세요.

<br />
<br />

  
## 1. 기술 스택, 기술 선정 이유
#### 1-1 Typescript
- 타입 안정성을 높여 타입 관련 오류를 사전에 방지하고, 유지 보수를 용이하게 하기 위해 타입스크립트를 사용하였습니다.
#### 1-2 tailwindCSS
- 미리 정의된 유틸리티 클래스를 사용하여 CSS를 작성하지 않아도 다양한 스타일을 적용할 수 있습니다.
- 빠르고 효율적인 코드 수정 및 스타일 변경이 가능하여 해당 기술을 사용하였습니다.


<br />
<br />


## 2. 컴포넌트 설계
- UI
   1. Button (공용 버튼 컴포넌트)
   2. Header (헤더)
   3. DrawingCanvas (캔버스)
   4. DrawingToolBar (드로잉 툴 바)
   5. Dropdown (드로잉 선 굵기 선택 드롭다운)

   
<br />
<br />


## 3. 프로젝트 화면
|기본 화면|자유 그리기|
|:--:|:--:|
|![기본화면](https://github.com/user-attachments/assets/4428ff12-2cac-4a9d-a51e-ab86a20649b1)|![자유그리기](https://github.com/user-attachments/assets/3f1581f4-130d-4b41-a72f-79a1666d5337)|


|직선 그리기| 타원 그리기 |
|:--:|:--:|
|![직선 그리기](https://github.com/user-attachments/assets/0ce4d594-dabe-4b70-abfe-06822bc07f32)|![타원그리기](https://github.com/user-attachments/assets/a4fa2ac0-e97b-4a88-b352-0be05bd36e63)|


|직사각형 그리기|다각형 그리기 |
|:--:|:--:|
|![페이지네이션2](https://github.com/user-attachments/assets/e38d934b-971e-4eef-b2e0-77a417cdb17a)|![image](https://github.com/user-attachments/assets/01d4f00b-5d40-4a44-8642-9896da53a8a8)|

|Undo(실행 취소)| Redo(되돌리기)|
|:--:|:--:|
|![image](https://github.com/user-attachments/assets/7beacdb0-9f70-40d6-98ee-8d56f6fd373e)|![image](https://github.com/user-attachments/assets/a8415205-4013-470d-ae06-0d8e498eafff)|

|선 굵기 선택 | 색상 선택 | 
|:--:|:--:|
|![image](https://github.com/user-attachments/assets/9e66e966-086a-41a1-8afe-f4c35b410f3e)|![image](https://github.com/user-attachments/assets/52104bd3-a355-43d1-950a-6cb16ae1f520)|

<br />
<br />

## 4. 프로젝트 화면 및 기능 설명
### 4.1 드로잉 타입 선택 : 자유그리기, 직선, 타원, 직사각형, 다각형
![드로잉_새로고침까지포함](https://github.com/user-attachments/assets/1be02d81-a1fa-48b2-808d-b7a37d48833f)


#### 요구사항 확인
1. 드로잉 타입 선택: 자유 그리기, 직선, 타원, 직사각형, 다각형(유첨 ‘polygon’ 파일 참고)
   - 1회성 드로잉이 아닌, 그려진 도형들이 한 화면에서 나타날 수 있어야 합니다. ✅
   - 가장 최근에 그린 도형이 맨 위에 표시되도록 해야 합니다. ✅
   - 새로 고침 이후에도 캔버스 내용이 유지되어야 합니다. ✅
     
- 관련 Git Issues
   - [#2드로잉 기능 구현 및 스타일링](https://github.com/OH-Neuri/neurocle-frontend-drawing-tool/issues/2)
 
      
          
<br />
<br />
  

### 4.2 선 두께 선택
![선둒](https://github.com/user-attachments/assets/a09adf30-c56a-4e5a-b1c2-9d7ea4c3c8ce)

#### 요구사항 확인
2. 선 두께 선택
   - 두께 값의 최소/최대 제한이 필요합니다. (최소 5px, 최대 50px) ✅
- 관련 Git Issues
   - [#2드로잉 기능 구현 및 스타일링](https://github.com/OH-Neuri/neurocle-frontend-drawing-tool/issues/2)
 

<br />
<br/ >


### 4.3 컬러 선택
![선색상변경](https://github.com/user-attachments/assets/a95691a4-02b5-4fa5-a5c6-e03ad131a149)


#### 요구사항 확인
3. 컬러 선택
   - 현재 선택된 컬러를 사용자가 인지할 수 있어야 합니다. ✅
- 관련 Git Issues
   - [#2드로잉 기능 구현 및 스타일링](https://github.com/OH-Neuri/neurocle-frontend-drawing-tool/issues/2)


<br />
<br/ >


### 4.4 Undo, Redo (선택사항)
![리두언두](https://github.com/user-attachments/assets/4209938a-6b15-45a1-a631-1fcf5491e876)

#### 요구사항 확인
4. Undo, Redo
  - 지난 작업으로 돌아갈 수 있어야 하고 마지막으로 작업한 시점으로 돌아올 수도 있어야 합니다. ✅
  - 최근 40개의 작업 기록만 저장되도록 해주세요. ✅
- 🔅 추가 구현
  - Redo, Undo 상황에 따라 각 버튼 활성화/비활성화 기능 추가 ✅
  - 로컬스토리지에서 데이터를 가져올 때 데이터가 손상된 경우를 처리할 수 있도록 에러 핸들링 코드를 추가 ✅
  - Ctrl + z, Ctrl +y 키보드 이벤트 적용 ✅
- 관련 Git Issues
  - [#2드로잉 기능 구현 및 스타일링](https://github.com/OH-Neuri/neurocle-frontend-drawing-tool/issues/2)

<br />
<br/ >

### 4.5 전체 지우기 (추가구현)
![전체지우기](https://github.com/user-attachments/assets/94e277a9-77f5-4d47-ba95-69377146ddaa)


#### 구현 사항
- 휴지통 아이콘 클릭 시 현재 캔버스에 그려진 도형 전체 지우기 기능 추가
- 새로고침 시 이전에 그려진 도형들로 초기화되지 않도록 로컬스토리지에 저장된 데이터 제거
- 드로잉 모드, 선 굵기, 색상 상태 값 유지 

<br />
<br/ >

## 5. 프로젝트 폴더 구조
``` jsx
📦public
 ┣ 📜neurocle-favicon.png
 ┗ 📜vite.svg
📦src
 ┣ 📂assets
 ┃ ┣ 📂css
 ┃ ┃ ┣ 📜index.css
 ┃ ┃ ┗ 📜tailwind.css
 ┃ ┣ 📂font
 ┃ ┃ ┗ 📜PretendardVariable.woff2
 ┃ ┗ 📂images
 ┃ ┃ ┣ 📂drawing
 ┃ ┃ ┃ ┣ 📜line-width.png
 ┃ ┃ ┃ ┣ 📜oval.svg
 ┃ ┃ ┃ ┣ 📜pencil.svg
 ┃ ┃ ┃ ┣ 📜polygon.svg
 ┃ ┃ ┃ ┣ 📜rectangle.svg
 ┃ ┃ ┃ ┣ 📜redo.svg
 ┃ ┃ ┃ ┣ 📜slash.svg
 ┃ ┃ ┃ ┣ 📜trash.svg
 ┃ ┃ ┃ ┗ 📜undo.svg
 ┃ ┃ ┗ 📂neurocle
 ┃ ┃ ┃ ┗ 📜neurocle-logo.png
 ┣ 📂components
 ┃ ┣ 📂common
 ┃ ┃ ┗ 📜Button.tsx
 ┃ ┣ 📜DrawingCanvas.tsx
 ┃ ┣ 📜DrawingToolBar.tsx
 ┃ ┣ 📜Dropdown.tsx
 ┃ ┗ 📜Header.tsx
 ┣ 📜App.tsx
 ┣ 📜index.css
 ┣ 📜main.tsx
 ┗ 📜vite-env.d.ts
```
