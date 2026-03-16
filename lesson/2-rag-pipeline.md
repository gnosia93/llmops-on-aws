## LLM 파이프라인 ##
* 1. 문서 수집 - Confluence, Notion, S3, 로컬 파일 등에서 원본 문서 가져오기
* 2. 문서 파싱 - PDF → 텍스트, HTML → 텍스트, 표/이미지 처리
* 3. 청킹 - RecursiveCharacterTextSplitter (500자, overlap 50) 또는 의미 기반/구조 기반 청킹
* 4. 임베딩 - 각 청크를 벡터로 변환 (예: bge-m3, text-embedding-3-small)
* 5. 벡터DB 저장 - 벡터 + 원본 텍스트 + 메타데이터(출처, 날짜 등) 저장

## Chunking ##
```
전략            정확도    속도     구현 난이도    적합한 경우
──────────────────────────────────────────────────────────
고정 크기        낮음     빠름     쉬움         빠른 프로토타입
재귀적 분할      중간     빠름     쉬움         범용 (기본 선택)
문장 기반        중간     빠름     쉬움         짧은 문서
의미 기반        높음     느림     중간         주제가 자주 바뀌는 문서
구조 기반        높음     빠름     중간         마크다운/HTML 문서
부모-자식        높음     중간     어려움       긴 문서, 문맥이 중요할 때
```


## ReRanking (Cross-Encoder/Bert) ##

Different from embedding model, reranker uses question and document as input and directly output similarity instead of embedding. You can get a relevance score by inputting query and passage to the reranker. And the score can be mapped to a float value in [0,1] by sigmoid function.

* https://huggingface.co/BAAI/bge-reranker-v2-m3
