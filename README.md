# what_is_next_for_llms
This repo serves as a space for posting on future trends that we are exploring.

# Introduction
LLMs have evolved during the last 6 years from being a simple language model to predict words that are from the same semantic group and tag documents and search results (as it is the case for Google using BERT back in the day to provide suggestions for the next word in the search bar); to become the substrate for the future of intelligence, and potentially the base for Artificial General Intelligences (AGI).

The last months have shown a great improvement of LLMs, making them capable of reasoning, coding, writing reports, summarizing, performing information retrieval and enrichment, generating well formatted data... to name a few.

Even though the pace of improvement is increasing everyday, there have been many well founded opinions on how LLMs are not enough to bring us to AGI. This space serves to as a medium to provide ideas that we are testing and that we find will serve as a substrate for further improvement of the LLM ecosystem.

# Using old NLPs is demonized. More smaller models collaborating.
Natural Language Processing has been around since the inception of the computer; serving as a way to catalog news, archive documents based on the topic, serve as a layer to organize email boxes to remove spam... If one studies classic NLP works, they will find that with much less computer power than nowadays, there are multiple works that would make our jaws to drop, based on the results that were obtained with basic NLP. Prior to the appearance of BERT, there was NLP, a lot of NLP; then BERT came and simplified the NLP process, and multiple BERT models were trained to perform the different tasks that were done before with specialized computer programs.

It feels like the AI community is heading towards putting on a pedestal the usage of a single model to rule them all, the creation of an AGI as a compact model that serves for any purpose; in the last days, it has seem that the way to create AGI is on the contrary (and as in many other research areas) based on creating small models that can perform specific tasks, and other bigger models that serve as the operating system or the orchestrators to move the requests to the different models.

Classic language models did Intent Prediction (based on utterances: a group of sentences that determined the possible ways for the user to ask for something): by comparing the user request to other reference requests, and based on the similarity on those requests, the user was routed one answer or another, one prompt to complete or another. We hypothesize that potentially there is some intent prediction made in code in some of the most famous LLMs today: Bing Chat or GPT-4.

The Web UI in Bing Chat, once you make a question, it will sometimes try to rephrase what you wrote differently to perform an internal search, that rephrasing process may be behind the potential improvement in LLM systems, by creating a router LLM that would send the request to the LLM that is more likely to be capable of answering the question.

This window opens up for many possibilities to be explored, if we accept the possibility of using intent detection, and not leave that task to the LLM (it actually happens in the LLM by default, in the different multi-head attention layers), somehow training a huge model on every possible task is prone to fail us to get into the AGI era.

More evidence on this being something remarkable to review is the fact that GPT-4 is reportedly from the leaks of its architecture using an MoE approach (Mixture of Experts): in which separate groups of MLP layers in the output layer are trained on different tasks. It is yet to be seen if MoEs bring us closer to AGI, or not; somehow, it seems clear that separation of duties of each expert in the later layers of the transformer model, specialized on different tasks, rather than being generic.

What could be done in addition to just using intent prediction and routing requests to different models, would be to remove responsabilities from the LLM and move them to code that orchestrates the responses from the different models; a possibility that may arise is the usage of multiple models in tandem, in order to generate the final answer: as an example, we could think of the following steps in the generation, given a question about mathematics to be explained in simple terms:
1. An intent detection model that can discriminate between different needs for expert models: e.g.: biology, maths, physics, chemistry, story teller, coding... detects that the user wants to solve a mathematical problem (INTENT CLASSIFY).
2. The main model routes the model to the mathematical expert model (again this routing is done in code, not as in the MoE proposal in which the weights of the layers determine which experts from the last MLP layers are activated).
3. The mathematical expert model generates a response.
4. The code of the LLM system asks the main model to detect other utterances or intents, it finds that the user wants the explanation of the solution to be provided in simple terms. The response is sent to a rephraser model that can explain things in simple terms with the output generated by the prior mathematical expert, and performs a rephrase to simplify the given context.
5. The response by the ELI5 (Explain like im 5 model) is returned back.
6. The whole answer generated by the models in tandem is returned to the user.

# Multi-stage LLM systems. Not agents.
Another possibility to consider is the usage of a multi-stage LLM system; this case differs from the previous case, in which multiple stages were performed by different LLMs. In this case there is no need to have multiple LLMs, we could have a single LLM to perform all the tasks, somehow, we may need to perform multiple stages to achieve certain objectives: like deploying guardrails for the model in production client applications. Without the intent to make the models censored for certain prompts, in which they do not provide answers, this use case would be more focused on providing the needed requirements to create an LLM based application, in which the developer wants the users to use the LLM in a certain manner, to get answers for a certain kinds of use cases but no others. We could think about this as an intelligent chatbot to be used as an aid for customer or IT support; which we want it to answer for the products maintained, and not for other use cases like for example chemistry questions.

# Expert Systems to aid in Logic and Reasoning
It seems clear that LLMs is not all we need; it seems cumbersome to rely on the LLM to provide correct factional answers on events that happen in the news; as it may require the retraining of the model continuosuly, something that seems not viable if we consider how Deep Learning works. Even the continuous training of the models would lead to bringing the performance of the model down, as it needs to learn the new facts to keep it updated; then it is likely that other well performing tasks for the model would be affected by the process of next token prediction.

For this kind of problems, RAG (Retrieval Augmented Generation) seems like the best solution: get related context from a vectorized DB, incorporate that context into the prompt, and ask the LLM to perform an answer. RAG has become such an standard lately. Somehow, we are missing on the capabilities for the model to perform logic and reasoning.
