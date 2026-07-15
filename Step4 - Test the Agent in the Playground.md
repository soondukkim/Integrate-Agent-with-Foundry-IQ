## Playground 에서 테스트

코드로 연결하기 전에 포털 플레이그라운드에서 에이전트를 테스트해 보세요.

1. **빌드** > **에이전트** 페이지에서 생성한 에이전트를 선택하세요.
1. 에이전트 페이지에서 플레이그라운드 탭이 선택된 것을 볼 수 있을 것입니다. 지식 섹션을 찾아 앞에서 생성한 **지식 기반 (Foundry IQ)** 을 선택하고 **저장** 하세요.

   <img width="531" height="307" alt="image" src="https://github.com/user-attachments/assets/c2022869-f7f6-434c-bbe2-a16532a58258" />


1. 다음 테스트 쿼리를 시도해 에이전트가 지식 베이스에서 정보를 가져올 수 있는지 확인해 보세요 :
    - `Contoso 는 어떤 종류의 텐트를 제공하나요?`
    - `XL 사이즈로 구매 가능한 백팩에 대해 알려주세요.`
    - `데이팩과 익스페디션 백팩의 차이점은 무엇인가요?`
   <br>

    <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/511de723-bd71-4e66-b965-e0a0ad19075d" />

<br>

    - 답변에 대한 **추적** 을 통해 에이전트의 작업 경로를 확인하세요
         
<br>
    <img width="1690" height="1037" alt="image" src="https://github.com/user-attachments/assets/bdacfdd3-74ed-4d52-a94b-3fe3ee94a06a" />

1. **게시** > **웹앱 미리보기** 를 통해서도 확인해 보세요 :

   <img width="480" height="385" alt="image" src="https://github.com/user-attachments/assets/e17b9eec-8f58-4525-832f-950e9fe7f7a5" />


<br>

    - '캠핑 용품에는 어떤 것들이 있나요?'
         
<br>

  <img width="2000" height="1075" alt="image" src="https://github.com/user-attachments/assets/92827415-0ef2-46d3-ac98-a949fde3c346" />
    
<br>

1. 답변을 검토하고 다음을 참고하세요 :
    - 에이전트는 지식 기반에서 구체적인 정보를 제공합니다
    - 출처 문서에 대한 인용이나 참고문헌이 포함될 수 있습니다
    - 에이전트은 제품 정보에 집중합니다


Foundry IQ 옵션을 변경하고 테스트해 보세요.

1. 지식 메뉴에서 생성한 **지식 기반 (Foundry IQ)** 를 선택하세요.
1. 지식 기반 옵션을 변경하세요 :
    - **검색 추론 작업** : 중간
    - **출력 모드** : 응답 생성
    - **지침에 답하기** : `전문가 답게 답변을 하고, 답변의 마지막에 전체 내용에 대한 요약을 한 문단으로 추가해주세요.`

<br> 
    <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/469c4ca0-28d8-4eaa-b53d-5a07f91be191" />


<br>

1. 에이전트 메뉴에서 생성한 에이전트를 선택하세요.
1. 다음 테스트 쿼리를 시도해 먼저 질문의 답변과 어떻게 다른지 확인해 보세요 :
    - `Contoso 는 어떤 종류의 텐트를 제공하나요?`
    - `XL 사이즈로 구매 가능한 백팩에 대해 알려주세요.`
    - `캠핑 용품에는 어떤 것들이 있나요?`
    - `데이팩과 익스페디션 백팩의 차이점은 무엇인가요?`

Azure Portal 에서 Foundry IQ 를 테스트해 보세요.

1. Azure Portal 'portal.azure.com' 탭으로 이동하세요.
1. 상단의 검색 창에서 **AI Search(Foundry IQ)** 를 검색하고, 만들어 놓은 **Search Service(Foundry IQ)** 를 선택하세요.

<br>
   <img width="1532" height="469" alt="image" src="https://github.com/user-attachments/assets/b676c600-6adf-4da2-867d-2912f34154df" />

1. **에이전트 검색** > **지식 기반** 에서 만들어 놓은 지식 기반 'kb-contosoproducts-OO' 을 선택하세요.
1. 지식 기반의 플레이그라운드를 확인할 수 있습니다.
1. 다음 테스트 쿼리를 시도해 먼저 질문의 답변과 어떻게 다른지 확인해 보세요 :
    - `백패킹 텐트와 돔 텐트의 특징을 비교해 주세요.`
    - `방수 기능이 되는 텐트의 종류별 특징과 가격을 알려주세요.`
    - `데이팩과 익스페디션 백팩의 차이점은 무엇인가요?`

<br>
    <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/f9c06039-6563-4b29-8c20-41af78415479" />
<br>

1. 답변을 검토하고 다음을 참고하세요 :
    - Foundry IQ 옵션 변경에 따라 답변이 달라집니다.
    - Azure Portal 의 지식 기반에서 더 구체적인 참조자료를 확인 및 디버그를 할 수 있습니다.

1. 다음 정보를 찾아 메모장에 복사하세요(나중에 필요할 것입니다):
    - **에이전트 이름**: 앞에서 만든 이름입니다 (`OO-product-expert-agent`)
    - **프로젝트 엔드포인트**: 프로젝트 설정 또는 홈페이지에서 찾을 수 있습니다
<br>

   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/0653f2ae-6459-4a5e-b7ed-c2611180a2f8" />

