## 앱에서 에이전트 통합 테스트

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
