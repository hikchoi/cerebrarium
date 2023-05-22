
- LLM
  - large language model

- multi-modal
  - this means that LLMs go beyond utilizing text and language.
  - understanding images, audio.
  - works by using multiple encoders that create vector representation of given image, text respectively.
  - given some text representation of a concept, and a similar concept in image, the two respective encoders will map them to similar vectors, essentially allowing it to "speak the same language in the vector space"
  - once input in any modality is processed with the encoder, all we are left with vectors of certain dimension (probably something a human cannot understand intuitively), and now we are able to search in any direction, from any modality to any modality.

- contrastive pretraining
  - two independantly trained models cannot map similar context to close vectors. When they are trained, respective models have to be aware of the other modes.
    - i.e. text and image encoders share indirect understanding of each other
  - this works by having a pair of two representations in different modality, and learning to encode the pair as close as possible.
  - we also need negative pairs to "contrast" this learning.
  - given two positive pairs, we can switch the items in the pair to directly compose two negative pairs.

- transformer
  - LSTMs were great but long ranged tasks like natural language was hard for them.
  - transformers, basically a set of encoder and decoder, has self-attention to tackle this issue

- transfer learning
  - train a model to do a relatively easy task, and use that to do harder stuff

- prompts
  - LLMs are trained with a simple idea of taking a sequence of text and output a sequence of text.
  - leveraging "good prompts" allows advanced usage of LLMs.
  - consists of `instructions`, `external information (context)`, `user input (query)`, `output indicator`

- langchain
  - provides various components that can be chained together to support advanced use cases with LLM
  - modules provided:
    - PromptTemplates
    - LLMs
    - Agents
    - Memory

- prompt templates
  - it's unlikely that we will hardcode instructiosn, context, and queries in a prompt
  - we will usually feed them dynamically, and prompt templates help us with that.
  - could be argued that we can just use f-strings for this, but the point here is to formalize the process of prompting.

- few-shot learning
  - give a model a prompt that includes "a few examples" of what it should do

- memory
  - by default llms are stateless, so it can't remember past conversations.
  - conversation chains allows us to keep a history of the conversation so that it could be used to infer context
  - conversational buffer memory
    - simply keep track of all the information fully
    - could slow calls down and easily hit token limit
  - conversational summary memory
    - summarizes each interaction and store that summarization
    - take additional calls to summarize, summarization may be even longer than full text if text is short
  - conversational buffer window memory
    - keep buffer, but for a short window
    - tackles token problem
  - and so on...

- retrieval augmentation
  - LLMs are frozen in time; unless they are trained with new data every time we need them to be aware of it, they will sit at a certain point in the past when they were trained (parametric knowledge).
  - instead of training again and again with new data, we instead give the external knowledge (source knowledge) to the LLM, and ask them to retrieve them.

- agents
  - enabling "tools" for LLMs. Since LLMs are stuck with their trained data in the past, and struggle with some rather simple tasks that simple programs can solve easily, we instead let the LLM use "tools" to solve them, instead of trying to infer the answers themselves.

  - zero-shot ReAct
    - no memory, consider one single interaction.
  - conversational ReAct
    - same as zero-shot, but with conversational memory.
  - ReAct docstore
    - same, but actively looks for information (lookup, search)
  - self-ask with search
    - has ability to search the web, and asks follow-up questions

- tools
  - objects that consume input and produces outputs.
  - generally input from LLM, and output to LLM
  - used by agents
  - can create custom tools that can be used by agents depending on the prompt and query as necessary