# Mortgage Assistant Agent

This example demonstrates the use of Amazon Bedrock Agents multi-agent collaboration with its built-in Routing Classifier feature. By simply enabling that mode for your supervisor, Bedrock automatically routes to the correct collaborating sub-agent using LLM intent classification optimized to route with sub-second latency. Contrast that with a traditional supervisor that must go through its own orchestration loop, a more expensive proposition that can take 3-6 seconds depending on which LLM you are using. This feature is most valuable when trying to build a unified customer experience across a set of sub-agents. In our example, we have 3 collaborators: one for general mortgage questions, one for handling conversations about Existing mortgages, and another for dealing with New mortgages.

Try sample prompts:

- "what's my balance?"
- "what are rates looking like over the past 2 weeks for new mortgages?"
- "what's your general guidance about refinancing mortgages?"

Each of these gets routed quickly to the right sub-agent for subsequent processing.
Conversation switching is seamless.

Routing also reverts automatically to full Supervisor mode if the request is truly
not mapping cleanly to a single collaborator. For example:

- "what interest rate do i have on my existing mortgage, and how does it compare to rates for new mortgages"

## Prerequisites

1. Clone and install repository

```bash
git clone https://github.com/awslabs/amazon-bedrock-agent-samples

cd amazon-bedrock-agent-samples/examples/amazon-bedrock-multi-agent-collaboration/mortgage_assistant

python3 -m venv .venv

source .venv/bin/activate

pip3 install -r src/requirements.txt
```

## Usage & Sample Prompts

Request model access in Bedrock for:
- Titan Text Embeddings V2
- Claude 3.5 Haiku
- Claude 3.5 Sonnet v2
- Claude 3.5 Sonnet
- Claude 3 Sonnet
- Claude 3 Haiku


1. Deploy Amazon Bedrock Agents

```bash
python3 main.py --recreate_agents "true"
```

2. Invoke

```bash
python3 main.py --recreate_agents "false"
```

## Not yet implemented
3. Cleanup

```bash
python3 main.py --clean_up "true"
```

## License

This project is licensed under the Apache-2.0 License.