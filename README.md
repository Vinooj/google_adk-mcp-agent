# Google ADK Based Agents

The LlmAgent (often aliased simply as Agent) is a core component in ADK, acting as the "thinking" part of your application. It leverages the power of a Large Language Model (LLM) for reasoning, understanding natural language, making decisions, generating responses, and interacting with tools.

Unlike deterministic Workflow Agents that follow predefined execution paths, LlmAgent behavior is non-deterministic. It uses the LLM to interpret instructions and context, deciding dynamically how to proceed, which tools to use (if any), or whether to transfer control to another agent.


## Agent Development Steps 

1. LlmAgeny defnition generally resides in the agnets.py file. It have name, model, description and detailed instructions that disctate the behavior of the agent.
   - There are primarily 2 ttypes of agent
     - Root agent
       - In the Agent Development Kit, a root agent is the top-level agent in a multi-agent system. Think ofit like the conductor of an orchestra who orchestrates the work of other artists.
       - The root agent is defined in a file called agents.py.
     - Sub-agents 
        - Sub-agent refers to an agent that is called or orchestrated by another (Parent) agent to perform a specific task as part of a larger workflow
        - They generally resides in its own seperate folder and has their own tools
   - There is also a concept called agent team. Don;t confuse it it sub_agents. 
3. Define the tools that are avilable to the agent.
   - Agents leverage tools to get things done. Tools are python functions and is registered with the agents in agents.py file.
5. Agents also supports
   - Callbacks
   - Multi Agent control 
