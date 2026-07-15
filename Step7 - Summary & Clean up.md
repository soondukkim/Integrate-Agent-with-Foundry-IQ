## 요약

이 실습에서는 다음을 수행하였습니다 :

- new Foundry UI로 Foundry 프로젝트와 에이전트를 생성했습니다.
- 제품 정보 문서로 지식 베이스를 구축했습니다.
- Foundry IQ가 활성화된 상태로 포털에서 에이전트를 구성했습니다.
- Python SDK를 사용하여 Visual Studio Code에서 에이전트에 연결했습니다.
- MCP 승인 처리, 대화 기록 및 오류 처리가 포함된 클라이언트 애플리케이션을 구현했습니다.
- 외부 도구 액세스에 대한 사용자 승인 제어를 통해 에이전트가 기술 자료에서 정보를 검색하고 종합하는 기능을 테스트했습니다.

이 실습은 AI 에이전트를 Foundry IQ와 통합하여 대화 컨텍스트를 유지하면서 기업 기술 자료에서 정보를 검색하고 추출할 수 있는 지능형 애플리케이션을 만드는 방법을 보여줍니다.

## 리소스 정리

Azure AI Agent Service 및 Foundry IQ 탐색을 마쳤다면 불필요한 Azure 비용 발생을 방지하기 위해 이 실습에서 생성한 리소스를 삭제해야 합니다.

1. 웹 브라우저에서 `https://portal.azure.com` 주소로 [Azure portal](https://portal.azure.com) 을 엽니다.
1. Foundry 리소스와 AI Search 리소스가 포함된 리소스 그룹으로 이동합니다.
1. 도구모음에서 **리소스 그룹 삭제** 를 선택합니다.
1. 리소스 그룹 이름을 입력하고 삭제합니다.


## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. Foundry 에이전트, AI Search 지식 기반 에서 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. 에이전트에서 도구 호출에 대한 승인 설정](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
