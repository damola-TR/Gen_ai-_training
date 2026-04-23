Learning Summary
The pre-requisites to interacting with the OpenRouter API are the following libraries: 
1.	openai: It’s a python SDk to interact with OpenAI APIs
2.	python-dotenv: to manage environment variables securely 
3.	requests: for HTTPS requests 

After initializing libraries, the API Key is retrieved either hard-coded or from the user to set as an environmental variable and verify the key’s format to avoid an issue. 
OpenRouter is an API gateway. Single interface to access multiple LLM models. 
Then there are three function definitions, call_openrouter_api() to handle authentication, https request and to collect the Json response for the prompt sent out; extract_response() to extract readable text from the Json reply and display_usage() to show the token usage statistic for better understanding.
On initial run of the code to compare the responses for the prompt given to different models. The open ai ChatGPT turbo model provides a successful output, while Mistral causes an error: 'No endpoints found for mistralai/mistral-small.' 
This gave an error code of 404 in the error message which means that the API end-point wasn’t found by the server.
Here: I decided to use some other Open source model, replaced the mistralai-small with the mistralai-large.
This led to success.

The output now looked like this:
 

This indicates that comparatively GPT used less tokens. Both the answers seem cut off as the answer was truncated at 100, i.e. only 100 characters of the final answer is displayed.

Prompt Engineering
a prompt s any input you give to an LLM to get a response. The quality of your prompt directly affects the accuracy/ quality of the response form the LLM. Hence the need of prompt engineering.

Principles of writing a prompt:
1.	Be Specific: Clear instructions get better results
2.	Provide Context: Give the model background information
3.	Use Examples: Few-shot learning (showing examples) improves performance
4.	Define Output Format: Specify how you want the response structured
5.	Set a Role: Tell the model what role to play (e.g., "You are a Python expert")

Prompt structure 
First the context -> Task -> Constraints -> Output format

Prompt examples:
Example 1: helped understand the importance of a good quality prompt with proper context, constraints and output format. Upon researching more on this type of prompt it was learnt that this is a zero-shot prompt.

 Example 2: This is a few shot prompt, here the examples are provided as context to let the LLM know the sort of output/response format that is expected.

Example 3: Role-playing context. This set the tone of the response to a more conversational response. The LLM responded as prompted.

LLM’s parameters:
1.	temperature: controls creativity (0.0 < 1.0 < 2.0) lower for facts, higher of creative answers. 1.0 is balanced.
2.	max_tokens: determine the length of responses (limits length and cost).
3.	top_p: alternative to temperature, only considers tokens with cumulative probability up to the provided value. Can be used with temperature for fine tuning the answer.

Exp 1: Temperature 0.1 gave a more concise answer while 1.5 gave a more elaborate answer that mimicked a human.
Exp 2: Showed how responses length could be controlled through token limitation hence controlling costs.
Exp 3: tweaked the max_tokens and temperature parameters to get various responses for idea generation to name app. Gathered a better understanding of the parameters and how they affect the responses.

Section 7: Errors
Common error codes:
1.	401: Unauthorized – Invalid API Key
2.	429: Too Many requests – Rate limit exceeded
3.	500: Server Error – OpenRouter server issue
4.	504: Timeout - Request took too long
5.	404 – API end-point could not be found by server

Coding Best practices for error handling:
•	Always wrap API calls in try-except blocks
•	Implement retry logic with exponential backoff
•	Check rate limit headers
•	Log errors for debugging
•	Set reasonable timeouts

Section 8:
Understood the real life applications of agentic AI through examples of text summarization, translation, code generation, content analysis and conversation AI .





