<h4 align='center'> 한국응용통계학회지 게재(예정) 논문 </h4>
<h2 align='center'> 임베딩 모델 및 Advanced RAG 기법을 활용한 한국어 텍스트 분류
<h3 align='center'> Embedding-Models-and-Advanced-RAG-for-Korean-Text-Classification </h3>
<br>   
<div align='center'>
<table>
    <thead>
        <tr>
            <th colspan="5"> First Author </th>
        </tr>
    </thead>
    <tbody>
        <tr>
          <tr>
            <td align='center'><a href="https://github.com/HyeyoonKim0711"><img src="https://github.com/HyeyoonKim0711.png" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/1020nys"><img src="https://github.com/1020nys.png" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/jhyeok2841"><img src="https://github.com/jhyeok2841.png" width="100" height="100"></td>
            <td align='center'><a href="https://github.com/min0908"><img src="https://github.com/min0908.png" width="100" height="100"></td>
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

 

## Key Ideas(임시로 넣어둔 것. 아래 그림 추가하는 것이랑 맞춰서 수정 가능)
1. 임베딩 모델을 활용해 데이터의 벡터스토어를 구축합니다.
2. 벡터스토어에서 입력 문장과 유사한 문장을 검색합니다.
3. 검색 결과와 함께 GPT-3.5-turbo API를 호출하여 입력 문장의 분류를 예측합니다.
4. 다양한 데이터셋을 대상으로 고도화된 RAG 방법들을 적용하고, 각 방법의 분류 예측 성능을 비교 분석합니다.

<p align="center">
  <img src="./images/preprocess_figure1.png" alt="sequence-to-text" width="800"/>
</p>
<p align="center">
    *Figure 1: Data preprocessing from sequence to text. Source: [논문링크](link).*
</p>

## Table: Mean of metrics of various RAG methods on datasets

<table>
  <tr>
    <td>

<strong>Legal Dataset</strong>  
<table>
<tr><th>Score\Method</th><th>No RAG</th><th>Naive</th><th>Multi</th><th>HyDE</th><th>Hybrid</th><th>Rerank</th><th>Heur.</th></tr>
<tr><td>F1</td><td>0.5466</td><td>0.6690</td><td>0.7170</td><td>0.7095</td><td>0.6682</td><td>0.6513</td><td>0.6278</td></tr>
<tr><td>Precision</td><td>0.6915</td><td>0.7291</td><td>0.6878</td><td>0.6527</td><td>0.7167</td><td>0.7064</td><td>0.6687</td></tr>
<tr><td>Recall</td><td>0.4521</td><td>0.6183</td><td>0.7490</td><td>0.7772</td><td>0.6261</td><td>0.6043</td><td>0.5918</td></tr>
<tr><td>Accuracy</td><td>0.5615</td><td>0.6430</td><td>0.6542</td><td>0.6276</td><td>0.6365</td><td>0.6216</td><td>0.5897</td></tr>
</table>

</td>
<td>

<strong>Ethical Dataset</strong>  
<table>
<tr><th>Score\Method</th><th>No RAG</th><th>Naive</th><th>Multi</th><th>HyDE</th><th>Hybrid</th><th>Rerank</th><th>Heur.</th></tr>
<tr><td>F1</td><td>0.6720</td><td>0.7033</td><td>0.7045</td><td>0.6773</td><td>0.7438</td><td>0.7140</td><td>0.6617</td></tr>
<tr><td>Precision</td><td>0.6778</td><td>0.7407</td><td>0.6048</td><td>0.6775</td><td>0.7056</td><td>0.6650</td><td>0.7133</td></tr>
<tr><td>Recall</td><td>0.6679</td><td>0.6715</td><td>0.8438</td><td>0.6774</td><td>0.7828</td><td>0.7712</td><td>0.6173</td></tr>
<tr><td>Accuracy</td><td>0.6746</td><td>0.7184</td><td>0.6461</td><td>0.6770</td><td>0.7289</td><td>0.6911</td><td>0.6845</td></tr>
</table>

</td>
  </tr>
  <tr>
    <td>

<strong>Complaint Dataset</strong>  
<table>
<tr><th>Score\Method</th><th>No RAG</th><th>Naive</th><th>Multi</th><th>HyDE</th><th>Hybrid</th><th>Rerank</th><th>Heur.</th></tr>
<tr><td>Macro F1</td><td>0.3118</td><td>0.6467</td><td>0.6816</td><td>0.6455</td><td>0.6549</td><td>0.6527</td><td>0.4650</td></tr>
<tr><td>Weighted F1</td><td>0.4249</td><td>0.6665</td><td>0.6833</td><td>0.6488</td><td>0.6765</td><td>0.6556</td><td>0.6068</td></tr>
<tr><td>Precision</td><td>0.4252</td><td>0.7033</td><td>0.7085</td><td>0.6705</td><td>0.6937</td><td>0.6725</td><td>0.5235</td></tr>
<tr><td>Recall</td><td>0.3228</td><td>0.6386</td><td>0.6769</td><td>0.6410</td><td>0.6495</td><td>0.6508</td><td>0.4513</td></tr>
<tr><td>Accuracy</td><td>0.4398</td><td>0.6581</td><td>0.6786</td><td>0.6443</td><td>0.6709</td><td>0.6537</td><td>0.5889</td></tr>
</table>

</td>
<td>

<strong>Commerce Dataset</strong>  
<table>
<tr><th>Score\Method</th><th>No RAG</th><th>Naive</th><th>Multi</th><th>HyDE</th><th>Hybrid</th><th>Rerank</th><th>Heur.</th></tr>
<tr><td>Macro F1</td><td>0.4946</td><td>0.7379</td><td>0.7395</td><td>0.7069</td><td>0.7477</td><td>0.6724</td><td>0.5600</td></tr>
<tr><td>Weighted F1</td><td>0.5929</td><td>0.7462</td><td>0.7444</td><td>0.7236</td><td>0.7528</td><td>0.6952</td><td>0.6702</td></tr>
<tr><td>Precision</td><td>0.5720</td><td>0.7589</td><td>0.7559</td><td>0.7296</td><td>0.7631</td><td>0.7193</td><td>0.7066</td></tr>
<tr><td>Recall</td><td>0.5157</td><td>0.7473</td><td>0.7475</td><td>0.7157</td><td>0.7554</td><td>0.6883</td><td>0.6570</td></tr>
<tr><td>Accuracy</td><td>0.6181</td><td>0.7557</td><td>0.7524</td><td>0.7325</td><td>0.7606</td><td>0.7117</td><td>0.6828</td></tr>
</table>

</td>
  </tr>
</table>

 



## Significance
첫번째 시나리오를 통해 언어 모델이 머신러닝 모델과 비슷한 성능을 보이고, 그 이외의 시나리오에서 더 우수한 분류 성능을 보여주어 언어 모형들의 예측 능력이 뛰어남을 확인하였다.

## Citation
```

```

