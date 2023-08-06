- 👋 Hi, I’m @talhajubaye
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
talhajubaye/talhajubaye is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/webhook', methods=['POST'])
def webhook():
    data = request.get_json()
    user_message = data['message']
    response = get_chatbot_response(user_message)
    return jsonify({'response': response})

def get_chatbot_response(user_message):
    # Your chatbot logic goes here
    if 'hello' in user_message.lower():
        return "Hello! Welcome to Pathao customer service. How can I assist you today?"
    elif 'help' in user_message.lower():
        return "Sure, I'm here to help! Please let me know what you need assistance with."
    elif 'order' in user_message.lower():
        return "To place an order, please visit our website or mobile app."
    elif 'complaint' in user_message.lower():
        return "I'm sorry to hear that you have a complaint. Please share the details, and we will look into it."
    else:
        return "I'm sorry, but I couldn't understand your request. Please try again with different wording."

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

