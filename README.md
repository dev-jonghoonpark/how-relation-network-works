# How Relation Network Works

**Relation Network — 모든 쌍을 같은 함수로 비교하기.** Santoro 외(DeepMind, NeurIPS 2017)의 「A simple neural network module for relational reasoning」을 브라우저에서 직접 실험하며 이해하는 인터랙티브 교육 자료입니다. 관계를 계산하는 능력을 학습시키지 않고 구조에 박아 둔 식 한 줄, RN(O) = f<sub>φ</sub>(Σ<sub>i,j</sub> g<sub>θ</sub>(o<sub>i</sub>, o<sub>j</sub>))를 하나씩 뜯어 보고, 마지막에는 브라우저에서 작은 RN과 MLP를 나란히 학습시킵니다.

🔗 **[데모 바로가기](https://dev-jonghoonpark.github.io/how-relation-network-works/)**

## 다루는 내용

1. **관계 질문과 비관계 질문** · Sort-of-CLEVR 장면에서 여섯 가지 질문(모양·좌우·상하 / 가장 가까운·가장 먼·같은 모양 개수)과 답에 필요한 객체·쌍 표시. CNN+MLP가 관계 질문 63%, 가장 가까운/먼 질문 52.3%에 멈춘 결과
2. **식 (1): 모든 쌍에 같은 g** · 객체 수를 바꾸며 완전 방향 그래프와 n × n 쌍 표, g 하나가 쌍을 차례로 지나가며 합을 쌓는 애니메이션. 데이터 효율(관계 함수를 n² 번 배우지 않고 한 번 배운다)
3. **더하기가 주는 것: 순서 불변** · 객체 순서를 섞으면 RN 출력은 그대로(차이 ~10⁻¹⁵), 이어 붙인 MLP 출력은 바뀜. Deep Sets와의 관계
4. **질문을 g에 넣기 — 손으로 짠 g** · 11비트 질문, e<sup>−d/τ</sup>를 더해 “가장 가까운 것”을 고르는 g, τ에 따른 정답률(장면 2,000개 채점), 질문에 따라 켜지는 6 × 6 쌍 표
5. **픽셀에서 객체 만들기** · 특징 맵 칸을 객체로 보는 방법과 좌표 태깅. 좌표를 끄고 칸을 섞으면 RN 출력이 한 자리도 안 바뀌는 것. CLEVR 설정으로 계산한 객체 64개·쌍 4,096개
6. **브라우저에서 학습하는 RN과 MLP** · 객체 벡터 Sort-of-CLEVR로 RN(4,524 파라미터)과 MLP(5,676)를 30,000 스텝 학습. 가장 가까운/먼 질문 RN 93.1%·94.3% vs MLP 71.6%·72.4%. 미리 학습한 가중치 불러오기, 학습한 g의 쌍별 반응 보기
7. **CLEVR 결과** · 표 1을 범주별 막대로 — RN 95.5% vs 사람 92.6%, 속성 비교에서 누적 어텐션 52.3% vs RN 97.1%, 상태 기술 96.4%
8. **bAbI와 움직이는 공** · 문장을 객체로 쓴 bAbI 18/20(기초 귀납 오류 2.1%), 공-용수철 시뮬레이션에서 “거리가 변하지 않는 쌍” 규칙으로 연결 찾기와 그 한계(A–B–C 묶음의 양 끝)
9. **n²의 값과 그다음** · 객체 수에 따른 RN과 셀프 어텐션의 계산량 비교, 두 식을 나란히 놓고 본 공통점과 차이, Relational RNN·그래프 네트워크로 이어진 흐름
10. **퀴즈** 6문항

## 참고

- Santoro 외 (2017), *A simple neural network module for relational reasoning* — [arXiv:1706.01427](https://arxiv.org/abs/1706.01427)
- Johnson 외 (2017), *CLEVR: A Diagnostic Dataset for Compositional Language and Elementary Visual Reasoning* — [arXiv:1612.06890](https://arxiv.org/abs/1612.06890)
- Zaheer 외 (2017), *Deep Sets* — [arXiv:1703.06114](https://arxiv.org/abs/1703.06114)
- Vaswani 외 (2017), *Attention Is All You Need* — [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)
- Battaglia 외 (2018), *Relational inductive biases, deep learning, and graph networks* — [arXiv:1806.01261](https://arxiv.org/abs/1806.01261)

[how-ai-works](https://github.com/dev-jonghoonpark/how-ai-works) 시리즈의 일부입니다.
