# 30 Days of Voice Agents Challenge

Welcome to the repository for my 30 Days of Voice Agents Challenge\! This project documents the journey of building a sophisticated, voice-activated conversational AI from the ground up. Over the course of this challenge, a simple web page evolves into a fully interactive voice agent capable of holding context-aware conversations.

-----

## 🤖 About The Project

This project is a hands-on guide to building a voice-based conversational AI using modern web technologies and powerful AI APIs. You can engage in a continuous, voice-to-voice conversation with an AI powered by Google's Gemini LLM. The agent remembers the context of your conversation, allowing for natural follow-up questions and a more human-like interaction.

The repository is structured by day, with each folder representing a significant step in the development process, from setting up the server to implementing a full conversational loop with memory.

### Key Features

### Core Functionality
- **🎙️ Real-time Speech Recognition**: Live audio streaming with AssemblyAI Universal Streaming
- **🧠 Multi-Persona AI Conversations**: Choose from Developer, Sosuke Aizen, Monkey D. Luffy, or Politician personas powered by Google Gemini
- **🔊 Streaming Text-to-Speech**: High-quality voice synthesis with real-time audio streaming using Murf AI
- **🔍 Intelligent Web Search**: Real-time web search using Tavily API with contextual integration
- **💾 Persistent Session Management**: MongoDB-powered conversation history with session switching
- **⚡ WebSocket Real-time Processing**: Instant audio processing and response generation

### Advanced AI Capabilities
- **🎭 Dynamic Persona Switching**: Real-time persona changes during conversations
- **🔄 Context-Aware Conversations**: Maintains conversation context across sessions
- **🧠 Intelligent Duplicate Detection**: Prevents processing of repeated audio inputs
- **⚡ Concurrent Processing Management**: Handles multiple simultaneous requests efficiently
- **🔄 Auto-retry Logic**: Robust error recovery and connection management
- **📊 Live Processing Status**: Real-time feedback on audio processing and AI generation

### Modern Interface Features
- **🎨 Contemporary UI**: Modern card-based interface with gradient backgrounds and animations
- **👤 Persona Selection**: Interactive persona switcher with visual indicators
- **💬 Dual Chat Interfaces**: Both modern streaming chat and legacy conversation history
- **📱 Responsive Design**: Mobile-optimized interface that works across all devices
- **🔄 Session Management**: Create new chats, switch between sessions, view conversation history
- **⚙️ Settings Modal**: User-friendly API key configuration with validation

### Technical Excellence
- **🔊 Audio Chunk Processing**: Real-time audio chunk handling with base64 encoding
- **🎵 Streaming Audio Playback**: Real-time audio chunk processing and playback
- **💾 Automatic Audio Cleanup**: Smart temporary file management and cleanup
- **🔐 Secure API Key Management**: In-browser storage with validation
- **📊 Comprehensive Logging**: Detailed logging with configurable levels
- **🛡️ Comprehensive Error Handling**: Graceful fallbacks for service failures
- **🔄 Fallback TTS Mechanisms**: Multiple TTS strategies for reliability
- **⚡ Performance Optimization**: Efficient WebSocket connection reuse and context management

-----

## 🛠️ Tech Stack

The application is built using a combination of Python for the backend, vanilla JavaScript for the frontend, and a suite of powerful AI APIs for the core functionalities.

  * **Backend**:
      * **FastAPI**: For building the high-performance, asynchronous API server.
      * **Uvicorn**: As the ASGI server to run the FastAPI application.
      * **Python-Dotenv**: To manage environment variables securely.
  * **Frontend**:
      * **HTML, CSS, JavaScript**: For the structure, styling, and client-side logic.
      * **Bootstrap**: For creating a responsive and modern user interface.
      * **MediaRecorder API**: To capture audio directly from the user's microphone in the browser.
  * **AI & Voice APIs**:
      * **Murf AI**: For generating high-quality, natural-sounding Text-to-Speech (TTS).
      * **AssemblyAI**: For providing fast and accurate Speech-to-Text (STT) transcription.
      * **Google Gemini**: As the Large Language Model (LLM) for generating intelligent and coherent responses.

-----

## ⚙️ Architecture

The application follows a client-server architecture. The frontend, running in the user's browser, is responsible for capturing audio and managing the user interface. The FastAPI backend acts as the orchestrator, managing the complex interactions between the various AI services.

Here is the flow for a single turn in a conversation:

