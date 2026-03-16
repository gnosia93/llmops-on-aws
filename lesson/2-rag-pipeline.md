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
