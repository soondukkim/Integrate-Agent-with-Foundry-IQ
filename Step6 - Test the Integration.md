## 앱에서 에이전트 통합 테스트


## 앱에서 에이전트와 연결하세요

이제 에이전트와 프로그래밍적으로 상호작용할 수 있는 Python 애플리케이션을 만들 것입니다. 빠르게 시작할 수 있도록 GitHub 저장소에 스타터 파일이 제공됩니다.

### Visual Studio Code 로 앱 개발을 준비하세요

이제 Visual Studio Code를 사용해 앱을 개발해 봅시다. 귀하의 앱 코드 파일은 GitHub 저장소에 제공되었습니다.

1. 명령 프롬프트에서 **git clone** 명령을 사용해서 로컬 폴더에 소스를 복제하세요. (어느 폴더든 상관 없습니다)
   ```
   git clone https://github.com/MicrosoftLearning/mslearn-ai-agents   
   ```

    <img width="2000" height="1043" alt="image" src="https://github.com/user-attachments/assets/f944c93b-eb99-4293-a61e-c12a27e290de" />
    <br>

1. 소스가 복제되면 Visual Studio Code 에서 'C:\Download\mslearn-ai-agents\Labfiles\04-integrate-agent-with-foundry-iq' 폴더를 엽니다.

    > **참고**: Visual Studio Code에서 열려는 코드를 신뢰하라는 팝업 메시지가 뜨면, **Yes, I trust the authors** 옵션을 클릭해 계속 진행하세요.

1. 추가 파일이 설치되어 레포 내 파이썬 코드 프로젝트를 지원할 때까지 기다려야 합니다(요청이 있을 경우).

    > **참고**: 빌드 및 디버깅을 위해 필요한 자산을 설치하라는 메시지가 뜨면, **Not Now** 를 선택하세요.

1. **Explorer** 창에서, **Labfiles/04-integrate-agent-with-foundry-iq/Python** 폴더를 펼칩니다.

    제공된 파일에는 애플리케이션 코드, 설정 설정, 에이전트 클라이언트 스타터 코드가 포함되어 있습니다.

### 애플리케이션 설정

1. Visual Studio Code 에서 **Labfiles/04-integrate-agent-with-foundry-iq/Python** 폴더에서 **.env** 설정 파일을 엽니다.
   <img width="2000" height="1075" alt="image" src="https://github.com/user-attachments/assets/716c71a2-9927-4207-8a52-ebedac5690f4" />

1. 코드 파일에 **your_project_endpoint** 자리 표시자를 프로젝트 엔드포인트(Foundry 포털의 프로젝트 홈페이지에서 복사한 것)로 바꾸고, AGENT_NAME 변수를 에이전트 이름('OO-product-expert-agent')으로 설정하세요.
1. 임시 표시자를 교체한 후에는 파일을 저장하세요.

### 에이전트 클라이언트 코드를 작성하세요

> **팁**: 코드를 추가할 때는 올바른 들여쓰기를 유지하세요. 코멘트 들여쓰기 수준을 참고하세요.

1. Visual Studio Code 에서 **Labfiles/04-integrate-agent-with-foundry-iq/Python** 폴더에서 **agent_client.py** 코드 파일을 엽니다.
1. 제공된 스타터 코드를 검토하세요. 여기에는 다음이 포함됩니다 :
    - Import statements and configuration loading
    - The `send_message_to_agent()` function structure
    - The `display_conversation_history()` function
    - The main program loop

1. 첫 번째 **TODO** 주석을 찾아서 다음 코드를 추가해 프로젝트에 연결하고, OpenAI 클라이언트를 받고, 에이전트를 불러와, 새로운 대화를 만듭니다 :

   <br>
 
     <img width="2000" height="1075" alt="image" src="https://github.com/user-attachments/assets/033c1011-5991-40f4-9372-9da384e1e695" />

   <br>

   > **팁**: 들여쓰기 수준을 올바르게 유지하도록 주의하세요.

   <br>

        ```python
        # Connect to the project and agent
        credential = DefaultAzureCredential(
            exclude_environment_credential=True,
            exclude_managed_identity_credential=True
        )
        project_client = AIProjectClient(
            credential=credential,
            endpoint=project_endpoint
        )
    
        # Get the OpenAI client
        openai_client = project_client.get_openai_client()
    
        # Get the agent
        agent = project_client.agents.get(agent_name=agent_name)
        print(f"Connected to agent: {agent.name} (id: {agent.id})\n")
    
        # Create a new conversation
        conversation = openai_client.conversations.create(items=[])
        print(f"Created conversation (id: {conversation.id})\n")
        ```

1. `send_message_to_agent()` 함수 내 두 번째 **TODO** 주석을 찾아 메시지를 보내고 응답을 처리하는 코드를 추가하세요. MCP 승인 요청을 포함합니다 :
 
        ```python
        # Add user message to the conversation
        openai_client.conversations.items.create(
            conversation_id=conversation.id,
            items=[{"type": "message", "role": "user", "content": user_message}],
        )
        
        # Store in conversation history (client-side)
        conversation_history.append({
            "role": "user",
            "content": user_message
        })
        
        # Create a response using the agent
        response = openai_client.responses.create(
            conversation=conversation.id,
            extra_body={"agent_reference": {"name": agent.name, "type": "agent_reference"}},
            input=""
        )
    
        # Check if the response output contains an MCP approval request
        approval_request = None
        if hasattr(response, 'output') and response.output:
            for item in response.output:
                if hasattr(item, 'type') and item.type == 'mcp_approval_request':
                    approval_request = item
                    break
        
        # Handle approval request if present
        if approval_request:
            print(f"[Approval required for: {approval_request.name}]\n")
            print(f"Server: {approval_request.server_label}")
            
            # Parse and display the arguments (optional, for transparency)
            import json
            try:
                args = json.loads(approval_request.arguments)
                print(f"Arguments: {json.dumps(args, indent=2)}\n")
            except:
                print(f"Arguments: {approval_request.arguments}\n")
            
            # Prompt user for approval
            approval_input = input("Approve this action? (yes/no): ").strip().lower()
            
            if approval_input in ['yes', 'y']:
                print("Approving action...\n")
                
                # Create approval response item
                approval_response = {
                    "type": "mcp_approval_response",
                    "approval_request_id": approval_request.id,
                    "approve": True
                }
            else:
                print("Action denied.\n")
                
                # Create denial response item
                approval_response = {
                    "type": "mcp_approval_response",
                    "approval_request_id": approval_request.id,
                    "approve": False
                }
            
            # Add the approval response to the conversation
            openai_client.conversations.items.create(
                conversation_id=conversation.id,
                items=[approval_response]
            )
            
            # Get the actual response after approval/denial
            response = openai_client.responses.create(
                conversation=conversation.id,
                extra_body={"agent_reference": {"name": agent.name, "type": "agent_reference"}},
                input=""
            )
        
        ```
    
1. 코드를 추가한 후에는 파일을 **저장**하세요.


## 애플리케이션에서 에이전트의 지식기반 정보 검색 테스트

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
* [Step 04. 다양한 환경에서 Foundry IQ 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. Foundry Toolkit 에서 도구 호출에 대한 승인 설정 및 테스](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
