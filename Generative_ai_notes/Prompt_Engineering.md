# Prompt Engineering
It is the art of crafting quality prompt for the model to generate accurate output. This prompt guide the llms in producting accuracy output.
<br>
The process involves:
* optimizing prompt length
* the prompt tone and writing style and structure in relation to the task

## what is a prompt:
A prompt is an input that the model uses to predict a specific output. The models output efficacy is dependent on the prompt- It is an input provided to the to model to generate a response
<br>

## How LLMS Works:
llms works by taking sequential text and predict the next token based on the data it is train on

## Prompt Usage
They can be use for the understanding annd the generation of the following:
* Text summarization
* code generation
* information extraction
* question and answer
* code documentation and reasoning

<br>
To get an accurate result from the llms, it is not just about the prompt alone, there are also some configuration that need to set to give accurate response. This are know as the output configuration. 

<br>
Let's understand __"LLMS Output Configuration"__

<br>

## LLMS Output Configuration
LLMS has configuration that controls the output of the model. Effective prompt engineering is to optimize this settings for the task at hand. 
<br>
Some examples of this settings are :

## Output Length
This set the number of geneerated tokens for the response. number of tokens affect the computation, the response time and the cost. The more the tokens generated the more the compute cost and slow response time. Hence the need to craft your prompt to accomodate your response. This will help the model to know when to stop predict and stop it from eating more compute resource.

It is also important to note that llms predict the probalities of what the next tokens will be. hence the need for sampling control setting to help get the next tokens

## Temperature
This control the degree of randomness in tokens selection. The lower the temperature the more deterministic the ouput is. The higher the token the more random the output is which can leads to unexpected results.

Higher temperature are good for creative output task, where rigid or preise output is not required and the desire for some degree of randomness.

## Top K and Top P
They restrict the predicted token to be from the top predicted tokens in the sample.

__Top k__: the higher it is the more varied  and creative the output is. Just like the Temperature. The lower Top k is the more restrictive it is. Top k of 1 is equivalent of Temperature of 0 which is know as greedy decoding- The highest probability is always selected.

__Top P__: select predicted token that does not exceed a cummulative threshold.

You can use both sampling setting together. experiment with them and see your output.

NB:
As a general starting point, a temperature of .2, top-P of .95, and top-K of 30 will give you
relatively coherent results that can be creative but not excessively so. If you want especially
creative results, try starting with a temperature of .9, top-P of .99, and top-K of 40. And if you
want less creative results, try starting with a temperature of .1, top-P of .9, and top-K of 20.
Finally, if your task always has a single correct answer (e.g., answering a math problem), start
with a temperature of 0.
_except_ from prompt_engineeing_white_paper from google.


## Prompt Engineering Techniques
* General prompting: Also know as zero where you give no examples and just give the description of the task

* One-shot and Few short prompt
This involves giving the model some examples thereby heloping the models understand what is required. This example can help guide the model to a desired output pattern.

when you supply the model with one example- one short. when you passes in few or more example- hence the name few shorts. few short prompt increase the chance that the models follow the pattern.

## System, Contextual and Role 
* System prompt: defines the big pictures and the model should be doing. The purpose of the model is define. it is use for generating output that meets specific requirement. it provides extra task to the system.

* Contextual prompting: providing background information to the current conversation or task. providing task specific information to guide the model.

* Role prompt: the model taking a character and give output base on the role taken.
Here are some styles you can choose from which I find effective:
Confrontational, Descriptive, Direct, Formal, Humorous, Influential, Informal,
Inspirational, Persuasive

## Step back Prompting
It first consider a general question related to the specific task at hand, and then feeding the
answer to that general question into a subsequent prompt for the specific task. using step increase the accuracy of your prompt.

# Chain of Thought(COT)
This causes the llms to generate intermediate reasoning steps as it product the output. Hence giving a more accurate answers. if you can explain the steps to solve the problem use it.
use this keyword- "lets think step by step and explain why"

## Self consistency
considering multiple perspectives and choosing the consistent answer. many cot is generated and the consitent answer are taken. allowing us to check other reasoning path. It uses sampling and majority voting to generate diverse reasoning path.
1. Generating diverse reasoning paths: The LLM is provided with the same prompt multiple
times. A high temperature setting encourages the model to generate different reasoning
paths and perspectives on the problem.
2. Extract the answer from each generated response.
3. Choose the most common answer

## Tree of Thought(TOT)
It explore multiple reasoning paths simultaneously

## ReAct(reason and act)
The llm first reason about the problem and create and action plan and then carried out the actions in the plan. use in solving complex task. the llm is update by observation. it does this untill the problem is solved.
it combine reasoning and action into one thought loop.

## Automatic Prompt Engineering
prompting a model to generate more prompt

# Code Prompting
* prompt fo translating code
* prompt for explaining code
* prompt of writing code
* prompt for debugging and review code

# Multimodal prompting
This is using mulitple input format to guide the model. such as textx, images, audio, code and other format.

## Best Pracices for Prompt Engineering
* Use one short/ few short prompt- this the model a guide and referene allowing it to product tailor and accurate output.

 * Use verbs that describe the action and actiion ambiguity in your description. prompt should be clear,easy to understand and concise.
 Try using verbs that describe the action. Here’s a set of examples:
Act, Analyze, Categorize, Classify, Contrast, Compare, Create, Describe, Define,
Evaluate, Extract, Find, Generate, Identify, List, Measure, Organize, Parse, Pick,
Predict, Provide, Rank, Recommend, Return, Retrieve, Rewrite, Select, Show, Sort,
Summarize, Translate, Write.
* Be specific about the output- use system and context prompt.
* Prioritize instruction over constraint
* control the max token length
* use variables in prompts
* Experiment with input formats and style( Questions, statement, instructions)
* for few shot prompting for classification task- mix it up the classes in the data.

* stay with model update and always
* Experiment with output format
* for non creative task do ask to give the o/p in json or xml- this limit hallucinations and gives structure

### Cot Best Practice
* set temperature to 0
* logic should be follow by the answer and not answer first
* Document the various prompt.

__Prompt engineering is an iterative process. Craft and test different prompts, analyze,
and document the results. Refine your prompt based on the model’s performance. Keep
experimenting until you achieve the desired output. When you change a model or model
configuration, go back and keep experimenting with the previously used prompts__







