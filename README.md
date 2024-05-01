# GPT_Assistant
ABSTRACT: Using OpenAI to make a chatbot assistant

Source: https://www.oreilly.com/library/view/developing-apps-with/9781098152475/

1. Give the chatbot a prompt role (give the chatbot an idea of what you want it to do)
```
# Example prompt
prompt_role = '''You are an assistant for journalists.
Your task is to write articles, based on the FACTS that are given to you.
You should respect the instructions: the TONE, the LENGTH, and the STYLE'''
```
2. Specify the format of the prompt you want to use
```
prompt = f'{prompt_role}\nFACTS: {facts}\nTONE: {tone}\nLENGTH: {length_words} words\nSTYLE: {style}'
return ask_chatgpt([{"role": "user", "content": prompt}])
```
3. Retreive the response from the OpenAI model
```
response = client.chat.completions.create(model="gpt-3.5-turbo", messages=messages)
return (response.choices[0].message.content)
```
- - - - -
Example:

Prompt: ['Guinea pigs are the preferred pet', 'Guinea pigs are more popular than dogs!'], 'news flash', 50, 'excited')
- Telling the chatbot:
  1. Facts: ['Guinea pigs are the preferred pet', 'Guinea pigs are more popular than dogs!']
  2. Tone: 'news flash'
  3. Length response should be: 50 (characters)
  4. Style of response: 'excited'

Response: 
'**News Flash: Guinea Pigs Surpass Dogs as Preferred Pets!**
In a surprising turn of events, guinea pigs have overtaken dogs as the most popular pet choice. With their adorable squeaks and playful nature, guinea pigs are winning the hearts of pet owners everywhere. Could this be the rise of the guinea pig era? Stay tuned for more updates!'
