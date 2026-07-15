### 에이전트를 도구 호출에 대한 승인을 요구하도록 설정하세

포털에서 에이전트를 만들면, 기본적으로 Foundry IQ(지식) 도구가 승인 없이 실행됩니다. 앱이 각 지식 기반 조회를 검토하고 제어할 수 있도록 하면, Foundry Toolkit for VS Code 확장 기능을 사용하기 전에 승인을 요구하도록 에이전트를 변경해야 합니다.

> **참고**: 현재 Foundry 포털에서는 이 승인 동작을 변경하는 설정을 제공하지 않으므로, 대신 Foundry Toolkit 확장 기능에서 설정해야 합니다.

1. Visual Studio Code 에서 왼쪽 창에 **Extensions** 을 선택하거나 **Ctrl+Shift+X** 버튼을 누르고, 마켓플레이스에서 Microsoft 확장 프로그램을 `Foundry Toolkit for VS Code` 검색한 후 **설치** (아직 설치되지 않은 경우)를 합니다.

    > **참고**: 확장 프로그램은 현재 **Foundry Toolkit** 으로 표기되어 있으나, 일부 VS Code 라벨, 명령어 또는 이전 스크린샷은 여전히 **AI Toolkit** 을 참조할 수 있습니다. 이 LAB 에서는 그 이름들을 동일한 확장 경험을 가리키는 것으로 간주하세요.

1. 사이드바에서 **Foundry Toolkit** 아이콘을 선택하고, 요청이 뜨면 Azure 계정에 로그인하세요.
   
    > **참고**: Foundry Toolkit 확장 프로그램으로 로그인할 수 없다면, Azure 확장 프로그램을 선택해야 합니다. 거기서 로그인한 후 다시 파운드리 툴킷으로 돌아가 자원에 접근하세요.

1. **Microsoft Foundry Resources** 에서 **Set Default Project** 을 선택하고 이전에 만든 프로젝트를 선택하세요.
1. 프로젝트 섹션을 확장하세요. **Prompt Agents** 에서 에이전트 `OO-product-expert-agent` 를 선택해 **Agent Builder** 창을 엽니다.
1. **Tools** 섹션에서 **Azure AI Search** 도구를 추가한 후, 이전에 만든 연결과 지식 베이스를 선택하세요.

    > **참고**: 에이전트가 여러 도구를 나열할 수 있습니다. Foundry 포털은 기본적으로 새로운 에이전트에게 **Web Search** 도구를 추가하므로, 다른 도구 대신 **Azure AI Search** 도구의 메뉴(세 점)를 지식 베이스에 선택하세요.
1. **도구 사용 전에 승인 필요** 드롭다운에서 **모든 도구에 대한 승인 요청** 을 선택하고 요청이 뜨면 변경 사항을 저장하세요.

이제 에이전트는 Foundry IQ를 사용해 지식 베이스를 검색할 때마다 승인을 요청하게 되며, 다음에 완료한 클라이언트 앱이 이를 처리합니다.

## 앱에서 에이전트와 연결하세요

이제 에이전트와 프로그래밍적으로 상호작용할 수 있는 Python 애플리케이션을 만들 것입니다. 빠르게 시작할 수 있도록 GitHub 저장소에 스타터 파일이 제공됩니다.

### Visual Studio Code 로 앱 개발을 준비하세요

이제 Visual Studio Code를 사용해 앱을 개발해 봅시다. 귀하의 앱 코드 파일은 GitHub 저장소에 제공되었습니다.

1. 명령 프롬프트에서 **git clone** 명령을 사용해서 로컬 폴더에 소스를 복제하세요. (어느 폴더든 상관 없습니다)
   ```
   git clone https://github.com/MicrosoftLearning/mslearn-ai-agents   

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

1. 코드를 추가한 후에는 파일을 저장하세요.

1. 코드를 검토하세요. 이제 대화 API를 사용해 에이전트와의 상호작용을 관리하세요. 다음과 같은 상황에서 :
    - 대화는 ID에 의해 생성되고 추적됩니다.
    - 사용자 메시지는 `conversations.items.create()` 를 사용해서 대화에 추가됩니다.
    - 응답은 agent_reference 가 포함된 `responses.create()` 를 사용하여 생성됩니다.
    - **MCP 승인 처리**: 에이전트가 Foundry IQ 에 접근해야 하는 경우, 응답 출력에 `mcp_approval_request` 를 반환하여 승인을 요청합니다.
    - 코드는 진행하기 전에 행동을 승인하거나 거부하도록 안내합니다.
    - 승인/거부 후 `mcp_approval_response` 가 추가되고 새로운 답변이 생성됩니다.
    - 에이전트는 승인 결정을 바탕으로 Foundry IQ에서 정보를 조회합니다.

