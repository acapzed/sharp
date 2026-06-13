# sharp

팀이 프로젝트 아이디어를 정리하고, 개발 전에 무엇을 만들지 맞추는 도구입니다.

아이디어를 입력하면 AI가 질문을 던집니다. 팀은 선택지로 답하고, 답변이 쌓이면 마인드맵과 리포트가 만들어집니다.

## 기능

- 아이디어 확인 질문 생성
- 답변 기록을 바탕으로 다음 질문 생성
- 선택지 기반 Q&A
- 실시간 마인드맵
- 프로젝트 종합 리포트
- 특정 항목에 대한 추가 질문
- Mermaid 코드 내보내기

## 실행

### 필요 항목

- Docker Desktop
- Groq API 키

### 시작하기

```bash
git clone https://github.com/acapzed/sharp.git
cd sharp

cp .env.example .env
# .env에 GROQ_API_KEY를 넣습니다.

docker compose up --build
```

브라우저에서 엽니다.

```text
http://localhost:5173
```

## 사용 흐름

```text
아이디어 입력
-> 아이디어 확인 질문
-> 프로젝트 Q&A
-> 마인드맵 업데이트
-> 종합 리포트 생성
```

## 기술 스택

| 구분 | 기술 |
|---|---|
| 프론트엔드 | React, Vite, Zustand, Tailwind CSS |
| 마인드맵 | @xyflow/react, dagre |
| 백엔드 | Node.js, Express |
| AI | Groq API |
| 실행 환경 | Docker Compose |

AI API 호출은 백엔드에서만 합니다.

## 환경변수

```env
GROQ_API_KEY=your_api_key
```

`docker-compose.yml`에서 AI 설정을 바꿀 수 있습니다.

```yaml
AI_BASE_URL=https://api.groq.com/openai/v1
AI_MODEL=llama-3.1-8b-instant
```

## API

```text
POST /api/sessions
POST /api/sessions/:id/confirm
POST /api/sessions/:id/confirm/done
POST /api/sessions/:id/questions
POST /api/sessions/:id/answers
POST /api/sessions/:id/mindmap/enrich
POST /api/sessions/:id/explore
GET  /api/sessions/:id
```

## 앞으로 할 일

- 팀원이 같은 세션에 참여하기
- PDF 또는 이미지 내보내기
- MVP 문서 생성
- 시간과 예산 기준으로 기능 범위 확인하기
