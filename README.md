# LearnMate — AI Based Learning Companion!

LearnMate is an AI-powered conversational assistant built with **Python, Flask, and Google Gemini**. It is designed to provide natural, helpful conversations while helping users understand and learn about a wide range of topics, including programming, technology, data science, artificial intelligence, and general concepts.

The application maintains conversation history so users can have meaningful multi-turn conversations instead of receiving isolated responses.

## Features

* 🤖 AI-powered conversations using Google Gemini
* 💬 Natural and conversational responses
* 🧠 Multi-turn conversation memory
* 🔄 Separate conversation history using conversation IDs
* 📚 Learning assistance across different topics
* 💻 Support for programming and technical questions
* 🪟 Context-window management using message truncation
* 🛡️ Basic API error handling
* 🔐 API key stored securely using environment variables
* 🎨 Responsive web-based chat interface
* 📋 Markdown and syntax-highlighted code responses
* 📎 Copy buttons for AI responses and code blocks
* 🆕 New chat functionality
* 📱 Mobile-friendly interface

## Technology Stack

* **Python**
* **Flask**
* **Google Gemini API**
* **Google GenAI Python SDK**
* **HTML5**
* **CSS3**
* **JavaScript**
* **Marked.js**
* **DOMPurify**
* **Highlight.js**
* **python-dotenv**

## How It Works

The application follows a simple conversational architecture:

```text
User
  ↓
LearnMate Web Interface
  ↓
Flask Backend
  ↓
Conversation History
  ↓
Context Window Management
  ↓
Google Gemini API
  ↓
AI Response
  ↓
LearnMate Interface
```

Each conversation receives a unique `conversation_id`. The backend stores the conversation history associated with that ID and sends the relevant recent messages to Gemini with every request.

## Conversation Memory

LearnMate maintains conversation history separately for each conversation.

For example:

```text
User: My name is Alex.
AI: Nice to meet you, Alex!

User: What should I learn first?
AI: ...

User: What is my name?
AI: Your name is Alex.
```

The application uses the most recent messages when communicating with Gemini.

### Context Window Management

To prevent unlimited conversation history from being sent to the model, LearnMate keeps only a fixed number of recent messages.

The current implementation uses:

```python
MAX_MESSAGES = 30
```

This provides a simple truncation-based context management strategy while allowing the assistant to maintain recent conversational context.

## System Prompt

LearnMate uses a custom system prompt to define the assistant's:

* Identity
* Conversation style
* Learning behavior
* Memory behavior
* Response style
* Technical assistance behavior
* Accuracy requirements

This ensures the application behaves as a defined AI assistant rather than relying only on the model's default behavior.

## Error Handling

The application includes basic error handling for situations such as:

* Missing API keys
* Invalid requests
* Empty user messages
* Gemini API failures
* Rate-limit errors
* Empty model responses
* Server/API connection problems

The frontend displays a clear message to the user when the AI service cannot process a request.

## Project Structure

```text
LearnMate/
│
├── app.py
│
├── templates/
│   └── index.html
│
├── .env
├── .gitignore
├── requirements.txt
└── README.md
```

## Installation

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd LearnMate
```

### 2. Create a virtual environment

Windows:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Gemini API key

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

**Never commit the `.env` file or expose your API key publicly.**

### 5. Run the application

```bash
python app.py
```

The application will run locally at:

```text
http://127.0.0.1:5000
```

Open the address in your browser to use LearnMate.

## API Endpoint

The chatbot uses a POST endpoint:

```text
POST /chat
```

Example request:

```json
{
    "conversation_id": "unique-conversation-id",
    "message": "Explain Python functions simply."
}
```

Example response:

```json
{
    "conversation_id": "unique-conversation-id",
    "response": "A function in Python is..."
}
```

## Security

The Gemini API key is loaded from an environment variable using `python-dotenv`.

The API key should never be hardcoded in `app.py` or committed to GitHub.

The `.env` file should be included in `.gitignore`.

For sharing the project, use a `.env.example` file containing only:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

## Future Improvements

Possible future improvements include:

* Persistent conversation storage
* User authentication
* Database integration
* Streaming AI responses
* Voice interaction
* File and document understanding
* Web search and real-time information
* Additional AI model providers
* Improved safety and guardrails
* Cloud deployment

## Project Status

**Completed — LLM API Integration**

LearnMate currently demonstrates:

* Real LLM API integration
* Multi-turn conversation
* Conversation-specific history
* Context-window management
* Custom system prompting
* API error handling
* Secure environment-variable configuration
* Functional web interface

## Author

**Lokeshkumar S**

B.Sc. Artificial Intelligence & Data Science

---

Built as part of a Generative AI internship project.
