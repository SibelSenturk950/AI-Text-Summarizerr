
import os
from dotenv import load_dotenv

load_dotenv()
api_key = os.getenv("OPENAI_API_KEY")

def summarize_text(text):
    try:

        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "Metni özetleyin."},
                {"role": "user", "content": f"Şu metni özetle: {text}"}
            ],
            max_tokens=100,
            temperature=0.5
        )
        return response.choices[0].message.content.strip()
    except Exception as e:
        return f"⚠️ Hata oluştu: {e}"



text_to_summarize = input("Özetlemek istediğiniz metni girin: ")


summary = summarize_text(text_to_summarize)
print("📌 Özet:", summary)# AI-Text-Summarizerr
