Commands to build and deploy agents using ADK 
Agent Development Tool kit:
Flexible and modular framework for developing and deploying AI agents.
Compatibility with other frameworks
Capable of complex tasks and complex workflows
 Command to install adk: pip install google-adk
Agent ability to understand the user request and generate response is powered 
By the LLM. here are two ways of llm calling 
By using google ai studio api key( we can provide api key in the environment file and we can call any of the gemini model by specifying the model name)
By using the google cloud vertex ai
( for this first we need to create the google cloud project, setup the google cli, and enabling the vertex ai api when we are using this vertex ai in environment file we need to specify the project name, location, and keep google\_geani\_use\_vertexai as true)
For running this agent we have different ways
Dev UI ( command : adk web)
 a) We will get an url when we run the above command in our browser,
 b) In top left corner we can select the respective agent in dropdown( if we do not find the respective agent name in the dropdown menu we need to make sure that we are adk web in parent folder are not).
 c) By looking at the events tab in top left we can inspect individual function calls, responses, model responses by clicking on that actions .
 d) By clicking on the trace button we can trace logs for each event where we can see latency for each function call.
Terminal ( command : adk run)
 Just by running adk run and agent \_name we can chat with out agent
API server( command : adk api\_server)
 The above command will enable us to create a local fast api server 
For Deploying agent some ways are:
Deploying to Agent Engine (this is an service managed by the vertex Ai in google cloud which is the easiest way to deploy our adk agents)
Deploying to cloud run( we can have full control over scaling and managing our agent by deploying it to the serverless architecture on google cloud)
Agent: Fundamental worker which is designed to perform the particular task and can use LLM for complex reasoning and it can also act as the deterministic controllers of the execution which are also called as the workflow Agents(SequentialAgent, ParallelAgent, LoopAgent)
Tool: Give abilities for agents by allowing them to interact with the external apis, run code and other services.
Callbacks: It is a custom code snippets provide by us to run at specific point to identify the agent process / to allow any modifications / logging.
Session management: which will handle the context of single conversation(session), where this session includes its history called as events and agent working memory for that conversation in state.
Memory: memory will enable agent to recall all the information about the user over multiple sessions which will provide long term context .where as state provides the short term session.
Artifact management: which will allow agent to save, load and mange files associated with in a session
Event: The basic unit of communication representing things that happen during a session (user message, agent reply, tool use), forming the conversation history.
Runner: The engine that manages the execution flow, orchestrates agent interactions based on Events, and coordinates with backend services.
Agent: we will have BAseAgent class as the foundation for all agents in adk. To create any agents we typically extend BaseAgent.
→ we extend BaseAgent in three main ways
LLM Agents: use LLMs as their engine to understand natural query, plan, and generate answers.
Workflow Agents: which are used to control the execution flow of the other agents without using llm for the flow control itself.
Custom Agents: created by extending the BaseAgent where we want to implement unique operational logic and any specific integrations not covered by the predefined types.
At what time we need to select what type of agents
Multi agent system:
 Real power of adk will come when we use these agents as the multi agents in the same project. Where as
 LLM Agents handle intelligent, language-based task execution.
 Workflow Agents manage the overall process flow using standard patterns.
 Custom Agents provide specialized capabilities or rules needed for unique integrations.
Model Context Protocol:
OPen standard design which is used to standardize how large language models communicate 
With external tools, data sources ands external applications.
Client server architecture
 Client— AI agent/llm host application
 Server — MCP server which is exposed of data resources, prompts and tools