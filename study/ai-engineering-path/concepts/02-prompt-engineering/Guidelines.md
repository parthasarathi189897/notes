Principles:

1. Write and clear specific instruction
	- #### Use delimiters to clearly indicate distinct parts of the input[](https://s172-28-22-52p8888.lab-w2-aws-production.deeplearning.ai/notebooks/l2_guidelines/l2-guidelines.ipynb#Tactic-1:-Use-delimiters-to-clearly-indicate-distinct-parts-of-the-input)
		- Delimiters can be anything like: ```, """, < >, `<tag> </tag>`, `:` 
		- Also, helpful in avoiding prompt injection through user input. Model can short of know that the text inside the delimiters are user input.
	- Ask for structured output
		- HTML or JSON
	- Check whether conditions are satisfied. Check assumptions are required to do the task
	- Fewshot prompting
2. Give model time to think
	- Specify the steps required to complete the task
	- Instruct the model to reason out it's solution before coming to the conclusion