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
2. Spell and grammer correction (Reference - https://writingprompts.com/bad-grammar-examples/)
3. Transform one format to another - Convert from HTML to json
4. Tone transformation - convert informal or slang to formal tone

## Expanding
Customer support respnse to review - 
"You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.
Given the customer email delimited by ```, \
Generate a reply to thank the customer for their review.
If the sentiment is positive or neutral, thank them for \
their review.
If the sentiment is negative, apologize and suggest that \
they can reach out to customer service. 
Make sure to use specific details from the review.
Write in a concise and professional tone.
Sign the email as `AI customer agent`.
Customer review: ```{review}```
Review sentiment"

Temperature in chatGPT - At lowest temperature = 0, the model always predicts highest likelihood word. At higher temperature, instead of the highest likelihood next word, also predict slightly lesser likelihood next words. At higher temperature the model is more random and creative.

## chatbots

    def get_completion(prompt, model="gpt-3.5-turbo"):
        messages = [{"role": "user", "content": prompt}]
        response = openai.ChatCompletion.create(
            model=model,
            messages=messages,
            temperature=0, # this is the degree of randomness of the model's output
        )
        return response.choices[0].message["content"]

LLM to be prompted using a json with keys - "role" and "content". 
The role can be either "user", "system", "assistant". 
"system" - Telling the LLM what role to take while replying like an assistant. For e.g. a custom chat assistant can be created by instructing the LLM as - "You are an assistant that speaks like Shakespeare."

For the chatbot, the context needs to be provided to get more accurant and relevant information.
