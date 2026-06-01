# BIPA 규정집 — BookStack 설치 가이드

## 실행 방법

### 1. APP_KEY 생성
```bash
openssl rand -base64 32
```
생성된 값을 `docker-compose.yml`의 `APP_KEY=` 에 붙여넣기

### 2. 비밀번호 변경 (권장)
`docker-compose.yml`에서 아래 항목을 변경:
- `DB_PASS` / `MYSQL_PASSWORD` — DB 비밀번호
- `MYSQL_ROOT_PASSWORD` — DB 루트 비밀번호

### 3. APP_URL 설정
실제 접속할 URL(도메인 또는 IP)로 `APP_URL` 변경

### 4. 실행
```bash
docker compose up -d
```

### 5. 초기 로그인
- URL: http://localhost:6875
- 이메일: `admin@admin.com`
- 비밀번호: `password`
- **로그인 후 즉시 비밀번호 변경 필요**

## 마크다운 콘텐츠 업로드
BookStack은 페이지 편집기에서 마크다운 모드를 지원합니다.
마크다운 파일은 BookStack 페이지 편집 화면 우측 상단의 **"Markdown"** 버튼으로 전환 후 붙여넣기 하거나,
API를 통해 자동 업로드할 수 있습니다.

## Cloudflare Tunnel 연동 (권장)
외부 접속을 위해 Cloudflare Tunnel 설정 후 `APP_URL`을 터널 도메인으로 변경하고 재시작:
```bash
docker compose restart bookstack
```
