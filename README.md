# Talk-To-Gemini

A sleek, single-file web chat interface for Google's **Gemma 3 1B IT** model powered by the Google Generative Language API.  
No installation, no build step — just open the HTML file in a browser and start chatting.

---

## ✨ Features

- **Zero-dependency frontend** — pure HTML, CSS, and JavaScript in one file
- **Gemma 3 1B IT** — Google's compact, instruction-tuned model via the Generative Language API
- **Conversation memory** — full chat history is maintained within the session
- **Markdown rendering** — headings, bold/italic, inline code, fenced code blocks, and lists
- **Typing indicator** — animated dots while the model is generating a reply
- **Suggestion cards** — one-click starter prompts on the welcome screen
- **Local API key** — your key is never sent anywhere except Google's own API
- **Responsive UI** — works on desktop and mobile browsers

---

## 🚀 Quick Start

1. **Get a free API key** from [Google AI Studio](https://aistudio.google.com).
2. **Download or clone** this repository.
3. **Open `Talk.html`** in any modern browser (Chrome, Firefox, Edge, Safari).
4. **Paste your API key** into the input field and click **Launch Chat**.
5. Start typing — press **Enter** to send, **Shift + Enter** for a new line.

> Your API key is stored only in the browser's memory for the duration of the session and is never persisted or shared.

---

## 📁 Project Structure

```
Talk-To-Gemini/
├── Talk.html        # Complete app — UI, styles, and logic in one file
├── requirements.txt # External dependencies & environment requirements
├── LICENSE          # MIT License
└── README.md        # This file
```

---

## 🔧 Requirements

See [`requirements.txt`](requirements.txt) for the full list.  
In short:

| Requirement | Details |
|---|---|
| Web browser | Chrome 90+, Firefox 88+, Edge 90+, Safari 14+ |
| Google AI API key | Free tier available at [aistudio.google.com](https://aistudio.google.com) |
| Internet connection | Required to reach the Generative Language API and load Google Fonts |

---

## 🖥️ How It Works

1. On launch, a setup screen asks for your Google AI Studio API key.
2. The key is stored in a JavaScript variable for the session only.
3. Each message you send is appended to a `chatHistory` array and posted to:
   ```
   https://generativelanguage.googleapis.com/v1beta/models/gemma-3-1b-it:generateContent
   ```
4. The model's reply is parsed, formatted (basic Markdown), and displayed in a chat bubble.
5. The full history is included with every request so the model retains context.

---

## 🎨 UI Overview

| Element | Description |
|---|---|
| **Setup screen** | API key entry with a link to Google AI Studio |
| **Chat screen** | Message bubbles for user (purple) and Gemini (blue) |
| **Suggestion cards** | Pre-written prompts visible on an empty chat |
| **Send button** | Activates when there is text; sends on click or Enter |
| **Clear chat** | Resets the conversation and chat history |
| **Scroll-to-bottom button** | Appears when the user scrolls up |

---

## 🔑 API Details

- **Model:** `gemma-3-1b-it`  
- **Endpoint:** `https://generativelanguage.googleapis.com/v1beta/models/gemma-3-1b-it:generateContent`  
- **Auth:** API key passed as a query parameter (`?key=…`)  
- **Payload format:** Google's `contents` array with `role` / `parts` objects

---

## 🛡️ Privacy & Security

- The API key is held **only in memory** for the current browser session.
- No data is stored on any server other than Google's own API.
- Refreshing or closing the tab clears the key and chat history.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
