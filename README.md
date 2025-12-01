# Ai-eye
약 봉투 리더기
# 💊 약 봉투 리더기

모바일 카메라로 약 봉투 텍스트를 실시간 인식하고 음성으로 안내하는 웹앱

## 🎯 주요 기능

- **실시간 OCR**: Tesseract.js 기반 텍스트 인식
- **음성 안내**: 약 종류 자동 판별 후 TTS 출력
- **오타 보정**: 정규표현식 기반 유연한 매칭 (COLD → C0LD, CO1D 등)
- **PWA 지원**: 모바일 브라우저에서 앱처럼 사용 가능

## 🚀 빠른 시작

### 온라인 사용
[앱 실행하기](https://ljs0336-koco.github.io/Ai-eye/)

### 로컬 실행
```bash
# 파일 다운로드 후
python -m http.server 8000
# 브라우저에서 localhost:8000 접속
```

## 📱 지원 환경

- **권장**: Chrome Mobile (Android/iOS)
- **필수**: HTTPS 환경 (카메라 권한)
- **제한**: 일부 구형 브라우저 미지원

## 🔍 인식 가능한 약

| 텍스트 패턴 | 인식 결과 |
|------------|----------|
| COLD, C0LD, CO1D | 감기약 |
| ASPIRIN, ASP1RIN | 두통약 |
| TYLENOL | 진통제 |
| VITAMIN, V1TAMIN | 비타민 |

## ⚙️ 커스터마이징

### 새로운 약 추가
`smartMatch()` 함수에 정규표현식 추가:

```javascript
const newMedicineRegex = /YOUR[PATTERN]HERE/;
if (newMedicineRegex.test(text)) {
    name = "표시할 이름";
    msg = "읽을 메시지";
}
```

### 인식 정확도 조절
```javascript
// Line 133: 이미지 크기 (크게 = 정확 / 작게 = 빠름)
const scale = 800 / video.videoWidth; 

// Line 138: 대비 강도
ctx.filter = 'grayscale(100%) contrast(200%)';
```

## ⚠️ 알려진 제한사항

- **손글씨 미지원**: 인쇄된 텍스트만 인식
- **조명 민감**: 어두운 환경에서 인식률 저하
- **CDN 의존**: Tesseract CDN 장애 시 작동 불가
- **배터리 소모**: 연속 OCR 처리로 배터리 빠르게 소모

## 📄 라이선스

MIT License

---

**⚕️ 면책**: 이 앱은 보조 도구이며 의료 행위를 대체하지 않습니다.
