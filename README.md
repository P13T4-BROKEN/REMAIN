# Snippet Studio

HTML/CSS 코드를 입력하면 실시간으로 미리보기를 보여주고, 완성된 결과를 하나의 HTML 파일로 다운로드할 수 있는 도구입니다. 순수 HTML/CSS/JS로만 만들어져서 별도 빌드 과정 없이 바로 배포할 수 있어요.

## GitHub Pages로 배포하는 방법

1. **GitHub에 새 저장소(repository) 만들기**
   - github.com 접속 → 우측 상단 `+` → `New repository`
   - 이름은 원하는 대로 (예: `snippet-studio`)
   - Public으로 설정 (GitHub Pages 무료 사용을 위해 필요)

2. **이 폴더의 파일 올리기**
   - `index.html` 파일을 방금 만든 저장소에 업로드
   - 저장소 페이지에서 `Add file` → `Upload files` 로 드래그해서 올려도 되고,
   - 터미널을 쓴다면:
     ```bash
     git init
     git add index.html
     git commit -m "Add Snippet Studio"
     git branch -M main
     git remote add origin https://github.com/사용자명/저장소명.git
     git push -u origin main
     ```

3. **GitHub Pages 켜기**
   - 저장소의 `Settings` 탭 → 왼쪽 메뉴 `Pages`
   - `Source`를 `Deploy from a branch`로 선택
   - Branch는 `main`, 폴더는 `/ (root)` 선택 후 `Save`

4. **1~2분 기다리기**
   - 같은 `Pages` 설정 화면 상단에 `https://사용자명.github.io/저장소명/` 형태의 주소가 뜹니다.
   - 그 주소로 접속하면 바로 사용할 수 있어요.

## 파일 구성

- `index.html` — 페이지 전체 (HTML + CSS + JS가 한 파일에 들어있어요, 배포가 더 간단하도록)

## 기능 요약

- 왼쪽: HTML 입력창 / 가운데: CSS 입력창 / 오른쪽: 실시간 미리보기
- 입력하는 즉시 미리보기에 자동 반영 (약 0.2초 디바운스)
- 상단 파일명 입력 후 `다운로드` 버튼을 누르면 완성된 HTML 파일 하나로 저장
- `예제 불러오기`로 샘플 코드 확인 가능
- 화면이 좁아지면(모바일) 상단 탭으로 HTML/CSS/미리보기를 전환

## React가 필요할까요?

아니요. 이 도구가 하는 일 — 텍스트 입력받기, `<iframe>`에 실시간으로 렌더링하기, 파일로 다운로드하기 — 는 모두 순수 JavaScript(`textarea`, `iframe.srcdoc`, `Blob` + `URL.createObjectURL`)만으로 충분합니다. 나중에 사용자 계정, 저장된 스니펫 목록 같은 기능을 추가하면서 화면 상태가 복잡해지면 그때 React 같은 프레임워크를 고려해도 늦지 않아요.
