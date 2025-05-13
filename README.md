# Google ADK Based Agents

The LlmAgent (often aliased simply as Agent) is a core component in ADK, acting as the "thinking" part of your application. It leverages the power of a Large Language Model (LLM) for reasoning, understanding natural language, making decisions, generating responses, and interacting with tools.

Unlike deterministic Workflow Agents that follow predefined execution paths, LlmAgent behavior is non-deterministic. It uses the LLM to interpret instructions and context, deciding dynamically how to proceed, which tools to use (if any), or whether to transfer control to another agent.

Ref: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github

## Agent Development Steps 

1. LlmAgeny defnition generally resides in the agnets.py file. It have name, model, description and detailed instructions that dictate the behavior of the agent.
   ```python
         capital_agent = LlmAgent(
             model="gemini-2.0-flash",
             name="capital_agent",
             description="Answers user questions about the capital city of a given country.",
             instruction="""You are an agent that provides the capital city of a country.
                              When a user asks for the capital of a country:
                              1. Identify the country name from the user's query.
                              2. Use the `get_capital_city` tool to find the capital.
                              3. Respond clearly to the user, stating the capital city.
                              Example Query: "What's the capital of France?"
                              Example Response: "The capital of France is Paris."
         """,
             # tools will be added next
         )
   ```
   - There are primarily 2 ttypes of agent
     - Root agent
       - In the Agent Development Kit, a root agent is the top-level agent in a multi-agent system. Think ofit like the conductor of an orchestra who orchestrates the work of other artists.
       - The root agent is defined in a file called agents.py.
     - Sub-agents 
        - Sub-agent refers to an agent that is called or orchestrated by another (Parent) agent to perform a specific task as part of a larger workflow
        - They generally resides in its own seperate folder and has their own tools
        - Important take away here is that, the interaction between the root agent and the sub_agents are hiearchical similar in nature similar to a parent child relationship.
        - If your agent relationship is not hierarchical, the you should look inot Multi Agent concept.
3. Define the tools that are avilable to the agent.
   - Agents leverage tools to get things done. Tools are python functions and is registered with the agents in agents.py file.
5. Agents also supports
   - Callbacks
   - Multi Agent control
  
## Muti Agent vs Sub Agent 

Here are some key things a more sophisticated multi-agent system can do that might be challenging or impossible with just a root agent and its sub-agents:

1. Decentralized Problem Solving and Emergent Behavior:
   - **Multi-Agent:** Agents can independently assess the environment, communicate with each other, and dynamically adjust their strategies based on the collective intelligence of the team. This can lead to emergent behaviors and solutions that weren't explicitly programmed into any single agent.   
   - **Sub-Agents:** Sub-agents are typically more reactive and follow the explicit instructions and workflow defined by their parent. Their actions are largely predetermined by the parent's logic.
2. Robustness and Fault Tolerance:
   - **Multi-Agent:** If one agent in a team fails, other agents can potentially take over its responsibilities or adapt to the loss, allowing the system to continue functioning (albeit potentially at a reduced capacity).   
   - **Sub-Agents:** If a crucial sub-agent fails, the parent agent's workflow is disrupted, and the entire process might stall unless the parent has explicit error handling and redundancy mechanisms built in.
3. Scalability and Flexibility:
   - **Multi-Agent:** Adding new capabilities or adapting to changing requirements can often be achieved by adding new agents to the team without significantly altering the core logic of existing agents. The communication protocols (like A2A) facilitate seamless integration.   
   - **Sub-Agents:** Expanding the functionality often requires modifying the parent agent's logic to incorporate and orchestrate new sub-agents, potentially leading to more complex and less modular code.
4. Parallel and Asynchronous Operations with Independent Decision-Making:
   - **Multi-Agent:** Agents in a team can operate more independently and asynchronously, making decisions and taking actions in parallel based on their local information and interactions with other agents.   
   - **Sub-Agents:** While a root agent can orchestrate parallel execution of sub-agents, the decision-making and flow are still centrally controlled by the root. Sub-agents don't typically have the autonomy to initiate actions or change course based on peer interactions.
5. Negotiation, Collaboration, and Conflict Resolution:
   - **Multi-Agent:** Agents in a team can engage in more complex interactions like negotiation, bargaining, and conflict resolution to reach a mutually beneficial outcome. This requires agents to have their own goals, beliefs, and the ability to reason about the perspectives of others.   
   - **Sub-Agents:** Sub-agent interactions are usually limited to the parent passing information and the sub-agent returning a result. There's typically no concept of negotiation or independent conflict resolution among sub-agents.
6. Learning and Adaptation at the Team Level:
   - **Multi-Agent:** A team of agents can collectively learn from experience and adapt their strategies as a group. This could involve agents sharing learned knowledge or evolving their communication protocols.   
   - **Sub-Agents:** Learning is usually confined to individual sub-agents (if implemented) and is directed by the parent agent. There's less opportunity for emergent learning at the system level based on inter-agent dynamics.
7. Handling Distributed Environments and Data:
   - **Multi-Agent:** In scenarios where data and resources are distributed, a multi-agent system can deploy agents closer to the data sources, enabling more efficient processing and decision-making. Agents can coordinate across these distributed environments.   
   - **Sub-Agents:** A root agent and its sub-agents typically operate within a more centralized context, making it more challenging to effectively manage and process information across geographically dispersed locations.
   
In essence, a true multi-agent system moves beyond a simple command-and-control hierarchy. 1  It embraces concepts of autonomy, communication, collaboration, and emergence to tackle problems that require distributed intelligence, adaptability, and robustness beyond what a centrally orchestrated set of sub-agents can easily provide. 2    

