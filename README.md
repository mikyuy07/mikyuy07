import requests
import json

def send_mailtrap_email(payload):
    url = "https://bulk.api.mailtrap.io/api/send"
    headers = {
      "Authorization": "Bearer your_api_token",  # Replace with your Mailtrap API token
      "Content-Type": "application/json"
    }

    response = requests.post(url, headers=headers, data=json.dumps(payload))
    return response.text

payload = {
    "from": {"email": "mailtrap@mailtrapdemo.com", "name": "Mailtrap Test"},
    "to": [{"email": "recipient@example.com"}],  # Add more recipients as needed
    "subject": "You are awesome!",
    "text": "Congrats for sending test email with Mailtrap!",
    "category": "Integration Test"
}

response_text = send_mailtrap_email(payload)
print(response_text)
