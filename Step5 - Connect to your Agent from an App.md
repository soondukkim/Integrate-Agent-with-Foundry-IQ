## Foundry Toolkit 에서 도구 호출에 대한 승인 설정 및 테스트

포털에서 에이전트를 만들면, 기본적으로 Foundry IQ(지식) 도구가 승인 없이 실행됩니다. 앱이 각 지식 기반 조회를 검토하고 제어할 수 있도록 하면, Foundry Toolkit for VS Code 확장 기능을 사용하기 전에 승인을 요구하도록 에이전트를 변경해야 합니다.

> **참고**: 현재 Foundry 포털에서는 이 승인 동작을 변경하는 설정을 제공하지 않으므로, 대신 Foundry Toolkit 확장 기능에서 설정해야 합니다.

1. Visual Studio Code 에서 왼쪽 창에 **Extensions** 을 선택하거나 **Ctrl+Shift+X** 버튼을 누르고, 마켓플레이스에서 Microsoft 확장 프로그램을 `Foundry Toolkit for VS Code` 검색한 후 **설치** (아직 설치되지 않은 경우)를 합니다.

    > **참고**: 확장 프로그램은 현재 **Foundry Toolkit** 으로 표기되어 있으나, 일부 VS Code 라벨, 명령어 또는 이전 스크린샷은 여전히 **AI Toolkit** 을 참조할 수 있습니다. 이 LAB 에서는 그 이름들을 동일한 확장 경험을 가리키는 것으로 간주하세요.

    <img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/80da0668-337f-44ce-9af2-8abed861e519" />

1. 사이드바에서 **Foundry Toolkit** 아이콘을 선택하고, 요청이 뜨면 Azure 계정에 로그인하세요.
   
    > **참고**: Foundry Toolkit 확장 프로그램으로 로그인할 수 없다면, Azure 확장 프로그램을 선택해야 합니다. 거기서 로그인한 후 다시 파운드리 툴킷으로 돌아가 자원에 접근하세요.

1. **Microsoft Foundry Resources** 에서 **Set Default Project** 을 선택하고 이전에 만든 프로젝트를 선택하세요.
1. 프로젝트 섹션을 확장하세요. **Prompt Agents** 에서 에이전트 `OO-product-expert-agent` 를 선택해 **Agent Builder** 창을 엽니다.
1. **Tools** 섹션에서 앞에서 생성한 지식을 확인할 수 있습니다.  해당 지식의 오른쪽에 세점을 클릭하여 **Configure** 를 클릭합니다.
   <img width="1331" height="679" alt="image" src="https://github.com/user-attachments/assets/b0da31b4-d408-4105-9ef2-4c24838d5d6a" />

1. **도구 사용 전에 승인 필요** 드롭다운에서 **Ask for approval for all tools** 을 선택하고 **저장**하세요.
   <img width="437" height="330" alt="image" src="https://github.com/user-attachments/assets/a8ca070d-9287-42b7-a063-a6f9c32ba97b" />

    > **참고**: 이제 에이전트는 Foundry IQ를 사용해 지식 베이스를 검색할 때마다 승인을 요청하게 되며, 다음에 완료한 클라이언트 앱이 이를 처리합니다.

1. **Playground** 창에서 다음 쿼리를 확인해 보세요. (에이전트가 답변하기 전에 승인을 요청하는지 확인하세요) :
    - `텐트의 방수 기능에 대해 설명해 주세요.`
    - `데이팩과 익스페디션 백팩의 차이점은 무엇인가요?`
      <img width="2000" height="1075" alt="image" src="https://github.com/user-attachments/assets/04824715-c773-429d-9b7b-b99bc42a2e25" />

1. 빠른 테스트를 위해 다시 도구 승인 옵션을 수정합니다.  **Tools** 섹션에서 앞에서 생성한 지식의 **Configure** 를 클릭하세요.
1. **도구 사용 전에 승인 필요** 드롭다운에서 **Always approve all tools** 을 선택하고 **저장**하세요.

### 다음과 같은 기능을 확인합니다 :
1. 에이전트가 Foundry IQ 에 접근해야 하는 경우 **MCP** **MCP 승인 설정** 에 따라서 검색을 진행하기 전에 행동을 승인하거나 거부하도록 안내합니다.
1. 에이전트는 승인 결정을 바탕으로 Foundry IQ에서 정보를 검색합니다.


## 다음 단계

* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)

## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. 다양한 환경에서 Foundry IQ 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. Foundry Toolkit 에서 도구 호출에 대한 승인 설정 및 테스](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
