<h4 align='center'> 한국응용통계학회지 게재 논문 </h4>
<h2 align='center'> 임베딩 모델 및 Advanced RAG 기법을 활용한 한국어 텍스트 분류
<h3 align='center'> Embedding-Models-and-Advanced-RAG-for-Korean-Text-Classification </h3>
<br>   
<div align='center'>
<table>
    <thead>
        <tr>
            <th colspan="4"> First Author </th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <tr>
            <td align='center'><a href=""><img src="" width="100" height="100"></td>
            <td align='center'><a href=""><img src="" width="100" height="100"></td>
            <td align='center'><a href=""><img src="" width="100" height="100"></td>
            <td align='center'><a href=""><img src="" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/ByungwookYang"><img src="https://github.com/ByungwookYang.png" width="100" height="100"></td>
          <tr>
            <td align='center'>김혜윤</td>
            <td align='center'>노연수</td>
            <td align='center'>박종혁</td>
            <td align='center'>박민정</td>
            <td align='center'>양병욱</td>
          </tr>
        </tr>
    </tbody>
</table>

</div>

<!-- Using HTML to center the abstract -->
<div class="columns is-centered has-text-centered">
    <div class="column is-four-fifths">
        <h2>Abstract</h2>
        <div class="content has-text-justified">
 Retrieval-Augmented Generation(RAG)은 검색된 정보를 바탕으로 텍스트를 생성하는 방식으로 대규모 언어 모델이 가진 사전 학습 지식의 한계를 극복하기 위해 외부 지식을 검색하여 응답에 활용한다. RAG 기반 시스템에서 검색 정확도는 전체 응답 품질에 밀접한 영향을 미치기 때문에 이를 높이기 위한 다양한 고도화 기법이 중요한 과제로 부상하고 있다. 만약, 사용자 질의에 대해 보다 정밀한 문서 검색이 가능하다면 정확하고 신뢰성 있는 답변 생성이 가능해질 것으로 기대된다. 본 논문에서는 검색 정확도를 향상시키기 위해 다양한 임베딩 모델과 Advanced RAG 기법을 조합하여 네 개의 도메인에서 검색 및 분류 결과를 비교하고 분석하는 방법을 제안한다. 이를 위해, 도메인별 수집된 한국어 텍스트 데이터에 대해 다수의 임베딩 모델을 적용하고, HyDE, Multi-Query, Rerank 등 다양한 검색 고도화 기법을 활용하여 검색 성능과 이를 활용한 분류 성능 변화를 정량적으로 분석한다. 최종적으로, 성능 평가 결과를 통해 단순 임베딩 기반 검색보다 Advanced RAG 기법을 적용했을 때 더 정확한 검색과 높은 분류 성능을 달성할 수 있음을 확인한다.
        </div>
    </div>
</div>

---

## Background
GPT와 같은 LLM 모델들이 고도화 되면서 자연어 생성 뿐만 아니라 이해와 분석을 위한 분야에 사용될 수 있습니다. 기존 머신러닝 기반 분류기와 비교하여 LLM을 분류 문제에서도 효과적으로 활용될 수 있는지에 대한 연구가 활발하게 진행되고 있으며, 전통적인 분류 방식에 대한 새로운 대안으로 주목받고 있습니다.

## Objective
이 논문에서의 주요 목표는 임베딩 모델 간의 검색 성능을 비교하고, LLM을 활용한 고도화된 RAG 방법들의 분류 예측 성능을 비교하는 것입니다.

 

## Key Ideas(여기부터 수정 필요)
1. 연속된 시계열 데이터를 시퀀스 형태로 나열한 후 언어 모델이 이해할 수 있는 텍스트 형태로 변환합니다.
2. 단순히 순차적 행동을 텍스트로 나열하는 것이 아니라, 요약 정보를 문장 초두에 함께 제시합니다.
3. 사전 학습된 언어 모델을 HuggingFace로부터 불러와 분류 과제를 학습하여 예측을 수행합니다.
4. 동일한 정보량이 주어졌을 때, 언어 모델과 머신러닝 모델의 예측 성능을 비교합니다.

<p align="center">
  <img src="./images/preprocess_figure1.png" alt="sequence-to-text" width="800"/>
</p>
<p align="center">
    *Figure 1: Data preprocessing from sequence to text. Source: [논문링크](link).*
</p>

## Table: Mean of metrics of various RAG methods on the legal dataset

|  Score\Method  | No RAG | Naive RAG | Multi Query |  HyDE | Hybrid Search | Reranker | Heuristic Filtering and Summary
| ------------  | ---------------- | ------------------- | ------------------- | ------------------- | ------------------- | ------------------- | ------------------- |
|  F1-score  | 0.5466 | 0.6690 | 0.7170 | 0.7095 | 0.6682 | 0.6513 | 0.6278     
|  Precision | 0.6915 | 0.7291 | 0.6878 | 0.6527 | 0.7167 | 0.7064 | 0.6687
|   Recall   | 0.4521 | 0.6183 | 0.7490 | 0.7772 | 0.6261 | 0.6043 | 0.5918
|  Accuracy  | 0.5615 | 0.6430 | 0.6542 | 0.6276 | 0.6365 | 0.6216 | 0.5897

## Significance
첫번째 시나리오를 통해 언어 모델이 머신러닝 모델과 비슷한 성능을 보이고, 그 이외의 시나리오에서 더 우수한 분류 성능을 보여주어 언어 모형들의 예측 능력이 뛰어남을 확인하였다.

## Citation
```

```

