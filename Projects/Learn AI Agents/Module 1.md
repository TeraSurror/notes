AI agent is a loop
```
messages = [system, user_task]
loop:
	response = llm(messages, tools)
	if response has no tool calls:
		return response.text
	for call in response.tool_calls:
		result = execute(call)
	messages += [response, results]
```

Production pillars:
1. Quality
2. Reliability
3. Latency
4. Cost
5. Safety and security
6. Operability

Sampling in LLMs
At step, the model produces a probability distribution over the next token, and sampling picks one.
1. Temperature: rescales the distribution: low = sharper (more likely token dominate), high = flatter (more diverse). 0 = always picks the top token
2. Top_p (nucleus sampling): sample only from the smallest set of tokens whose probabilities sum to p
3. Temperature 0 is not deterministic in practice.
4. Parameter support varies by model.

Budgets:
Pre-flight check: Check with an estimate (eg known input tokens  + max_tokens as worst case outputs) prevents starting a call you can't afford
Post-call: Charge records what was actually spent. Record before raising

jjj






