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

### Configure the application settings

1. In Visual Studio Code, in the **Labfiles/04-integrate-agent-with-foundry-iq/Python** folder, open the **.env** configuration file.
1. In the code file, replace the **your_project_endpoint** placeholder with the endpoint for your project (copied from the project **Home** page in the Foundry portal) and ensure that the AGENT_NAME variable is set to your agent name (which should be *product-expert-agent*).
1. After you've replaced the placeholder, save the file.

### Complete the agent client code

> **Tip**: As you add code, be sure to maintain the correct indentation. Use the comment indentation levels as a guide.

1. In Visual Studio Code, in the **Labfiles/04-integrate-agent-with-foundry-iq/Python** folder, open the **agent_client.py** code file.
1. Review the starter code that has been provided, including:
    - Import statements and configuration loading
    - The `send_message_to_agent()` function structure
    - The `display_conversation_history()` function
    - The main program loop

1. Find the first **TODO** comment and add the following code to connect to the project, get the OpenAI client, retrieve the agent, and create a new conversation:

    > **Tip**: Be careful to maintain the correct indentation level.

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

1. Find the second **TODO** comment inside the `send_message_to_agent()` function and add the following code to send messages and handle responses, including MCP approval requests:

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

1. After you've added the code, save the file.

1. Review the code now uses the conversations API to manage interactions with your agent, where:
    - A conversation is created and tracked by its ID
    - User messages are added to the conversation using `conversations.items.create()`
    - Responses are generated using `responses.create()` with an agent reference
    - **MCP approval handling**: When the agent needs to access Foundry IQ, it requests approval by returning an `mcp_approval_request` in the response output
    - The code prompts you to approve or deny the action before proceeding
    - After approval/denial, an `mcp_approval_response` is added to the conversation and a new response is generated
    - The agent retrieves information from Foundry IQ based on your approval decision

## Test the Integration

Now you'll run your application and test the agent's ability to retrieve information from the knowledge base.

1. In Visual Studio Code, open an integrated terminal for the **Labfiles/04-integrate-agent-with-foundry-iq/Python** folder by right-clicking the folder and selecting **Open in Integrated Terminal**.
1. First, create a virtual environment and install dependencies.

    ```
   python -m venv labenv
   ./labenv/Scripts/activate
   pip install -r requirements.txt
    ```

1. In the terminal pane, enter the following command to sign into Azure.

    ```
    az login
    ```

    > **Note**: In most scenarios, just using *az login* will be sufficient. However, if you have subscriptions in multiple tenants, you may need to specify the tenant by using the *--tenant* parameter. See [Sign into Azure interactively using the Azure CLI](https://learn.microsoft.com/cli/azure/authenticate-azure-cli-interactively) for details.

1. When prompted, follow the instructions to open the sign-in page in a new tab and enter the authentication code provided and your Azure credentials. Then complete the sign in process in the command line, selecting the subscription containing your Foundry resource if prompted.

1. In the terminal pane, run your application:

    ```
   python agent_client.py
    ```

1. When the application starts, test the agent with the following queries:

    **Query 1 - Product Categories:**

    ```
    What types of outdoor products does Contoso offer?
    ```

    When prompted for approval, type **yes** to allow the agent to search the knowledge base. Observe how the agent retrieves information from multiple documents in the knowledge base.

    **Query 2 - Specific Product Details:**

    ```
    Tell me about the weatherproof features of your tents.
    ```

    Approve the request and notice how the agent provides specific details from the tents catalog.

    **Query 3 - Product Comparisons:**

    ```
    What's the difference between your daypacks and expedition backpacks?
    ```

    Approve the request and see how the agent can synthesize information from the backpacks guide.

    **Query 4 - Accessories and Add-ons:**

    ```
    What camping accessories would you recommend for a weekend hiking trip?
    ```

    Approve the request and observe the agent's ability to provide recommendations based on the knowledge base.

    **Query 5 - Follow-up Question:**

    ```
    How much do those items typically cost?
    ```

    Notice how the agent maintains conversation context from your previous query.

1. Type `history` to view the complete conversation history.

1. Type `quit` when you're done testing.

### Review the results

Consider the following aspects of the agent's responses:

- **MCP Approval Flow**: Each time the agent needs to access the knowledge base, it requests approval, giving you control over external tool usage
- **Accuracy**: The agent provides information directly from the knowledge base documents
- **Citations**: The agent may include source references or document IDs
- **Context awareness**: The agent remembers previous messages in the conversation
- **Grounding**: The agent indicates when it cannot find relevant information in the knowledge base
- **Error handling**: The application gracefully handles errors and connection issues

## Summary

In this exercise, you:

- Created a Foundry project and agent with the new Foundry UI
- Built a knowledge base with product information documents
- Configured an agent in the portal with Foundry IQ enabled
- Connected to your agent from Visual Studio Code using the Python SDK
- Implemented a client application with MCP approval handling, conversation history, and error handling
- Tested the agent's ability to retrieve and synthesize information from the knowledge base with user-controlled approval for external tool access

This demonstrates how to integrate AI agents with Foundry IQ to create intelligent applications that can search and retrieve information from enterprise knowledge bases while maintaining conversational context.

## Clean up

If you've finished exploring Azure AI Agent Service and Foundry IQ, you should delete the resources you have created in this exercise to avoid incurring unnecessary Azure costs.

1. In a web browser, open the [Azure portal](https://portal.azure.com) at `https://portal.azure.com`.
1. Navigate to the resource group containing your Foundry resource and AI Search resources.
1. On the toolbar, select **Delete resource group**.
1. Enter the resource group name and confirm that you want to delete it.
