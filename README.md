# Integrate Agent with Foundry IQ (한글 가이드)

원문: [Integrate an AI agent with Foundry IQ | Develop AI Agents in Azure](https://microsoftlearning.github.io/mslearn-ai-agents/Instructions/Exercises/04-integrate-agent-with-foundry-iq.html)

## Microsoft Foundry 소개

<img src="https://ai.azure.com/favicon.ico" alt="Microsoft Foundry logo" width="64"/>

Microsoft Foundry는 엔터프라이즈 환경에서 AI 에이전트를 구축(Build), 배포(Deploy), 운영(Operate) 및 거버넌스(Govern)할 수 있도록 모델, 에이전트, 지식, 도구, 보안 기능을 통합 제공하는 엔터프라이즈 AI 플랫폼 입니다.

Foundry IQ 는 엔터프라이즈 환경의 지식과 데이터를 AI Agent 에 연결하여, 신뢰할 수 있는 근거 기반 답변과 업무 맥락 이해를 가능하게 하는 Microsoft 의 지능 계층(Intelligence Layer) 입니다.
- 기업의 지식과 데이터를 AI Agent 에 연결하여, 에이전트가 단순 LLM 추론이 아닌 조직의 실제 문서와 데이터를 기반으로 답변할 수 있도록 합니다.
- 엔터프라이즈 RAG(Retrieval-Augmented Generation) 방식으로 동작하여, 질문 시 관련 정보를 검색한 후 이를 근거로 답변을 생성하고 출처를 함께 제공합니다.
- 에이전트 서비스와 통합되어 AI Agent 가 기업 지식 뿐만 아니라 MCP 및 1,400 개 이상의 커넥터를 통해 다양한 비즈니스 시스템의 정보까지 활용할 수 있습니다.


## Hands-on Lab 개요

이 연습에서는 Microsoft Foundry 포털을 사용해 Foundry IQ와 통합되어 지식 베이스에서 정보를 검색하고 검색하는 에이전트를 만들 것입니다. 검색 자원을 만들고, 샘플 데이터로 지식 베이스를 구성하며, 포털에서 에이전트를 만든 후 Visual Studio Code에서 프로그래밍적으로 상호작용합니다

예상 소요 시간: 약 45분

> 참고
> 이 실습에서 사용하는 일부 기술은 미리 보기(Preview) 또는 활발히 개발 중인 기능일 수 있습니다. 환경에 따라 경고나 예상치 못한 동작이 발생할 수 있습니다.

## Prerequisites (사전 요구 사항)

실습을 시작하기 전에 아래 항목을 준비하세요.

- 충분한 권한 및 할당량(Quota)이 있는 [Azure 구독](https://azure.microsoft.com/free/)
- 로컬 PC에 설치된 [Visual Studio Code](https://code.visualstudio.com/)
- [Python 3.13](https://www.python.org/downloads/) 이상
- 로컬 PC에 설치된 [Git](https://git-scm.com/downloads)
- Azure AI 서비스 및 Python 프로그래밍에 대한 기본 이해

> 참고
> Python 3.13은 사용 가능하지만, 일부 종속성은 해당 버전에 대해 아직 컴파일되지 않았을 수 있습니다. 본 랩은 Python 3.13.12 환경에서 정상 동작이 확인되었습니다.

## 다음 단계

* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)

## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. Foundry 에이전트, AI Search 지식 기반 에서 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. 에이전트에서 도구 호출에 대한 승인 설정](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
