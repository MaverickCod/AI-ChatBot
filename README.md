
# AI Chatbot

This project is an AI-powered chatbot interface that interacts with users in real-time. The bot leverages Google's Gemini API to generate responses based on user input. Users can input text, upload files, and include emojis in their messages.

## Checkout the website
    
  [AI ChatBot](https://ai-chat-bot-chi.vercel.app/)

## Features

- **User Messages**: Users can send text messages and files (images) to the chatbot.
- **Bot Responses**: The chatbot generates responses using the Gemini API.
- **File Attachments**: Users can attach files to their messages, and the chatbot can display them.
- **Emoji Support**: Emoji support is provided using the EmojiMart library.
- **Responsive Design**: The chatbot interface is designed to be responsive and visually appealing.

## Project Structure

- `index.html`: The main HTML structure of the chatbot.
- `script.js`: JavaScript code for chatbot interactions and API calls.
- `styles.css`: Styling for the chatbot interface.
- `favicon.ico`: Icon displayed on the browser tab.

## Setup Instructions

1. **Clone the Repository**:
    ```bash
    git clone <https://github.com/MaverickCod/AI-ChatBot>
    ```

2. **Navigate to Project Directory**:
    ```bash
    cd ai-chatbot
    ```

3. **Open index.html in Browser**:
   Double-click on `index.html` to view the chatbot in your default browser.

## Code Overview

### JavaScript (script.js)

- **Event Listeners**:
    - Listens for user message submissions, file uploads, and emoji selections.
    - Updates the chatbot interface in real-time based on user interactions.

- **Functionality**:
    - `generateBotResponse`: Sends a request to the Gemini API to generate bot responses.
    - `handleOutgoingMessage`: Handles the sending of messages from users.
    - `createMessageElement`: Creates HTML elements dynamically for user and bot messages.

- **API Integration**:
    - The bot uses the Gemini API (`https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash-latest:generateContent`) to generate responses.
    - Make sure to replace the `API_KEY` with your own key in the `script.js` file.

### HTML (index.html)

- Contains the chatbot structure, including a header, chat window, and input form.
- Uses Material Icons for a modern UI.

## Dependencies

- **EmojiMart**: Used for emoji picker functionality.
- **Google Fonts**: Used for icons in the chatbot interface.

## Sample Code

### JavaScript Code Snippet

```javascript
const generateBotResponse = async(incomingMessageDiv) => {
    const messageElement = incomingMessageDiv.querySelector(".message-text");
    
    // Add user message to chat history
    chatHistory.push({
        role: "user",
        parts:[{ text: userData.message }, ...(userData.file.data ? [{ inline_data: userData.file }] : [])]
    });

    try {
        // Fetch bot response from API
        const response = await fetch(API_URL, requestOptions);
        const data = await response.json();
        const apiResponse = data.candidates[0].content.parts[0].text;
        messageElement.innerText = apiResponse;
    } catch (err) {
        console.log(err);
        messageElement.innerText = "Error generating response";
    }
};
```

## Note

Replace the `API_KEY` in `script.js` with a valid Google API Key.

## License

This project is open-source under the MIT license.
