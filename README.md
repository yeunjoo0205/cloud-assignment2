GitHub: https://github.com/사용자명/ledger-api · Render: https://<서비스>.onrender.com/docs

# 가계부 API (FastAPI + Supabase PostgreSQL)

클라우드컴퓨팅실습 4주차 과제 — FastAPI 앱을 Render에 배포하고, 환경변수 `DATABASE_URL`로 Supabase(PostgreSQL, Session pooler)에 연결했다.

## 엔드포인트

| 메서드 | 경로 | 설명 |
|---|---|---|
| POST | `/accounts` | 계좌 생성 |
| GET | `/accounts` | 계좌 목록 |
| GET | `/accounts/{account_id}` | 계좌 단건 조회 |
| POST | `/transactions` | 거래 생성 (계좌 외래키) |
| GET | `/accounts/{account_id}/detail` | 계좌 + 거래 목록 중첩 응답 |
| GET | `/stats/by-category` | 카테고리별 지출 합계 (GROUP BY) |

## 파일 구성

- `database.py` — Engine · Session · Base · `get_db`
- `models.py` — 테이블 구조 (accounts · categories · transactions)
- `schemas.py` — API 입출력 형식 (Pydantic)
- `main.py` — 앱 생성 + 테이블 생성 + 경로
- `requirements.txt` — 배포 시 설치할 패키지
- `.env` — DB 연결 문자열 (Git 제외, Render에서는 환경변수로 설정)

## 실습 기록

### ① 결과 확인

<!-- Supabase Table Editor 캡처, Render /docs 의 GET /accounts 캡처를 붙인다 -->

### ② 핵심 개념 되새김

- 계좌·거래를 두 테이블로 나눈 이유(1:N 관계):
- SQLAlchemy 모델 클래스와 실제 테이블의 대응:
- 접속 문자열을 `.env`로 분리하는 이유:

### ③ 자유 로그

<!-- 오늘 배운 것 · 막힌 곳과 푼 과정 · 아직 안 풀린 것 -->
<!-- AI에게 무엇을 시켰고 결과를 어떻게 검증했는지 한 줄 -->
