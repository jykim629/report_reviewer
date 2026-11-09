# R 과제 채점 리뷰어

r-fd 스킬이 생성한 엑셀과 피드백 zip 파일을 업로드하여 성적을 검토·수정하고 최종 파일을 다운로드하는 웹 애플리케이션입니다.

## 프로젝트 구조

```
reviewer/
├── index.html          # 메인 HTML 구조
├── css/
│   └── style.css       # 모든 스타일 정의
├── js/
│   └── app.js          # 애플리케이션 로직
└── README.md           # 이 파일
```

## 기능

### 📥 파일 업로드
- **점수.xlsx** - 학생 이름, 번호, 점수, 채점 항목(O/X)이 포함된 엑셀 파일
- **피드백.zip** - 학생별 피드백 텍스트와 R 코드 파일이 담긴 압축 파일

### 🔍 검토 각색 체계
- **왼쪽 위**: 원본 R 코드 표시
- **왼쪽 아래**: 피드백 직접 편집 (실시간 저장)
- **오른쪽 위**: 채점 항목 O/X 토글
- **오른쪽 아래**: 점수 내역 및 수정

### 📊 주요 기능
- 각 학생별 독립적 검토
- 채점 항목 클릭으로 O/X 토글 (자동 점수 재계산)
- 점수 수정
- 종합 의견 요약 편집
- 이름으로 학생 검색
- **자동 저장** (localStorage) - 새로고침 후에도 작업 유지
- 최종 파일 다운로드 (xlsx, zip)

## 사용 방법

### 1. 브라우저에서 열기
```bash
# 간단하게 index.html을 브라우저에서 열면 됩니다
```

### 2. 파일 업로드
- 업로드 카드에 파일을 끌어다 놓거나 클릭하여 선택
- 두 파일 모두 업로드되면 **리뷰 시작** 버튼 활성화

### 3. 학생별 검토
- 왼쪽 목록에서 학생 선택
- 각 패널에서 내용 확인 및 수정
- 채점 항목 클릭하여 O/X 변경
- 점수 입력 후 **적용** 버튼 클릭

### 4. 최종 파일 생성
- 하단 **최종 파일 생성** 버튼 클릭
- 수정된 xlsx, zip 파일이 순차 다운로드됨

## 주요 기술

- **XLSX.js** - 엑셀 파일 읽기/쓰기
- **JSZip** - ZIP 파일 압축/해제
- **LocalStorage** - 자동 저장 (브라우저 저장소)
- **Vanilla JavaScript** - 외부 프레임워크 미사용

## 브라우저 호환성

- Chrome/Edge 최신 버전
- Firefox 최신 버전
- Safari (최신)

※ 한글 인코딩(EUC-KR, CP949) 자동 감지 지원

## 자동 저장

작업 내용은 LocalStorage에 자동 저장됩니다:
- 1.5초 동안 입력이 없으면 자동 저장
- 브라우저 새로고침해도 이전 작업이 유지됨
- 확인 메시지를 통해 복구 여부 선택 가능

## 파일 구조

### `index.html`
- 순수 HTML 마크업만 포함
- CSS와 JS는 외부 파일에서 로드

### `css/style.css`
- CSS 변수(Custom Properties)로 테마 관리
- 반응형 레이아웃
- 다크/라이트 색상 체계

### `js/app.js`
- 모든 애플리케이션 로직
- 파일 파싱 및 데이터 관리
- UI 렌더링 및 이벤트 핸들러
- LocalStorage 자동 저장

## 외부 라이브러리

CDN에서 로드:
```html
<!-- XLSX - 엑셀 처리 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>

<!-- JSZip - ZIP 처리 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Nanum+Gothic+Coding:wght@400;700&family=Pretendard:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

## 확장 가능성

이 프로젝트는 다음과 같이 확장할 수 있습니다:

- **Backend 추가** - Express/Node.js와 연결하여 서버 저장 기능
- **데이터베이스** - MongoDB/PostgreSQL로 영구 저장
- **권한 관리** - 사용자 인증 및 역할 기반 접근 제어
- **통계시스템** - 점수 분포, 평균, 통계 분석
- **버전 관리** - 수정 이력 추적
- **Bulk 작업** - 여러 학생 일괄 수정

## 라이선스

MIT License
