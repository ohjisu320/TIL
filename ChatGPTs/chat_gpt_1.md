# Chat GPT

- 최근 언어 및 이미지 분석에서 큰 파급력을 보임
    - 수익성, 일상까지의 범용성
- GPT 모델을 기반으로 한 대화형 AI
    - GPT
        - Generative
        - Pre-trained
        - Transformer
            - Deep Learning
            - Attention 매커니즘
                - Self-Attention 매커니즘 덕분에 자율학습이 가능해 짐.
                    - Attention 매커니즘: 지도학습
                    - Self-Attention 매커니즘: 지도/학습을 알아서 해줌
            - 병렬 처리 기능
                - RNN과 달리 순차 처리가 필요 없어 속도가 빠름
            - 스케일링 가능
                - 대규모 데이터 및 파라미터로 확장 가능
            
            `GPT 모델은 특히 Transformer의 **디코더 부분**만을 사용` 
            
            - 입력부는 띄어버리고 출력부만 “보이게?” 만듦

# Prompt Engineering

- OpenAI API
    - Context window: 입력 값의 뭉치([a, b, c], … z)
    - 토큰
        - 텍스트 데이터를 처리하고 이해하는 기본 단위
            - 이지만 언어마다, 또는 언어학자 마다 다르기 때문에 굉장히 복잡함
        - 문장에서 `단어` 의 역할? `형태소`의 역할 !
        - 영어보다 한글 문장을 표현하는데 **훨씬** 더 많은 토큰이 소요됨
            - 한글은 다양한 조합형 문자로 인해 많은 토큰이 필요
        - 각 토큰은 고유한 숫자가 매겨져 있음
        - 최대 입력 토큰 제한: 각 LLM 모델마다 최대로 입력할 수 있는 토큰 수가 제한
        - 토큰 수 확인: OpenAI tokenizer확인
- OpenAI API 주요 파라미터
    - 필수 파라미터
        - model: GPT 모델 이름
        - message: 대 메시지 기록
    - Optional
        - temperature: 다음 토큰 예측의 다양성을 조정 (0~2)
            - 응답의 창의성과 다양성 조정
                - 확률 분포를 날카롭거나 평탄하게 만드는 역할
                - 높은 확률은 더 높게 낮은 확률은 더 낮게
                    - 0 - 더 높게→ 일관성 있는 답이 나올 수 있음
                    - 2 - 더 낮게→ 다양한 답이 나올 수 있음
                        - Higher values like 0.8 will make the output more random
                        - while lower values like 0.2 will make it more focused and deterministic.
        - top_p: 선택할 토큰의 확률 범위를 제한 (0~1)
            - 누적 확률 기반으로 응답의 범위 제한
                - 확률 분포 범위 (상위 확률의 단어들만) 제한
                - 누적 확률 기준으로 단어 후보의 수를 제한
                - 응답의 신뢰성과 예측 가능성을 조정
                    - 0 - 답 후보가 매우 적음
                    - 1 - 모든 답이 답 후보
                        - 0.1 means only the tokens comprising the top 10% probability mass are considered.
        - temperature 와 top_p 함께 사용
            - 낮은 temperature + 높은 top_p → **정확한** 정보가 필요한 **문서** 만들 때
            - 높은 temperature + 낮은 top_p → **목적에 맞는** **창의적**이고 독창적인 응답.

## Google Notebook LM

[Google NotebookLM | Note Taking & Research Assistant Powered by AI](https://notebooklm.google/)

- pdf, web site, audio … → 참조해서 채팅할 수 있게 해주는 사이트?
- 면접질문을 만들 때 말로 물어보는 것 보다 유사한 유튜브 동영상이나 웹사이트 정보를 넣고 참조해서 질문을 만들어달라고 하면 현실 밀착형 질문을 얻을 수 있을 것임