## 앱에서 에이전트 통합 테스트

이제 애플리케이션을 실행하고 에이전트가 지식 기반에서 정보를 가져오는 능력을 테스트할 것입니다.

1. Visual Studio Code 에서 **Labfiles/04-integrate-agent-with-foundry-iq/Python** 폴더에서 오른쪽 클릭한 후 **Open in Integrated Terminal** 메뉴를 클릭하세요.

   <img width="445" height="715" alt="image" src="https://github.com/user-attachments/assets/c23d74a8-fa06-4b56-8c18-de09f2b7cb51" />

1. 가상 환경을 만들고 requirements.txt 를 통해 필요한 패키지를 설치하세요.

    ```
   python -m venv labenv
   ./labenv/Scripts/activate
   pip install -r requirements.txt
    ```

1. 터미널 창에서 다음 명령을 입력해 Azure 에 로그인 하세요.

    ```
    az login
    ```

    > **참고**: 대부분의 경우 az 로그인만 사용해도 충분합니다. 하지만 여러 테넌트에 구독이 있다면 --tenant 매개변수를 사용해 테넌트를 지정해야 할 수도 있습니다. 자세한 내용은 [Sign into Azure interactively using the Azure CLI](https://learn.microsoft.com/cli/azure/authenticate-azure-cli-interactively) 방식을 참조하세.

1. 안내를 따라 새 탭에서 로그인 페이지를 열고 제공된 인증 코드와 Azure 자격 증명을 입력하세요. 그 다음 명령줄에서 로그인 과정을 완료하고, Foundry 리소스가 포함된 구독을 선택하세요.

1. 터미널 창에서 애플리케이션을 실행하세요 :

    ```
   python agent_client.py
    ```

1. 애플리케이션이 시작되면 다음 쿼리로 에이전트를 테스트합니다 :

    **Query 1 - 제품 카테고리:**

    ```
    Contoso 는 어떤 종류의 아웃도어 제품을 제공하나요?
    ```

    **Query 2 - 특정 제품 세부사항:**

    ```
    텐트의 방수 기능에 대해 설명해 주세요.
    ```

    **Query 3 - 제품 비교:**

    ```
    데이팩과 익스페디션 백팩의 차이점은 무엇인가요?
    ```

    **Query 4 - 액세서리 및 Add-on:**

    ```
    주말 하이킹 여행에 추천할 만한 캠핑 액세서리는 무엇인가요?
    ```

    **Query 5 - 후속 질문:**

    ```
    그런 제품들의 가격은 보통 얼마인가요?
    ```

    상담원이 이전 문의의 대화 맥락을 어떻게 유지하는지 주목하세요.


1. 테스트가 끝나면 `quit` 명령으로 해당 앱을 종료하세요.


## 결과 검토

에이전트의 반응에서 다음과 같은 측면을 고려해 보십시오 :

- **MCP 승인 흐름**: 에이전트가 지식 베이스에 접근할 때마다 승인을 요청하여 외부 도구 사용을 제어할 수 있습니다
- **정확성**: 에이전트는 지식 기반 문서에서 직접 정보를 제공합니다
- **출처**: 에이전트는 출처 참조나 문서 ID를 포함할 수 있습니다
- **맥락 이해**: 상담원이 대화 중 이전 메시지를 기억합니다
- **그라운딩**: 에이전트가 지식 기반에서 관련 정보를 찾을 수 없을 때 표시합니다
- **오류 처리**: 애플리케이션은 오류 및 연결 문제를 원활하게 처리합니다


## 다음 단계

* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)

## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. Foundry 에이전트, AI Search 지식 기반 에서 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. 에이전트에서 도구 호출에 대한 승인 설정](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