1.  The **Client** captures the user's voice using the MediaRecorder API and sends the audio data to the backend.
2.  The **FastAPI Server** receives the audio file.
3.  It first sends the audio to **AssemblyAI** to be transcribed into text (STT).
4.  The server retrieves the chat history for the current session and appends the new transcript. This entire context is then sent to the **Google Gemini LLM**.
5.  Gemini processes the conversation and generates a text response, which is sent back to the server.
6.  The server adds the LLM's response to the chat history and forwards the text to **Murf AI** for speech synthesis (TTS).
7.  The server receives the final audio URL from Murf AI and sends it back to the client.
8.  The **Client** automatically plays the received audio, and the UI updates to indicate it's ready for the user's next turn.

-----

## 🚀 Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

  * Python 3.8+
  * API keys for:
      * Murf AI
      * AssemblyAI
      * Google Gemini

### Installation & Running the App

1.  **Clone the repository**
    ```sh
    git clone https://github.com/AdityaSChauhan1/murf.git
    ```
2.  **Navigate to a specific day's project directory** (e.g., `day-13` for the latest version).
    ```sh
    cd 30-days-of-voice-agents/day-13/
    ```
3.  **Install the required dependencies** from the `requirements.txt` file.
    ```sh
    pip install -r requirements.txt
    ```
4.  **Create a `.env` file** in the chosen day's directory. Copy the contents of `.env.example` (if available) or create it from scratch.
    ```
    MURF_API_KEY="your_murf_api_key_here"
    ASSEMBLYAI_API_KEY="your_assemblyai_api_key_here"
    GEMINI_API_KEY="your_gemini_api_key_here"
    ```
5.  **Run the FastAPI server** with hot-reloading.
    ```sh
    uvicorn main:app --reload
    ```
6.  **Open your browser** and navigate to `http://localhost:8000`. Grant microphone permissions when prompted and start conversing\!

-----

## 🗓️ Project Journey: Day 1 to 13

Here is a summary of the progress made during the first 13 days of the challenge.

  * **Day 01**: Laid the foundation with a basic **FastAPI server** and a simple **Bootstrap UI**.
  * **Day 02**: Integrated the **Murf AI API** to create the first endpoint for Text-to-Speech (TTS).
  * **Day 03**: Built the **frontend interface** to interact with the TTS endpoint, allowing users to type text and hear it spoken.
  * **Day 04**: Developed a client-side **Echo Bot** using the `MediaRecorder` API to record and play back user audio.
  * **Day 05**: Enhanced the echo bot by implementing **server-side audio upload**, moving from client-only to a client-server model.
  * **Day 06**: Integrated the **AssemblyAI API** for Speech-to-Text (STT), allowing the server to transcribe user audio.
  * **Day 07**: Created a **voice transformation bot** by chaining the STT and TTS services. The app would listen, transcribe, and speak the user's words back in a different voice.
  * **Day 08**: Introduced intelligence by integrating the **Google Gemini LLM**, creating an endpoint that could generate text-based responses to queries.
  * **Day 09**: Achieved a full **voice-to-voice conversational loop**. The app could now listen to a spoken question and provide a spoken answer generated by the LLM.
  * **Day 10**: Implemented **chat history** and session management, giving the agent a "memory" to hold context-aware conversations.
  * **Day 11**: Made the application more robust by adding **server-side and client-side error handling**, including a friendly fallback audio message for API failures.
  * **Day 12**: Performed a major **UI revamp**, simplifying the interface to a single, animated record button and a cleaner, more modern aesthetic.
  * **Day 13**: Focused on **documentation**, creating this comprehensive `README.md` file to explain the project's architecture, features, and setup.
  * **Day 14**: Code refactor → services + schemas.
  * **Day 15**: Added agent persona.
  * **Day 16**: Real-time STT streaming.
  * **Day 17**: Streaming LLM replies.
  * **Day 18**: Streaming TTS (faster playback).
  * **Day 19**: Switched to WebSockets for live comms.
  * **Day 20**: Turn detection in STT.
  * **Day 21**: Integrated SerpAPI for live Google Search.
  * **Day 22**: Function calling in Gemini → decides when to search.
  * **Day 23**: UI shows real-time transcription + agent’s "thinking".
  * **Day 24**: Loading animations + better feedback.
  * **Day 25**: Welcome message on startup.
  * **Day 26**: Agent gets a name → MURF Ai.
  * **Day 27**: Settings panel for API key input in UI.
  * **Day 28**: Cloud deployment on Render.
  * **Day 29**: Polished README + architecture docs.Day 30: 🎉 Final version of a fully featured Voice AI Assistant.
  * **Day 30**: 🎉 Final version of a fully featured Voice AI Assistant.
