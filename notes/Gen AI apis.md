# ChatGPT
GPT is the most robust api of them all and can give better results. But it is not freely available. A paid subscription is available to use. We can install the 
'openai' package through pip and access it like this - 

    def get_completion(prompt, model="gpt-3.5-turbo"):
      messages = [{"role": "user", "content": prompt}]
      response = client.chat.completions.create(
          model=model,
          messages=messages,
          temperature=0
      )
      return response.choices[0].message.content

# Bard
Bard is an LLM by google. Though it is no longer freely available, it's keys could be hacked for a while through browser inspect option.
A simple chatbot could be built by accessing the bard api through the python package 'bard'.

    session = requests.Session()
    session.headers = SESSION_HEADERS
    token = <"The key">
    
    session.cookies.set("__Secure-1PSID", token)
    session.cookies.set("__Secure-1PSIDTS", "<VALUE>")
    session.cookies.set("__Secure-1PSIDCC", "<VALUE>")
    
    bard = Bard(token=token, session=session)
    input_text = "How much time does it take to go to New Delhi from Beijing?"
    print(bard.get_answer(input_text)['content'])

It is no longer needed to hack the key, since the Palm api is available freely for development purposes.

# PaLM
PaLM2 is now freely available to use by Google. It can be used for multiple tasks like sentiment analysis, seq to seq translation, code explantion, etc.
It can be accessed through the makersuite or AI studio by Google. 
google-generativeapi package can be installed in python and the palm api can be accessed as - 

    import google.generativeai as palm
    
    completion = palm.generate_text(
      model=model,
      prompt=prompt,
      temperature=0,
      # The maximum length of the response
      max_output_tokens=500,
      )
Bard now used PaLM2 at it's backened. 
