# alura-google

!pip install google-genai
import os
from google.colab import userdata
os.environ['GOOGLE_API_KEY'] = userdata.get('GOOGLE_API_KEY')
from google import genai
client = genai.Client()
modelo = "gemini-2.0-flash"


from google.genai import types
chat_config = types.GenerateContentConfig(
    system_instruction= "Você é um assistente pessoal e você sempre responde de forma sucinta.",

)

chat = client.chats.create(model=modelo, config=chat_config)
resposta = chat.send_message("O que é inteligencia artificial?")
resposta.text

prompt = input("Esperando prompt")
while prompt != "fim":
  resposta = chat.send_message(prompt)
  print ('Resposta', resposta.text)
  prompt = input("Esperando prompt")
