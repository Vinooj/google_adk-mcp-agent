# Google ADK Based Agents

The LlmAgent (often aliased simply as Agent) is a core component in ADK, acting as the "thinking" part of your application. It leverages the power of a Large Language Model (LLM) for reasoning, understanding natural language, making decisions, generating responses, and interacting with tools.

Unlike deterministic Workflow Agents that follow predefined execution paths, LlmAgent behavior is non-deterministic. It uses the LLM to interpret instructions and context, deciding dynamically how to proceed, which tools to use (if any), or whether to transfer control to another agent.


## Agent Development Steps 

1. LlmAgeny defnition generally resides in the agnets.py file. It have name, model, description and detailed instructions that disctate the behavior of the agent.
2. Define the tools that are avilable to the agent.
   - There is at least one agent called a root agent. This agent can have sub agents. The root agent is defined in a file called tools.py . This file can have agents defined other than the root agent.
   - sub-agents resides in its own seperate folder
   - There is also a concept called agent team. Don;t confuse it it sub_agents.  
4. Agnets als supports
   - Callbacks
   - Multi Agent control 
