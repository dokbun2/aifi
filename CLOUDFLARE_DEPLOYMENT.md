# Cloudflare Pages 배포 가이드

## 📋 배포 준비 완료
✅ GitHub 리포지토리: https://github.com/dokbun2/aifi.git
✅ 브랜치: main
✅ 모든 파일이 GitHub에 푸시됨

## 🚀 Cloudflare Pages 배포 단계

### 1단계: Cloudflare Pages 접속
1. https://dash.cloudflare.com 로그인
2. 좌측 메뉴에서 "Workers & Pages" 선택
3. "Create application" 버튼 클릭
4. "Pages" 탭 선택
5. "Connect to Git" 클릭

### 2단계: GitHub 연결
1. "Connect GitHub account" 클릭
2. GitHub 로그인 및 권한 승인
3. 리포지토리 목록에서 "dokbun2/aifi" 선택
4. "Begin setup" 클릭

### 3단계: 빌드 설정
**프로젝트 이름**: aifi (또는 원하는 이름)

**Production branch**: main

**Build settings**:
- Framework preset: None (정적 사이트)
- Build command: (비워두기 - 빌드 명령 불필요)
- Build output directory: / (루트 디렉토리)

**Root directory**: / (비워두기)

**Environment variables**: 설정 불필요

### 4단계: 배포
1. "Save and Deploy" 클릭
2. 첫 배포는 몇 분 소요됨
3. 배포 완료 후 제공되는 URL 확인:
   - 기본 도메인: `[프로젝트명].pages.dev`
   - 예: `aifi.pages.dev`

### 5단계: 커스텀 도메인 설정 (선택사항)
1. 프로젝트 설정 → "Custom domains" 탭
2. "Add custom domain" 클릭
3. 도메인 입력 (예: aifi.example.com)
4. DNS 설정 안내 따라하기:
   - CNAME 레코드 추가
   - SSL 자동 적용됨

## 🔄 자동 배포 설정
- main 브랜치에 푸시할 때마다 자동 배포
- Pull Request 시 프리뷰 URL 자동 생성
- 빌드 로그 실시간 확인 가능

## ⚙️ 추가 설정 옵션

### Redirects 설정
프로젝트에 이미 `_redirects` 파일 포함됨
```
# SPA 라우팅 지원
/*    /index.html   200
```

### Headers 설정 (필요시)
`_headers` 파일 생성:
```
/*
  Cache-Control: max-age=3600
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
```

### 환경 변수 (필요시)
프로젝트 설정 → Environment variables에서 추가

## 📊 모니터링
- Analytics: 방문자 통계 확인
- Web Analytics: 상세 분석 (Pro 플랜)
- Build logs: 배포 로그 확인

## 🆘 문제 해결

### 404 에러
- Build output directory 확인
- index.html 파일 존재 확인

### 빌드 실패
- Build command 비워두기 확인
- 파일 경로 대소문자 확인

### 배포 후 업데이트 안됨
- 캐시 퍼지: Caching → Purge Cache
- 브라우저 캐시 삭제

## 📝 배포 정보
- **GitHub Repository**: https://github.com/dokbun2/aifi
- **Branch**: main
- **Framework**: None (Vanilla JS)
- **Build Required**: No
- **Static Files**: Yes

## 🎉 배포 완료 후
1. 제공된 URL로 사이트 접속 테스트
2. 모든 페이지 정상 작동 확인
3. 콘솔 에러 확인
4. 필요시 커스텀 도메인 설정

---

배포 관련 문의사항이 있으시면 언제든지 물어보세요!