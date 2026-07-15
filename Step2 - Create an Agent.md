## 에이전트 생성

1. Foundry Portal 홈페이지에서 **에이전트 빌드** 영역에서 **빌드시작** 버튼 클릭합니다.  또는 오른쪽 상단 메뉴에서 **빌드**를 클릭합니다.
   
   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/f537ba40-d439-4fc0-b013-60fa1bdbabdf" />


1. 에이전트를 설명적인 이름으로 만드세요 `OO-product-expert-agent`.
   
   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/4823c2ca-24e9-4649-98da-7d5fc80c0d27" />

    >  에이전트를 생성할 때는 기본 모델(예 `gpt-5`)을 배포합니다. 에이전트가 생성되면, 자동으로 해당 모델이 선택된 에이전트 플레이그라운드를 볼 수 있습니다.
   
      <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/48c0837b-0036-4973-91ec-babbb710bf92" />

1. 에이전트에게 다음과 같은 지침을 주세요:

    ```
    당신은 아웃도어 캠핑 및 하이킹 제품 전문 기업인 콘토소(Contoso)의 친절한 AI 도우미입니다.
    제품 또는 제품 카탈로그에 대한 질문에 답변할 때는 항상 지식 기반을 검색해야 합니다.
    자세하고 정확한 정보를 제공하고 출처를 반드시 명시하세요.
    에이전트에 연결된 지식 및 도구에서만 정보를 참조하고, 관련 정보를 찾지 못한 경우에는 명확하게 알려주세요.
    ```

1. 현재 에이전트 구성을 저장하려면 **저장** 을 클릭하세요.
   
   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/9f2ca54b-38a8-40a2-8bb9-301d237f4e5b" />



## 다음 단계

* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)

## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. 다양한 환경에서 Foundry IQ 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. Foundry Toolkit 에서 도구 호출에 대한 승인 설정 및 테스](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
