1. Instruction tuned LLM is built on top of Base LLMs. They are fine tuned on instructions.
## Prompting principles -
1. Clear and specific instructions need to be provided to the model
    1. Using delimiters to indicate distinct parts of the prompt.
    2. Asking for structured output
    3. Ask the model for conditions met. For e.g. check if the prompt contains some instructions and extract them through the model.
    4. Few shot prompting - give some examples with the prompt to get correct answer.
2. Give the model time to think
    1. Specify steps required to complete a task if the task is complex othewise it can give incorrect answer. You can provide how you want the answer to be, in what format, including what all details, etc.
    2. Instruct to workout it's own solution before coming to a conclusion. We can specify to the model that we need it to workout the solution to a problem for e.g. a math problem itself before giving the final answer.
3. Model limitations : Hallucinations - Model can make things up and fabricate facts which can sound very realistic. To reduce hallucination we can ask model to -
    1. Look for relevant information from the text
    2.  Tie the solution to the source documents
  
## Iterative Prompt Development
1. Write a clear prompt
2. Examine why the prompt does not work
3. Refine
4. Repeat

When the text is too long - instruct it to use exact number of words or number of sentences.\
When the text focuses on wrong details - instruct it to focus on intended details\
For the desired format - instruct LLM to format in a table to HTML text, json, etc.

## Summarizing
1. Summarizing the text with character/word/sentence limit.
2. For e.g. a product review summary can focus on - shipment department, pricing details
3. To not include irrelevant details, try the word 'extract'.

## Inferring
Inferring sentiments and topics from the product reviews and newa articles.
1. Identifying list of emotions from a review.
2. Identifying the sentiments from a review or text article.
3. Asking to extract topics in the reviw or article.
4. Combining multiple tasks in one prompt.
5. Zero shot learning - asking the LLM to identify if the text belongs to an existing topic.
6. Alert - We can create an alert if a particular topic is present in the text. For e.g. alert if NASA story is present in the alert.

## Transforming
1. Language translation
2. Spell and grammer correction
3. Transform one format to another - Convert from HTML to json
4. Tone transformation - convert informal or slang to formal tone

