# personal-game-recommendation
개인 데이터분석 프로젝트. 개인화 게임 추천 알고리즘 제작

- **개요** : 게임 플레이 데이터를 이용해 collaborative filtering 기반으로 개인별 맞춤 **게임을 추천해주는 시스템 제작**
- **성과** : 논리적 가설을 바탕으로 한 EDA역량과 인사이트 도출 역량 향상, 추천시스템 및 MF(Matrix Factorization)에 대한 이해/실 사용 역량 향상.
- **데이터** : 유저별 게임 플레이 기록 데이터 from kaggle([링크](https://www.kaggle.com/datasets/tamber/steam-video-games/data))
- **`Language / Tool`  : `Python` `Pandas` `Numpy` `Matplotlib` `Seaborn` `Google colab`**
- **과정 및 결과 :** 1️⃣전처리 및 EDA  ⇒  2️⃣user profile matrix 생성  ⇒  3️⃣추천 시스템 제작, 활용 방안 제안
    - **주요 전처리 및 EDA** : 유저 중심의 데이터 특성을 밝히는 EDA와 추천시스템에 사용할 user profile을 만들기 위한 전처리 위주로 진행.
        - MF(Matrix Factorization) 기법 중 하나인 SVD(Singular Value Decomposition)를 활용해 user profile matrix 생성
    - **결과**
        - 유저별 플레이 기록 및 플레이 시간 기반으로 해당 유저에게 추천할 게임 Top 10 도출하는 추천시스템 제작
            
            ex) 유저 76767의 게임 플레이 기록 Top10 & 유저 76767에게 추천하는 게임 리스트 Top 10
            
        
        | UserID | Game | play_hours |
        | ------ | -------------- | ---------- |
        | 76767  | Counter-Strike | 365 |
        | 76767 | Call of Duty World at War | 271 |
        | 76767 | Total War ATTILA | 207 |
        | …     |                   … | … |
        | 76767 | Call of Duty Black Ops | 22 |
        | 76767 | Call of Duty Modern Warfare 3 | 15.9 |
        | 76767 | Portal 2 | 15 |
        
        | Game | recommendation_score |
        | --- | --- |
        | APB Reloaded | 45.32 |
        | The Elder Scrolls V Skyrim | 32.29 |
        | Mount & Blade Warband | 13.79 |
        | … | … |
        | Left 4 Dead 2 | 5.63 |
        | Warframe | 4.72 |
        | Clicker Heroes | 4.66 |

- **Lesson Learned**
    - 추천 시스템의 여러 유형들이 각각 어떤 방식으로 컨텐츠를 추천하는지, 어떤 데이터에 어떤 추천 기법을 사용해야 하는지 학습할 수 있었고,
    그 중 특히 collaborative filtering 기법을 직접 적용함으로써 해당 기법의 특성에 대해 깊이 학습할 수 있었다.
    - **아쉬웠던 점**
        - 사용한 데이터에 feature가 충분치 않았다. 유저들이 직접 남긴 별점이나 리뷰, 혹은 게임 카테고리나 장르 등의 데이터가 추가로 있었다면
        더 정교하고 성능이 좋은 추천 시스템을 만들어볼 수 있었을 뿐 아니라 collaborative filtering 외에 knowledge based filtering, content based filtering 등의 다양한 추천 알고리즘을 적용해볼 수 있었을 것이다.
        - 사용한 데이터는 구매 데이터와 플레이 데이터로 나뉘는데, 구매 기반 개인화 추천 시스템과 플레이 기반 개인화 추천 시스템을 각각 만들어볼 수도 있었을 것 같다.
    - **성능 평가** : 아래와 같은 과정으로 성능을 평가해볼 수 있을 것이다.
        1. 오프라인 성능 평가 : 사용자의 아이템에 대한 선호 기록과 추천 시스템이 추천한 결과를 비교해서 시스템의 품질을 평가하는 방법으로, 온라인 성능 평가보다 반드시 선행되어야 한다. 
        해당 시스템은 ranking 기반 추천 시스템이므로 성능 평가 지표로는 Precision@K, Recall@K, Hit Rate@K 등을 사용할 수 있다.
        2. 온라인 성능 평가 : 사용자에게 직접 적용해보는 평가 방법이다. 정확하겠지만 성능이 좋지 않을 경우 사용자가 서비스를 떠나갈 수 있는 risky한, 즉 비용이 커질 수 있는 성능평가 방법이므로 오프라인 성능 평가에서 충분히 좋은 성능을 얻은 후에야 사용해볼 수 있을 것이다.
        
    - **활용 방안**
        - 특정 게임을 구매(혹은 장바구니에 담기)했을 때, 비슷한 게임을 구매한 다른 유저들의 선호 게임을 추천할 수 있다.
        - 일정 플레이 타임을 넘었을 때 해당 사용자가 선호할만한 다른 게임을 추천할 수 있다.
