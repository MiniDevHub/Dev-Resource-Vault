<div align="center">

# 🌐 AI APIs - Complete Guide

![AI APIs](https://img.shields.io/badge/AI-APIs-blue?style=for-the-badge&logo=openai)
![Integration](https://img.shields.io/badge/Easy-Integration-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-orange?style=for-the-badge)

### _Integrate powerful AI into your applications_ 🚀

**From text generation to image creation - AI at your fingertips** ✨

</div>

---

## 📚 Table of Contents

- [🎯 What Are AI APIs?](#-what-are-ai-apis)
- [🤖 OpenAI API](#-openai-api)
- [🧠 Anthropic Claude API](#-anthropic-claude-api)
- [🔮 Google AI APIs](#-google-ai-apis)
- [🤗 Hugging Face](#-hugging-face)
- [🎨 Image Generation APIs](#-image-generation-apis)
- [🗣️ Speech & Audio APIs](#️-speech--audio-apis)
- [☁️ Cloud AI Services](#️-cloud-ai-services)
- [📊 Comparison Guide](#-comparison-guide)
- [💡 Best Practices](#-best-practices)
- [🔒 Security & Cost Management](#-security--cost-management)
- [🚀 Real-World Applications](#-real-world-applications)

---

<div align="center">

## 🎯 What Are AI APIs?

</div>

### Understanding AI APIs 📖

```bash
# ═══════════════════════════════════════════
# AI API OVERVIEW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHAT ARE AI APIs?                        ║
╚════════════════════════════════════════════════════════════╝

AI APIs: Web services that provide access to AI models
─────────────────────────────────────────────────────────────
• Pre-trained AI models via HTTP
• Pay-per-use pricing
• No infrastructure management
• Scalable on demand
• Easy integration

Types of AI APIs:
─────────────────────────────────────────────────────────────

┌─────────────────────────────────────────────────────────┐
│  1. TEXT & LANGUAGE                                     │
│     • Text generation (GPT-4, Claude)                  │
│     • Translation                                       │
│     • Summarization                                     │
│     • Sentiment analysis                               │
│     • Text classification                              │
│                                                         │
│  2. VISION & IMAGE                                      │
│     • Image generation (DALL-E, Midjourney)           │
│     • Image recognition                                 │
│     • Object detection                                  │
│     • OCR                                              │
│     • Image editing                                     │
│                                                         │
│  3. AUDIO & SPEECH                                      │
│     • Speech-to-text (Whisper)                        │
│     • Text-to-speech                                   │
│     • Audio generation                                 │
│     • Music creation                                   │
│                                                         │
│  4. EMBEDDINGS & SEARCH                                 │
│     • Vector embeddings                                │
│     • Semantic search                                  │
│     • Recommendation systems                           │
│                                                         │
│  5. MULTIMODAL                                          │
│     • Vision + Language (GPT-4V, Gemini)             │
│     • Audio + Text                                     │
│     • Video understanding                              │
└─────────────────────────────────────────────────────────┘

╔════════════════════════════════════════════════════════════╗
║                   WHY USE AI APIs?                         ║
╚════════════════════════════════════════════════════════════╝

Benefits:
─────────────────────────────────────────────────────────────
✅ No ML expertise required
✅ No infrastructure management
✅ Quick integration (hours, not months)
✅ Scalable automatically
✅ Pay only for what you use
✅ Access to state-of-the-art models
✅ Regular improvements & updates
✅ Well-documented
✅ Multiple SDKs available
✅ Production-ready

Challenges:
─────────────────────────────────────────────────────────────
⚠️ Costs can add up
⚠️ Rate limits
⚠️ Internet dependency
⚠️ Data privacy concerns
⚠️ Vendor lock-in
⚠️ Limited customization
⚠️ Latency (API calls)

╔════════════════════════════════════════════════════════════╗
║                   TYPICAL USE CASES                        ║
╚════════════════════════════════════════════════════════════╝

1. Chatbots & Virtual Assistants
2. Content Generation
3. Code Generation
4. Image Creation & Editing
5. Speech Recognition
6. Language Translation
7. Sentiment Analysis
8. Document Processing
9. Recommendation Systems
10. Search & Discovery

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🤖 OpenAI API

</div>

### The Most Popular AI API 🌟

```python
# ═══════════════════════════════════════════
# OPENAI API
# ═══════════════════════════════════════════

"""
OpenAI API: Access to GPT-4, GPT-3.5, DALL-E, Whisper, and more
- Industry-leading language models
- Image generation
- Speech-to-text
- Embeddings
"""

print("="*60)
print("OPENAI API")
print("="*60)

# ═══════════════════════════════════════════
# SETUP & AUTHENTICATION
# ═══════════════════════════════════════════

# Installation
# pip install openai

import openai
import os
from openai import OpenAI

# Initialize client
client = OpenAI(api_key=os.environ.get("OPENAI_API_KEY"))

# Or set globally
# openai.api_key = "your-api-key-here"

print("✅ OpenAI client initialized")

# ═══════════════════════════════════════════
# GPT-4 & GPT-3.5 (CHAT COMPLETION)
# ═══════════════════════════════════════════

"""
╔════════════════════════════════════════════════════════════╗
║                   CHAT COMPLETION API                      ║
╚════════════════════════════════════════════════════════════╝

Models:
─────────────────────────────────────────────────────────────
• gpt-4                    Most capable, expensive
• gpt-4-turbo             Faster, cheaper GPT-4
• gpt-3.5-turbo           Fast, affordable
• gpt-3.5-turbo-16k       Larger context window

Pricing (as of 2024):
─────────────────────────────────────────────────────────────
GPT-4:         $0.03/1K input, $0.06/1K output tokens
GPT-4 Turbo:   $0.01/1K input, $0.03/1K output tokens
GPT-3.5:       $0.0005/1K input, $0.0015/1K output tokens
"""

# Basic chat completion
def simple_chat(prompt: str) -> str:
    """
    Simple chat completion.
    """
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {"role": "user", "content": prompt}
        ]
    )
    return response.choices[0].message.content

# Example usage
result = simple_chat("Explain quantum computing in simple terms")
print("\nSimple Chat Response:")
print(result)

# ─────────────────────────────────────────────
# ADVANCED CHAT WITH SYSTEM PROMPT
# ─────────────────────────────────────────────

def chat_with_context(
    system_prompt: str,
    user_message: str,
    temperature: float = 0.7,
    max_tokens: int = 500
) -> dict:
    """
    Chat with system context and customization.
    """
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": user_message}
        ],
        temperature=temperature,  # 0-2, higher = more creative
        max_tokens=max_tokens,
        top_p=1.0,
        frequency_penalty=0.0,
        presence_penalty=0.0
    )

    return {
        'content': response.choices[0].message.content,
        'tokens': response.usage.total_tokens,
        'cost': calculate_cost(response.usage, "gpt-3.5-turbo")
    }

def calculate_cost(usage, model):
    """Calculate approximate cost."""
    if model == "gpt-3.5-turbo":
        input_cost = usage.prompt_tokens * 0.0005 / 1000
        output_cost = usage.completion_tokens * 0.0015 / 1000
    elif model == "gpt-4":
        input_cost = usage.prompt_tokens * 0.03 / 1000
        output_cost = usage.completion_tokens * 0.06 / 1000
    return input_cost + output_cost

# Example: Customer service bot
system = "You are a helpful customer service assistant. Be friendly and concise."
user = "I received a damaged product. What should I do?"
response = chat_with_context(system, user)

print("\nCustomer Service Bot:")
print(f"Response: {response['content']}")
print(f"Tokens used: {response['tokens']}")
print(f"Cost: ${response['cost']:.6f}")

# ─────────────────────────────────────────────
# CONVERSATION WITH HISTORY
# ─────────────────────────────────────────────

class ChatBot:
    """
    Chatbot that maintains conversation history.
    """
    def __init__(self, system_prompt: str = "You are a helpful assistant."):
        self.messages = [{"role": "system", "content": system_prompt}]
        self.client = OpenAI()

    def chat(self, user_message: str) -> str:
        """Send message and get response."""
        # Add user message
        self.messages.append({"role": "user", "content": user_message})

        # Get response
        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=self.messages
        )

        # Add assistant response
        assistant_message = response.choices[0].message.content
        self.messages.append({"role": "assistant", "content": assistant_message})

        return assistant_message

    def reset(self):
        """Clear conversation history."""
        self.messages = self.messages[:1]  # Keep system prompt

# Example usage
bot = ChatBot("You are a Python programming tutor.")
print("\nChatbot Conversation:")
print("User: What are decorators?")
print("Bot:", bot.chat("What are decorators in Python?"))
print("\nUser: Show me an example")
print("Bot:", bot.chat("Show me a simple example"))

# ═══════════════════════════════════════════
# FUNCTION CALLING
# ═══════════════════════════════════════════

"""
Function Calling: Let GPT call your functions
"""

import json

# Define functions GPT can call
functions = [
    {
        "name": "get_weather",
        "description": "Get current weather for a location",
        "parameters": {
            "type": "object",
            "properties": {
                "location": {
                    "type": "string",
                    "description": "City name, e.g., San Francisco"
                },
                "unit": {
                    "type": "string",
                    "enum": ["celsius", "fahrenheit"],
                    "description": "Temperature unit"
                }
            },
            "required": ["location"]
        }
    }
]

def get_weather(location: str, unit: str = "celsius") -> dict:
    """Actual function to get weather (mock)."""
    # In real app, call weather API
    return {
        "location": location,
        "temperature": 22 if unit == "celsius" else 72,
        "condition": "Sunny",
        "unit": unit
    }

# Use function calling
response = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "user", "content": "What's the weather in Tokyo?"}
    ],
    functions=functions,
    function_call="auto"
)

# Check if GPT wants to call a function
message = response.choices[0].message

if message.function_call:
    function_name = message.function_call.name
    function_args = json.loads(message.function_call.arguments)

    print(f"\nGPT wants to call: {function_name}")
    print(f"With arguments: {function_args}")

    # Call the actual function
    if function_name == "get_weather":
        function_response = get_weather(**function_args)

        # Send function response back to GPT
        final_response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "user", "content": "What's the weather in Tokyo?"},
                message,
                {
                    "role": "function",
                    "name": function_name,
                    "content": json.dumps(function_response)
                }
            ]
        )

        print("\nFinal Response:")
        print(final_response.choices[0].message.content)

# ═══════════════════════════════════════════
# DALL-E (IMAGE GENERATION)
# ═══════════════════════════════════════════

"""
DALL-E: Generate images from text descriptions
"""

def generate_image(
    prompt: str,
    size: str = "1024x1024",
    quality: str = "standard",
    n: int = 1
) -> list:
    """
    Generate images with DALL-E.

    Sizes: 1024x1024, 1792x1024, 1024x1792
    Quality: standard, hd
    """
    response = client.images.generate(
        model="dall-e-3",
        prompt=prompt,
        size=size,
        quality=quality,
        n=n
    )

    return [img.url for img in response.data]

# Example
prompt = "A serene Japanese garden with cherry blossoms, digital art"
# images = generate_image(prompt)
# print(f"\nGenerated image URL: {images[0]}")

# Image editing
def edit_image(
    image_path: str,
    mask_path: str,
    prompt: str
) -> str:
    """Edit image using DALL-E."""
    response = client.images.edit(
        image=open(image_path, "rb"),
        mask=open(mask_path, "rb"),
        prompt=prompt,
        n=1,
        size="1024x1024"
    )
    return response.data[0].url

# Image variation
def create_variation(image_path: str) -> str:
    """Create variation of existing image."""
    response = client.images.create_variation(
        image=open(image_path, "rb"),
        n=1,
        size="1024x1024"
    )
    return response.data[0].url

# ═══════════════════════════════════════════
# WHISPER (SPEECH-TO-TEXT)
# ═══════════════════════════════════════════

"""
Whisper: Convert audio to text
"""

def transcribe_audio(audio_file_path: str) -> dict:
    """
    Transcribe audio file to text.

    Supports: mp3, mp4, mpeg, mpga, m4a, wav, webm
    Max file size: 25 MB
    """
    with open(audio_file_path, "rb") as audio_file:
        transcript = client.audio.transcriptions.create(
            model="whisper-1",
            file=audio_file,
            response_format="text"
        )
    return transcript

def translate_audio(audio_file_path: str) -> str:
    """
    Translate audio to English.
    """
    with open(audio_file_path, "rb") as audio_file:
        translation = client.audio.translations.create(
            model="whisper-1",
            file=audio_file
        )
    return translation.text

# Example usage
# transcript = transcribe_audio("meeting.mp3")
# print(f"Transcription: {transcript}")

# ═══════════════════════════════════════════
# TEXT-TO-SPEECH
# ═══════════════════════════════════════════

"""
TTS: Convert text to speech
"""

def text_to_speech(
    text: str,
    voice: str = "alloy",
    output_path: str = "output.mp3"
) -> str:
    """
    Convert text to speech.

    Voices: alloy, echo, fable, onyx, nova, shimmer
    """
    response = client.audio.speech.create(
        model="tts-1",  # or tts-1-hd for higher quality
        voice=voice,
        input=text
    )

    response.stream_to_file(output_path)
    return output_path

# Example
# text = "Hello! This is a test of the text-to-speech API."
# audio_file = text_to_speech(text, voice="nova")
# print(f"Audio saved to: {audio_file}")

# ═══════════════════════════════════════════
# EMBEDDINGS
# ═══════════════════════════════════════════

"""
Embeddings: Convert text to vector representations
"""

def get_embedding(text: str, model: str = "text-embedding-3-small") -> list:
    """
    Get embedding vector for text.

    Models:
    - text-embedding-3-small: 1536 dimensions, $0.00002/1K tokens
    - text-embedding-3-large: 3072 dimensions, $0.00013/1K tokens
    - text-embedding-ada-002: 1536 dimensions (older)
    """
    response = client.embeddings.create(
        input=text,
        model=model
    )
    return response.data[0].embedding

# Example: Semantic search
def semantic_similarity(text1: str, text2: str) -> float:
    """Calculate similarity between two texts."""
    import numpy as np

    emb1 = np.array(get_embedding(text1))
    emb2 = np.array(get_embedding(text2))

    # Cosine similarity
    similarity = np.dot(emb1, emb2) / (np.linalg.norm(emb1) * np.linalg.norm(emb2))
    return similarity

# Example
text1 = "The weather is sunny today"
text2 = "It's a beautiful day with clear skies"
text3 = "Python is a programming language"

# similarity = semantic_similarity(text1, text2)  # High similarity
# print(f"Similarity: {similarity:.4f}")

# ═══════════════════════════════════════════
# MODERATION
# ═══════════════════════════════════════════

"""
Moderation: Check content for policy violations
"""

def check_moderation(text: str) -> dict:
    """
    Check if text violates OpenAI policies.

    Categories: hate, self-harm, sexual, violence
    """
    response = client.moderations.create(input=text)
    result = response.results[0]

    return {
        'flagged': result.flagged,
        'categories': result.categories.dict(),
        'category_scores': result.category_scores.dict()
    }

# Example
# result = check_moderation("This is a test message")
# print(f"Flagged: {result['flagged']}")

print("\n✅ OpenAI API Guide Complete")
```

---

<div align="center">

## 🧠 Anthropic Claude API

</div>

### Constitutional AI 🛡️

```python
# ═══════════════════════════════════════════
# ANTHROPIC CLAUDE API
# ═══════════════════════════════════════════

"""
Claude API: Anthropic's AI assistant
- 200K+ token context window
- Strong reasoning capabilities
- Safer, more helpful
- Good for complex analysis
"""

print("="*60)
print("ANTHROPIC CLAUDE API")
print("="*60)

# Installation
# pip install anthropic

import anthropic
import os

# Initialize
client = anthropic.Anthropic(api_key=os.environ.get("ANTHROPIC_API_KEY"))

"""
╔════════════════════════════════════════════════════════════╗
║                   CLAUDE MODELS                            ║
╚════════════════════════════════════════════════════════════╝

Available Models:
─────────────────────────────────────────────────────────────
• claude-3-opus-20240229      Most capable, 200K context
• claude-3-sonnet-20240229    Balanced performance
• claude-3-haiku-20240307     Fast, cost-effective
• claude-2.1                   Legacy, 200K context

Pricing:
─────────────────────────────────────────────────────────────
Opus:   $15/1M input, $75/1M output tokens
Sonnet: $3/1M input, $15/1M output tokens
Haiku:  $0.25/1M input, $1.25/1M output tokens

Key Feature: 200K+ token context window!
"""

# ─────────────────────────────────────────────
# BASIC USAGE
# ─────────────────────────────────────────────

def claude_chat(prompt: str, model: str = "claude-3-sonnet-20240229") -> dict:
    """
    Send message to Claude.
    """
    message = client.messages.create(
        model=model,
        max_tokens=1024,
        messages=[
            {"role": "user", "content": prompt}
        ]
    )

    return {
        'content': message.content[0].text,
        'tokens': message.usage.input_tokens + message.usage.output_tokens,
        'stop_reason': message.stop_reason
    }

# Example
response = claude_chat("Explain the theory of relativity in simple terms")
print("\nClaude Response:")
print(response['content'])
print(f"Tokens: {response['tokens']}")

# ─────────────────────────────────────────────
# WITH SYSTEM PROMPT
# ─────────────────────────────────────────────

def claude_with_system(
    system: str,
    prompt: str,
    temperature: float = 1.0
) -> str:
    """
    Claude with system context.
    """
    message = client.messages.create(
        model="claude-3-sonnet-20240229",
        max_tokens=2048,
        temperature=temperature,  # 0-1
        system=system,
        messages=[
            {"role": "user", "content": prompt}
        ]
    )

    return message.content[0].text

# Example: Code reviewer
system = """You are an expert code reviewer. Review code for:
- Security vulnerabilities
- Performance issues
- Best practices
- Maintainability
Be specific and constructive."""

code_to_review = """
def login(username, password):
    query = f"SELECT * FROM users WHERE username='{username}' AND password='{password}'"
    result = db.execute(query)
    return result
"""

review = claude_with_system(system, f"Review this code:\n{code_to_review}")
print("\nCode Review:")
print(review)

# ─────────────────────────────────────────────
# MULTI-TURN CONVERSATION
# ─────────────────────────────────────────────

def claude_conversation(messages: list) -> str:
    """
    Multi-turn conversation with Claude.

    messages: [
        {"role": "user", "content": "..."},
        {"role": "assistant", "content": "..."},
        {"role": "user", "content": "..."}
    ]
    """
    response = client.messages.create(
        model="claude-3-sonnet-20240229",
        max_tokens=2048,
        messages=messages
    )

    return response.content[0].text

# Example conversation
conversation = [
    {"role": "user", "content": "What is Python?"},
    {"role": "assistant", "content": "Python is a high-level programming language..."},
    {"role": "user", "content": "Show me a hello world example"}
]

response = claude_conversation(conversation)
print("\nConversation Response:")
print(response)

# ─────────────────────────────────────────────
# LARGE DOCUMENT ANALYSIS
# ─────────────────────────────────────────────

def analyze_large_document(document: str, question: str) -> str:
    """
    Analyze large documents (up to 200K tokens!).
    """
    message = client.messages.create(
        model="claude-3-opus-20240229",  # Opus for complex analysis
        max_tokens=4096,
        messages=[
            {
                "role": "user",
                "content": f"""Here's a document:

{document}

Question: {question}"""
            }
        ]
    )

    return message.content[0].text

# Example: Analyze entire codebase or book
# long_document = "..." # Up to 200K tokens!
# analysis = analyze_large_document(long_document, "Summarize the main points")

# ─────────────────────────────────────────────
# STREAMING RESPONSES
# ─────────────────────────────────────────────

def claude_stream(prompt: str):
    """
    Stream Claude's response (for real-time display).
    """
    with client.messages.stream(
        model="claude-3-sonnet-20240229",
        max_tokens=1024,
        messages=[{"role": "user", "content": prompt}]
    ) as stream:
        for text in stream.text_stream:
            print(text, end="", flush=True)
    print()  # New line at end

# Example
print("\nStreaming Response:")
# claude_stream("Write a short poem about AI")

print("\n✅ Claude API Guide Complete")
```

---

<div align="center">

## 🔮 Google AI APIs

</div>

### Google's AI Ecosystem 🌐

```python
# ═══════════════════════════════════════════
# GOOGLE AI APIS
# ═══════════════════════════════════════════

"""
Google AI: Gemini, PaLM, and more
- Gemini Pro (multimodal)
- PaLM 2
- Vertex AI
"""

print("="*60)
print("GOOGLE AI APIS")
print("="*60)

# ═══════════════════════════════════════════
# GEMINI API
# ═══════════════════════════════════════════

"""
Gemini: Google's most capable multimodal model
"""

# Installation
# pip install google-generativeai

import google.generativeai as genai
import os

# Configure
genai.configure(api_key=os.environ.get("GOOGLE_API_KEY"))

"""
╔════════════════════════════════════════════════════════════╗
║                   GEMINI MODELS                            ║
╚════════════════════════════════════════════════════════════╝

Available Models:
─────────────────────────────────────────────────────────────
• gemini-pro              Text generation
• gemini-pro-vision       Multimodal (text + images)

Features:
─────────────────────────────────────────────────────────────
✅ 32K token context
✅ Multimodal (text, images, video)
✅ Function calling
✅ Free tier available
✅ Fast inference
"""

# ─────────────────────────────────────────────
# TEXT GENERATION
# ─────────────────────────────────────────────

def gemini_generate(prompt: str) -> str:
    """
    Generate text with Gemini Pro.
    """
    model = genai.GenerativeModel('gemini-pro')
    response = model.generate_content(prompt)
    return response.text

# Example
response = gemini_generate("Explain machine learning in simple terms")
print("\nGemini Response:")
print(response)

# ─────────────────────────────────────────────
# MULTIMODAL (TEXT + IMAGE)
# ─────────────────────────────────────────────

from PIL import Image

def gemini_vision(prompt: str, image_path: str) -> str:
    """
    Analyze image with text prompt.
    """
    model = genai.GenerativeModel('gemini-pro-vision')

    # Load image
    img = Image.open(image_path)

    # Generate response
    response = model.generate_content([prompt, img])
    return response.text

# Example
# response = gemini_vision("What's in this image?", "photo.jpg")
# print(response)

# ─────────────────────────────────────────────
# CHAT CONVERSATION
# ─────────────────────────────────────────────

def gemini_chat():
    """
    Multi-turn conversation with Gemini.
    """
    model = genai.GenerativeModel('gemini-pro')
    chat = model.start_chat(history=[])

    # Send messages
    response1 = chat.send_message("What is Python?")
    print("Bot:", response1.text)

    response2 = chat.send_message("Show me a hello world example")
    print("Bot:", response2.text)

    # Access history
    print("\nChat History:")
    for message in chat.history:
        print(f"{message.role}: {message.parts[0].text[:50]}...")

# Example
print("\nGemini Chat:")
# gemini_chat()

# ─────────────────────────────────────────────
# STREAMING
# ─────────────────────────────────────────────

def gemini_stream(prompt: str):
    """
    Stream responses from Gemini.
    """
    model = genai.GenerativeModel('gemini-pro')
    response = model.generate_content(prompt, stream=True)

    for chunk in response:
        print(chunk.text, end='', flush=True)
    print()

# Example
print("\nStreaming:")
# gemini_stream("Write a story about AI")

# ─────────────────────────────────────────────
# SAFETY SETTINGS
# ─────────────────────────────────────────────

from google.generativeai.types import HarmCategory, HarmBlockThreshold

def gemini_with_safety(prompt: str) -> str:
    """
    Generate with custom safety settings.
    """
    model = genai.GenerativeModel('gemini-pro')

    safety_settings = {
        HarmCategory.HARM_CATEGORY_HATE_SPEECH: HarmBlockThreshold.BLOCK_NONE,
        HarmCategory.HARM_CATEGORY_HARASSMENT: HarmBlockThreshold.BLOCK_NONE,
    }

    response = model.generate_content(
        prompt,
        safety_settings=safety_settings
    )

    return response.text

print("\n✅ Google AI APIs Guide Complete")
```

---

<div align="center">

## 🤗 Hugging Face

</div>

### Open-Source AI Hub 🌟

```python
# ═══════════════════════════════════════════
# HUGGING FACE
# ═══════════════════════════════════════════

"""
Hugging Face: The GitHub of Machine Learning
- 300K+ models
- Inference API
- Free tier available
- Easy integration
"""

print("="*60)
print("HUGGING FACE")
print("="*60)

# Installation
# pip install huggingface_hub

from huggingface_hub import InferenceClient
import requests
import os

"""
╔════════════════════════════════════════════════════════════╗
║                   HUGGING FACE OVERVIEW                    ║
╚════════════════════════════════════════════════════════════╝

Features:
─────────────────────────────────────────────────────────────
✅ 300K+ pre-trained models
✅ Inference API (serverless)
✅ Hosted inference endpoints
✅ Free tier (rate limited)
✅ Pro tier: $9/month
✅ Open-source models
✅ Easy model deployment

Popular Models:
─────────────────────────────────────────────────────────────
• Llama 2 (Meta)
• Mistral 7B
• Falcon
• BLOOM
• CodeLlama
• Stable Diffusion
• Whisper
"""

# Initialize client
HF_TOKEN = os.environ.get("HUGGINGFACE_TOKEN")
client = InferenceClient(token=HF_TOKEN)

# ─────────────────────────────────────────────
# TEXT GENERATION
# ─────────────────────────────────────────────

def hf_generate_text(prompt: str, model: str = "mistralai/Mistral-7B-v0.1") -> str:
    """
    Generate text using Hugging Face Inference API.
    """
    response = client.text_generation(
        prompt,
        model=model,
        max_new_tokens=500,
        temperature=0.7,
        top_p=0.95
    )
    return response

# Example
# text = hf_generate_text("Once upon a time")
# print(text)

# ─────────────────────────────────────────────
# CHAT MODELS
# ─────────────────────────────────────────────

def hf_chat(messages: list, model: str = "meta-llama/Llama-2-70b-chat-hf") -> str:
    """
    Chat with LLM using chat template.
    """
    response = client.chat_completion(
        messages=messages,
        model=model,
        max_tokens=500
    )
    return response.choices[0].message.content

# Example
messages = [
    {"role": "user", "content": "What is machine learning?"}
]
# response = hf_chat(messages)

# ─────────────────────────────────────────────
# EMBEDDINGS
# ─────────────────────────────────────────────

def hf_embeddings(text: str) -> list:
    """
    Get text embeddings.
    """
    response = client.feature_extraction(
        text,
        model="sentence-transformers/all-MiniLM-L6-v2"
    )
    return response

# Example
# embedding = hf_embeddings("Hello world")
# print(f"Embedding dimensions: {len(embedding)}")

# ─────────────────────────────────────────────
# IMAGE GENERATION
# ─────────────────────────────────────────────

def hf_generate_image(prompt: str) -> bytes:
    """
    Generate image with Stable Diffusion.
    """
    image = client.text_to_image(
        prompt,
        model="stabilityai/stable-diffusion-2-1"
    )
    return image

# Example
# image = hf_generate_image("A beautiful sunset over mountains")
# image.save("output.png")

# ─────────────────────────────────────────────
# SPEECH-TO-TEXT
# ─────────────────────────────────────────────

def hf_transcribe(audio_path: str) -> str:
    """
    Transcribe audio with Whisper.
    """
    with open(audio_path, "rb") as audio:
        result = client.automatic_speech_recognition(
            audio.read(),
            model="openai/whisper-large-v3"
        )
    return result.text

# ─────────────────────────────────────────────
# TRANSLATION
# ─────────────────────────────────────────────

def hf_translate(text: str, source: str = "en", target: str = "fr") -> str:
    """
    Translate text.
    """
    model = f"Helsinki-NLP/opus-mt-{source}-{target}"
    result = client.translation(text, model=model)
    return result.translation_text

# Example
# translated = hf_translate("Hello, how are you?", "en", "es")
# print(translated)

# ─────────────────────────────────────────────
# SENTIMENT ANALYSIS
# ─────────────────────────────────────────────

def hf_sentiment(text: str) -> dict:
    """
    Analyze sentiment.
    """
    result = client.text_classification(
        text,
        model="distilbert-base-uncased-finetuned-sst-2-english"
    )
    return {
        'label': result[0].label,
        'score': result[0].score
    }

# Example
# sentiment = hf_sentiment("I love this product!")
# print(sentiment)

# ─────────────────────────────────────────────
# USING INFERENCE ENDPOINTS
# ─────────────────────────────────────────────

"""
For production: Use dedicated inference endpoints
- $0.06/hour (CPU)
- $0.60/hour (GPU)
- No rate limits
- Custom scaling
"""

def query_endpoint(endpoint_url: str, payload: dict) -> dict:
    """
    Query dedicated endpoint.
    """
    headers = {"Authorization": f"Bearer {HF_TOKEN}"}
    response = requests.post(endpoint_url, headers=headers, json=payload)
    return response.json()

# Example
# endpoint = "https://api-inference.huggingface.co/models/..."
# result = query_endpoint(endpoint, {"inputs": "Hello world"})

print("\n✅ Hugging Face Guide Complete")
```

---

<div align="center">

## 🎨 Image Generation APIs

</div>

### Create Stunning Images with AI 🖼️

```python
# ═══════════════════════════════════════════
# IMAGE GENERATION APIS
# ═══════════════════════════════════════════

print("="*60)
print("IMAGE GENERATION APIS")
print("="*60)

# ═══════════════════════════════════════════
# STABILITY AI
# ═══════════════════════════════════════════

"""
Stability AI: Creators of Stable Diffusion
- Stable Diffusion XL
- Image-to-image
- Upscaling
- Editing
"""

# Installation
# pip install stability-sdk

import requests
import os

STABILITY_API_KEY = os.environ.get("STABILITY_API_KEY")

def stability_generate_image(
    prompt: str,
    negative_prompt: str = "",
    width: int = 1024,
    height: int = 1024,
    steps: int = 30,
    cfg_scale: float = 7.0
) -> bytes:
    """
    Generate image with Stability AI.
    """
    url = "https://api.stability.ai/v1/generation/stable-diffusion-xl-1024-v1-0/text-to-image"

    headers = {
        "Authorization": f"Bearer {STABILITY_API_KEY}",
        "Content-Type": "application/json"
    }

    body = {
        "text_prompts": [
            {"text": prompt, "weight": 1},
            {"text": negative_prompt, "weight": -1}
        ],
        "cfg_scale": cfg_scale,
        "height": height,
        "width": width,
        "steps": steps,
        "samples": 1
    }

    response = requests.post(url, headers=headers, json=body)

    if response.status_code == 200:
        data = response.json()
        return data["artifacts"][0]["base64"]
    else:
        raise Exception(f"Error: {response.text}")

# Example
# prompt = "A futuristic city with flying cars, cyberpunk style, 8k"
# negative = "blurry, low quality"
# image_b64 = stability_generate_image(prompt, negative)
# Save image...

# ─────────────────────────────────────────────
# IMAGE-TO-IMAGE
# ─────────────────────────────────────────────

def stability_image_to_image(
    init_image_path: str,
    prompt: str,
    strength: float = 0.5
) -> bytes:
    """
    Transform existing image.

    strength: 0-1, higher = more change
    """
    url = "https://api.stability.ai/v1/generation/stable-diffusion-xl-1024-v1-0/image-to-image"

    headers = {
        "Authorization": f"Bearer {STABILITY_API_KEY}"
    }

    files = {
        "init_image": open(init_image_path, "rb")
    }

    data = {
        "text_prompts[0][text]": prompt,
        "text_prompts[0][weight]": 1,
        "cfg_scale": 7,
        "samples": 1,
        "steps": 30,
        "image_strength": strength
    }

    response = requests.post(url, headers=headers, files=files, data=data)
    return response.json()["artifacts"][0]["base64"]

# ─────────────────────────────────────────────
# UPSCALING
# ─────────────────────────────────────────────

def stability_upscale(image_path: str, width: int = 2048) -> bytes:
    """
    Upscale image up to 4K.
    """
    url = "https://api.stability.ai/v1/generation/esrgan-v1-x2plus/image-to-image/upscale"

    headers = {
        "Authorization": f"Bearer {STABILITY_API_KEY}"
    }

    files = {
        "image": open(image_path, "rb")
    }

    data = {
        "width": width
    }

    response = requests.post(url, headers=headers, files=files, data=data)
    return response.json()["artifacts"][0]["base64"]

# ═══════════════════════════════════════════
# REPLICATE (MIDJOURNEY-STYLE)
# ═══════════════════════════════════════════

"""
Replicate: Run ML models via API
- Access to Midjourney-style models
- SDXL, Flux, and more
"""

# Installation
# pip install replicate

import replicate

def replicate_generate(prompt: str) -> str:
    """
    Generate with SDXL on Replicate.
    """
    output = replicate.run(
        "stability-ai/sdxl:39ed52f2a78e934b3ba6e2a89f5b1c712de7dfea535525255b1aa35c5565e08b",
        input={
            "prompt": prompt,
            "negative_prompt": "ugly, blurry, low quality",
            "width": 1024,
            "height": 1024,
            "num_outputs": 1
        }
    )
    return output[0]  # URL to generated image

# Example
# image_url = replicate_generate("A serene mountain landscape")
# print(image_url)

# ═══════════════════════════════════════════
# LEONARDO.AI
# ═══════════════════════════════════════════

"""
Leonardo.ai: Game asset generation
- Specialized for game art
- Character design
- Environment art
"""

def leonardo_generate(prompt: str, api_key: str) -> dict:
    """
    Generate with Leonardo.ai.
    """
    url = "https://cloud.leonardo.ai/api/rest/v1/generations"

    headers = {
        "Authorization": f"Bearer {api_key}",
        "Content-Type": "application/json"
    }

    payload = {
        "prompt": prompt,
        "modelId": "6bef9f1b-29cb-40c7-b9df-32b51c1f67d3",  # Leonardo Creative
        "width": 1024,
        "height": 1024,
        "num_images": 1
    }

    response = requests.post(url, json=payload, headers=headers)
    return response.json()

print("\n✅ Image Generation APIs Complete")
```

---

<div align="center">

## 🗣️ Speech & Audio APIs

</div>

### Voice and Audio AI 🎙️

```python
# ═══════════════════════════════════════════
# SPEECH & AUDIO APIS
# ═══════════════════════════════════════════

print("="*60)
print("SPEECH & AUDIO APIS")
print("="*60)

# ═══════════════════════════════════════════
# ELEVENLABS (TEXT-TO-SPEECH)
# ═══════════════════════════════════════════

"""
ElevenLabs: Most realistic TTS
- Natural-sounding voices
- Voice cloning
- Multiple languages
"""

# Installation
# pip install elevenlabs

from elevenlabs import generate, play, set_api_key, voices

def elevenlabs_tts(
    text: str,
    voice: str = "Bella",
    model: str = "eleven_monolingual_v1"
) -> bytes:
    """
    Generate speech with ElevenLabs.

    Popular voices: Bella, Antoni, Elli, Josh, Arnold
    Models:
    - eleven_monolingual_v1 (English)
    - eleven_multilingual_v1 (Multiple languages)
    """
    set_api_key(os.environ.get("ELEVENLABS_API_KEY"))

    audio = generate(
        text=text,
        voice=voice,
        model=model
    )

    return audio

# Example
# audio = elevenlabs_tts("Hello! This is a test of text-to-speech.")
# Save audio or play it

# List available voices
def list_elevenlabs_voices():
    """Get all available voices."""
    set_api_key(os.environ.get("ELEVENLABS_API_KEY"))
    voice_list = voices()

    for voice in voice_list:
        print(f"{voice.name}: {voice.voice_id}")

# ─────────────────────────────────────────────
# VOICE CLONING
# ─────────────────────────────────────────────

from elevenlabs import clone

def clone_voice(
    name: str,
    description: str,
    audio_files: list
) -> str:
    """
    Clone a voice from audio samples.
    """
    set_api_key(os.environ.get("ELEVENLABS_API_KEY"))

    voice = clone(
        name=name,
        description=description,
        files=audio_files
    )

    return voice.voice_id

# Example
# voice_id = clone_voice(
#     name="My Voice",
#     description="A professional voice",
#     audio_files=["sample1.mp3", "sample2.mp3"]
# )

# ═══════════════════════════════════════════
# ASSEMBLYAI (SPEECH-TO-TEXT)
# ═══════════════════════════════════════════

"""
AssemblyAI: Advanced speech recognition
- Speaker diarization
- Sentiment analysis
- Topic detection
- PII redaction
"""

# Installation
# pip install assemblyai

import assemblyai as aai

def assemblyai_transcribe(audio_url: str) -> dict:
    """
    Transcribe audio with advanced features.
    """
    aai.settings.api_key = os.environ.get("ASSEMBLYAI_API_KEY")

    config = aai.TranscriptionConfig(
        speaker_labels=True,  # Speaker diarization
        sentiment_analysis=True,
        entity_detection=True,
        auto_highlights=True
    )

    transcriber = aai.Transcriber()
    transcript = transcriber.transcribe(audio_url, config=config)

    return {
        'text': transcript.text,
        'speakers': [
            {
                'speaker': utterance.speaker,
                'text': utterance.text,
                'sentiment': utterance.sentiment
            }
            for utterance in transcript.utterances
        ],
        'highlights': transcript.auto_highlights
    }

# Example
# result = assemblyai_transcribe("https://example.com/audio.mp3")
# print(result['text'])

# ─────────────────────────────────────────────
# REAL-TIME TRANSCRIPTION
# ─────────────────────────────────────────────

def assemblyai_realtime():
    """
    Real-time speech-to-text.
    """
    aai.settings.api_key = os.environ.get("ASSEMBLYAI_API_KEY")

    def on_data(transcript: aai.RealtimeTranscript):
        if not transcript.text:
            return

        if isinstance(transcript, aai.RealtimeFinalTranscript):
            print(transcript.text, end="\r\n")
        else:
            print(transcript.text, end="\r")

    def on_error(error: aai.RealtimeError):
        print("Error:", error)

    transcriber = aai.RealtimeTranscriber(
        on_data=on_data,
        on_error=on_error,
        sample_rate=16000
    )

    transcriber.connect()

    # Stream audio to transcriber
    # microphone_stream = aai.extras.MicrophoneStream()
    # transcriber.stream(microphone_stream)

    # transcriber.close()

# ═══════════════════════════════════════════
# MURF.AI (TTS)
# ═══════════════════════════════════════════

"""
Murf.ai: Professional voiceovers
- 120+ voices
- Multiple languages
- Voice customization
"""

def murf_generate(text: str, voice_id: str) -> bytes:
    """
    Generate voiceover with Murf.ai.
    """
    url = "https://api.murf.ai/v1/speech/generate"

    headers = {
        "Authorization": f"Bearer {os.environ.get('MURF_API_KEY')}",
        "Content-Type": "application/json"
    }

    payload = {
        "voiceId": voice_id,
        "text": text,
        "format": "MP3",
        "sampleRate": 48000
    }

    response = requests.post(url, json=payload, headers=headers)
    return response.content

print("\n✅ Speech & Audio APIs Complete")
```

---

<div align="center">

## ☁️ Cloud AI Services

</div>

### Enterprise AI Platforms 🏢

```bash
# ═══════════════════════════════════════════
# CLOUD AI SERVICES OVERVIEW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CLOUD AI COMPARISON                      ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Service           | AWS                 | Azure                    | Google Cloud        |
| ----------------- | ------------------- | ------------------------ | ------------------- |
| **Text AI**       | Bedrock, Comprehend | OpenAI Service, Language | Vertex AI, PaLM API |
| **Vision**        | Rekognition         | Computer Vision          | Vision AI           |
| **Speech**        | Transcribe, Polly   | Speech Services          | Speech-to-Text, TTS |
| **Translation**   | Translate           | Translator               | Translation API     |
| **Custom Models** | SageMaker           | ML Studio                | Vertex AI           |
| **AutoML**        | AutoML              | AutoML                   | AutoML Tables       |
| **Pre-built**     | ✅✅✅              | ✅✅✅                   | ✅✅✅              |
| **Pricing**       | Pay-per-use         | Pay-per-use              | Pay-per-use         |
| **Free Tier**     | ✅ Limited          | ✅ Limited               | ✅ Limited          |

</div>

```python
# ═══════════════════════════════════════════
# AWS AI SERVICES
# ═══════════════════════════════════════════

"""
AWS AI Services: Comprehensive AI portfolio
"""

import boto3

# ─────────────────────────────────────────────
# AWS BEDROCK (LLMs)
# ─────────────────────────────────────────────

def aws_bedrock_chat(prompt: str) -> str:
    """
    Use Claude, Llama, or other LLMs via Bedrock.
    """
    bedrock = boto3.client('bedrock-runtime', region_name='us-east-1')

    body = {
        "prompt": prompt,
        "max_tokens_to_sample": 500,
        "temperature": 0.7
    }

    response = bedrock.invoke_model(
        modelId="anthropic.claude-v2",
        body=json.dumps(body)
    )

    return json.loads(response['body'].read())['completion']

# ─────────────────────────────────────────────
# AWS REKOGNITION (VISION)
# ─────────────────────────────────────────────

def aws_detect_labels(image_bytes: bytes) -> list:
    """
    Detect objects and scenes in images.
    """
    rekognition = boto3.client('rekognition', region_name='us-east-1')

    response = rekognition.detect_labels(
        Image={'Bytes': image_bytes},
        MaxLabels=10,
        MinConfidence=80
    )

    return [
        {'label': label['Name'], 'confidence': label['Confidence']}
        for label in response['Labels']
    ]

def aws_detect_faces(image_bytes: bytes) -> list:
    """
    Detect and analyze faces.
    """
    rekognition = boto3.client('rekognition')

    response = rekognition.detect_faces(
        Image={'Bytes': image_bytes},
        Attributes=['ALL']
    )

    return response['FaceDetails']

# ─────────────────────────────────────────────
# AWS TRANSCRIBE (SPEECH-TO-TEXT)
# ─────────────────────────────────────────────

def aws_transcribe(audio_s3_uri: str, job_name: str) -> str:
    """
    Transcribe audio file from S3.
    """
    transcribe = boto3.client('transcribe')

    transcribe.start_transcription_job(
        TranscriptionJobName=job_name,
        Media={'MediaFileUri': audio_s3_uri},
        MediaFormat='mp3',
        LanguageCode='en-US'
    )

    # Wait for completion
    while True:
        status = transcribe.get_transcription_job(
            TranscriptionJobName=job_name
        )
        if status['TranscriptionJob']['TranscriptionJobStatus'] in ['COMPLETED', 'FAILED']:
            break
        time.sleep(5)

    if status['TranscriptionJob']['TranscriptionJobStatus'] == 'COMPLETED':
        transcript_uri = status['TranscriptionJob']['Transcript']['TranscriptFileUri']
        # Fetch and return transcript
        return transcript_uri

# ═══════════════════════════════════════════
# AZURE AI SERVICES
# ═══════════════════════════════════════════

"""
Azure AI: Microsoft's AI platform
"""

# ─────────────────────────────────────────────
# AZURE OPENAI SERVICE
# ─────────────────────────────────────────────

from openai import AzureOpenAI

def azure_openai_chat(prompt: str) -> str:
    """
    Use GPT-4 via Azure OpenAI Service.
    """
    client = AzureOpenAI(
        api_key=os.environ.get("AZURE_OPENAI_KEY"),
        api_version="2024-02-01",
        azure_endpoint=os.environ.get("AZURE_OPENAI_ENDPOINT")
    )

    response = client.chat.completions.create(
        model="gpt-4",  # deployment name
        messages=[
            {"role": "user", "content": prompt}
        ]
    )

    return response.choices[0].message.content

# ─────────────────────────────────────────────
# AZURE COMPUTER VISION
# ─────────────────────────────────────────────

from azure.cognitiveservices.vision.computervision import ComputerVisionClient
from msrest.authentication import CognitiveServicesCredentials

def azure_analyze_image(image_url: str) -> dict:
    """
    Analyze image with Azure Computer Vision.
    """
    client = ComputerVisionClient(
        os.environ.get("AZURE_CV_ENDPOINT"),
        CognitiveServicesCredentials(os.environ.get("AZURE_CV_KEY"))
    )

    features = ["tags", "description", "categories", "objects"]

    analysis = client.analyze_image(image_url, features)

    return {
        'description': analysis.description.captions[0].text,
        'tags': [tag.name for tag in analysis.tags],
        'objects': [obj.object_property for obj in analysis.objects]
    }

# ─────────────────────────────────────────────
# AZURE SPEECH
# ─────────────────────────────────────────────

import azure.cognitiveservices.speech as speechsdk

def azure_speech_to_text(audio_file: str) -> str:
    """
    Transcribe with Azure Speech.
    """
    speech_config = speechsdk.SpeechConfig(
        subscription=os.environ.get("AZURE_SPEECH_KEY"),
        region=os.environ.get("AZURE_SPEECH_REGION")
    )

    audio_config = speechsdk.audio.AudioConfig(filename=audio_file)
    speech_recognizer = speechsdk.SpeechRecognizer(
        speech_config=speech_config,
        audio_config=audio_config
    )

    result = speech_recognizer.recognize_once()
    return result.text

def azure_text_to_speech(text: str, output_file: str):
    """
    Generate speech with Azure.
    """
    speech_config = speechsdk.SpeechConfig(
        subscription=os.environ.get("AZURE_SPEECH_KEY"),
        region=os.environ.get("AZURE_SPEECH_REGION")
    )

    audio_config = speechsdk.audio.AudioOutputConfig(filename=output_file)
    synthesizer = speechsdk.SpeechSynthesizer(
        speech_config=speech_config,
        audio_config=audio_config
    )

    synthesizer.speak_text_async(text).get()

print("\n✅ Cloud AI Services Complete")
```

---

<div align="center">

## 📊 Comparison Guide

</div>

### Choose the Right AI API 🎯

```bash
# ═══════════════════════════════════════════
# COMPREHENSIVE API COMPARISON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TEXT GENERATION APIs                     ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| API               | Context | Quality    | Speed      | Price (1M tokens) | Best For         |
| ----------------- | ------- | ---------- | ---------- | ----------------- | ---------------- |
| **OpenAI GPT-4**  | 8K      | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | $30-60            | Complex tasks    |
| **GPT-3.5 Turbo** | 16K     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | $0.50-1.50        | Fast, affordable |
| **Claude Opus**   | 200K    | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | $15-75            | Large documents  |
| **Claude Sonnet** | 200K    | ⭐⭐⭐⭐   | ⭐⭐⭐⭐   | $3-15             | Balanced         |
| **Gemini Pro**    | 32K     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐   | Free/Paid         | Google users     |
| **Cohere**        | 4K      | ⭐⭐⭐     | ⭐⭐⭐⭐   | $1-2              | Enterprise       |
| **Llama 2 (HF)**  | 4K      | ⭐⭐⭐     | ⭐⭐⭐     | Free\*            | Open-source      |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   IMAGE GENERATION APIs                    ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| API                     | Quality    | Speed    | Price/Image | Features             | Best For     |
| ----------------------- | ---------- | -------- | ----------- | -------------------- | ------------ |
| **DALL-E 3**            | ⭐⭐⭐⭐⭐ | ⭐⭐⭐   | $0.04-0.08  | High quality, safety | Professional |
| **Stable Diffusion XL** | ⭐⭐⭐⭐   | ⭐⭐⭐⭐ | $0.02-0.05  | Customizable         | Flexible     |
| **Midjourney**          | ⭐⭐⭐⭐⭐ | ⭐⭐⭐   | $10-60/mo   | Artistic             | Artists      |
| **Leonardo.ai**         | ⭐⭐⭐⭐   | ⭐⭐⭐⭐ | Free tier   | Game assets          | Game dev     |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   SPEECH APIs                              ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| API              | Quality    | Languages | Price/min | Features      | Best For       |
| ---------------- | ---------- | --------- | --------- | ------------- | -------------- |
| **ElevenLabs**   | ⭐⭐⭐⭐⭐ | 29        | $0.30     | Voice cloning | Premium voices |
| **OpenAI TTS**   | ⭐⭐⭐⭐   | Multiple  | $0.015    | Fast          | General use    |
| **Google TTS**   | ⭐⭐⭐⭐   | 100+      | $0.000004 | WaveNet       | Scale          |
| **Azure Speech** | ⭐⭐⭐⭐   | 100+      | $0.001    | Neural voices | Enterprise     |
| **AWS Polly**    | ⭐⭐⭐     | 60+       | $0.000004 | Neural        | AWS users      |

</div>

```bash
╔════════════════════════════════════════════════════════════╗
║                   DECISION MATRIX                          ║
╚════════════════════════════════════════════════════════════╝

Choose Based On:
─────────────────────────────────────────────────────────────

Budget:
  Free:           Gemini Pro, Hugging Face
  Low ($0-50/mo): GPT-3.5, Claude Haiku
  Medium:         GPT-4, Claude Sonnet
  High:           Claude Opus, DALL-E 3

Use Case:
  Chatbot:        GPT-3.5, Claude Haiku
  Complex tasks:  GPT-4, Claude Opus
  Large docs:     Claude (200K context)
  Images:         DALL-E 3, Stable Diffusion
  Voice:          ElevenLabs, OpenAI TTS
  Transcription:  Whisper, AssemblyAI

Scale:
  Prototype:      Free tiers
  Small app:      Pay-per-use APIs
  Medium app:     Dedicated endpoints
  Enterprise:     Cloud AI services

Privacy:
  High privacy:   On-premise (Hugging Face)
  Moderate:       Enterprise APIs (Azure)
  Standard:       Public APIs

Integration:
  Quick start:    OpenAI, Anthropic
  AWS:            Bedrock, Rekognition
  Azure:          Azure OpenAI
  Google:         Vertex AI

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 💡 Best Practices

</div>

### API Integration Guidelines 📋

```bash
# ═══════════════════════════════════════════
# AI API BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   IMPLEMENTATION BEST PRACTICES            ║
╚════════════════════════════════════════════════════════════╝

1. Error Handling
─────────────────────────────────────────────────────────────
```

```python
import time
from functools import wraps

def retry_with_exponential_backoff(
    func,
    max_retries=3,
    initial_delay=1,
    backoff_factor=2
):
    """
    Retry with exponential backoff.
    """
    @wraps(func)
    def wrapper(*args, **kwargs):
        delay = initial_delay

        for attempt in range(max_retries):
            try:
                return func(*args, **kwargs)
            except Exception as e:
                if attempt == max_retries - 1:
                    raise

                print(f"Attempt {attempt + 1} failed: {e}")
                time.sleep(delay)
                delay *= backoff_factor

    return wrapper

@retry_with_exponential_backoff
def call_api(prompt):
    """API call with retry logic."""
    return client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
```

```bash
2. Rate Limiting
─────────────────────────────────────────────────────────────
```

```python
from ratelimit import limits, sleep_and_retry

# Limit: 3 calls per second
@sleep_and_retry
@limits(calls=3, period=1)
def rate_limited_api_call(prompt):
    """
    API call with rate limiting.
    """
    return client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
```

```bash
3. Caching
─────────────────────────────────────────────────────────────
```

```python
from functools import lru_cache
import hashlib

@lru_cache(maxsize=1000)
def cached_api_call(prompt: str) -> str:
    """
    Cache API responses to reduce costs.
    """
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}],
        temperature=0  # Deterministic for caching
    )
    return response.choices[0].message.content

# Or use Redis for distributed caching
import redis
import json

redis_client = redis.Redis(host='localhost', port=6379)

def cached_with_redis(prompt: str) -> str:
    """
    Cache with Redis.
    """
    # Create cache key
    cache_key = hashlib.md5(prompt.encode()).hexdigest()

    # Check cache
    cached = redis_client.get(cache_key)
    if cached:
        return json.loads(cached)

    # Call API
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    result = response.choices[0].message.content

    # Cache result (expire in 1 hour)
    redis_client.setex(cache_key, 3600, json.dumps(result))

    return result
```

```bash
4. Cost Tracking
─────────────────────────────────────────────────────────────
```

```python
class CostTracker:
    """
    Track API costs.
    """
    def __init__(self):
        self.total_input_tokens = 0
        self.total_output_tokens = 0
        self.total_cost = 0.0

    def track_call(self, usage, model="gpt-3.5-turbo"):
        """Track a single API call."""
        input_tokens = usage.prompt_tokens
        output_tokens = usage.completion_tokens

        # Calculate cost
        if model == "gpt-3.5-turbo":
            cost = (input_tokens * 0.0005 + output_tokens * 0.0015) / 1000
        elif model == "gpt-4":
            cost = (input_tokens * 0.03 + output_tokens * 0.06) / 1000

        self.total_input_tokens += input_tokens
        self.total_output_tokens += output_tokens
        self.total_cost += cost

    def report(self):
        """Generate cost report."""
        return {
            'input_tokens': self.total_input_tokens,
            'output_tokens': self.total_output_tokens,
            'total_tokens': self.total_input_tokens + self.total_output_tokens,
            'total_cost': f"${self.total_cost:.4f}"
        }

# Usage
tracker = CostTracker()

response = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[{"role": "user", "content": "Hello"}]
)

tracker.track_call(response.usage)
print(tracker.report())
```

```bash
5. Monitoring & Logging
─────────────────────────────────────────────────────────────
```

```python
import logging
from datetime import datetime

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def monitored_api_call(prompt: str) -> dict:
    """
    API call with monitoring.
    """
    start_time = datetime.now()

    try:
        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}]
        )

        duration = (datetime.now() - start_time).total_seconds()

        logger.info({
            'status': 'success',
            'model': 'gpt-3.5-turbo',
            'tokens': response.usage.total_tokens,
            'duration': duration,
            'timestamp': datetime.now().isoformat()
        })

        return {
            'content': response.choices[0].message.content,
            'metadata': {
                'tokens': response.usage.total_tokens,
                'duration': duration
            }
        }

    except Exception as e:
        logger.error({
            'status': 'error',
            'error': str(e),
            'timestamp': datetime.now().isoformat()
        })
        raise
```

```bash
╔════════════════════════════════════════════════════════════╗
║                   PROMPT OPTIMIZATION                      ║
╚════════════════════════════════════════════════════════════╝

Save costs by optimizing prompts:
─────────────────────────────────────────────────────────────

1. Be Concise
   ❌ "I would like you to please help me understand..."
   ✅ "Explain..."

2. Use System Messages Efficiently
   Set context once in system message, not every user message

3. Limit Output Length
   max_tokens=500  # Don't let it generate unnecessarily

4. Use Cheaper Models When Possible
   • GPT-3.5 for simple tasks
   • GPT-4 only when needed

5. Batch Requests
   Process multiple items in one API call when possible

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔒 Security & Cost Management

</div>

### Protect Your API Keys and Budget 💰

```bash
# ═══════════════════════════════════════════
# SECURITY & COST MANAGEMENT
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SECURITY BEST PRACTICES                  ║
╚════════════════════════════════════════════════════════════╝

1. API Key Management
─────────────────────────────────────────────────────────────
```

```python
# ❌ NEVER DO THIS
openai.api_key = "sk-1234567890abcdef"  # Hardcoded!

# ✅ USE ENVIRONMENT VARIABLES
import os
from dotenv import load_dotenv

load_dotenv()
openai.api_key = os.environ.get("OPENAI_API_KEY")

# ✅ USE SECRET MANAGERS (Production)
import boto3
from botocore.exceptions import ClientError

def get_secret(secret_name):
    """
    Retrieve API key from AWS Secrets Manager.
    """
    client = boto3.client('secretsmanager', region_name='us-east-1')

    try:
        response = client.get_secret_value(SecretId=secret_name)
        return response['SecretString']
    except ClientError as e:
        raise Exception(f"Error retrieving secret: {e}")

# Usage
api_key = get_secret("prod/openai/api_key")
```

```bash
2. Environment Variables Setup
─────────────────────────────────────────────────────────────
```

```bash
# .env file (NEVER commit to git!)
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
HUGGINGFACE_TOKEN=hf_...
STABILITY_API_KEY=sk-...

# .gitignore
.env
.env.local
.env.production
```

```python
# config.py
import os
from pydantic import BaseSettings

class Settings(BaseSettings):
    """
    Application settings with validation.
    """
    openai_api_key: str
    anthropic_api_key: str
    max_tokens: int = 1000
    temperature: float = 0.7

    class Config:
        env_file = ".env"

settings = Settings()
```

```bash
3. Rate Limiting & Quotas
─────────────────────────────────────────────────────────────
```

```python
class APIQuotaManager:
    """
    Manage API quotas and prevent overspending.
    """
    def __init__(self, daily_limit: float = 100.0):
        self.daily_limit = daily_limit  # USD
        self.daily_spent = 0.0
        self.reset_date = datetime.now().date()

    def check_budget(self, estimated_cost: float) -> bool:
        """Check if we can afford this call."""
        # Reset if new day
        if datetime.now().date() > self.reset_date:
            self.daily_spent = 0.0
            self.reset_date = datetime.now().date()

        return (self.daily_spent + estimated_cost) <= self.daily_limit

    def record_spend(self, cost: float):
        """Record API spend."""
        self.daily_spent += cost

    def get_remaining_budget(self) -> float:
        """Get remaining budget."""
        return self.daily_limit - self.daily_spent

# Usage
quota = APIQuotaManager(daily_limit=50.0)

def safe_api_call(prompt: str):
    """API call with budget check."""
    # Estimate cost (rough)
    estimated_tokens = len(prompt.split()) * 1.3
    estimated_cost = (estimated_tokens * 0.002) / 1000

    if not quota.check_budget(estimated_cost):
        raise Exception("Daily budget exceeded!")

    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    # Record actual cost
    actual_cost = calculate_cost(response.usage, "gpt-3.5-turbo")
    quota.record_spend(actual_cost)

    return response.choices[0].message.content
```

```bash
4. Input Validation & Sanitization
─────────────────────────────────────────────────────────────
```

```python
def sanitize_input(user_input: str) -> str:
    """
    Sanitize user input before sending to API.
    """
    # Remove excessive whitespace
    sanitized = " ".join(user_input.split())

    # Limit length
    max_length = 4000
    if len(sanitized) > max_length:
        sanitized = sanitized[:max_length]

    # Remove potential injection attempts
    dangerous_patterns = ["<script>", "javascript:", "onerror="]
    for pattern in dangerous_patterns:
        sanitized = sanitized.replace(pattern, "")

    return sanitized

def validate_input(user_input: str) -> bool:
    """
    Validate user input.
    """
    # Check length
    if len(user_input) == 0 or len(user_input) > 10000:
        return False

    # Check for suspicious patterns
    if any(pattern in user_input.lower() for pattern in ["ignore previous", "disregard"]):
        return False

    return True

# Usage
user_input = request.form.get('prompt')

if not validate_input(user_input):
    return {"error": "Invalid input"}, 400

sanitized = sanitize_input(user_input)
response = call_api(sanitized)
```

```bash
5. Output Filtering
─────────────────────────────────────────────────────────────
```

```python
def filter_sensitive_output(text: str) -> str:
    """
    Filter potentially sensitive information from output.
    """
    import re

    # Remove potential API keys
    text = re.sub(r'sk-[a-zA-Z0-9]{48}', '[REDACTED_API_KEY]', text)

    # Remove email addresses (if needed)
    text = re.sub(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b',
                  '[EMAIL_REDACTED]', text)

    # Remove phone numbers
    text = re.sub(r'\b\d{3}[-.]?\d{3}[-.]?\d{4}\b', '[PHONE_REDACTED]', text)

    return text

# Usage with moderation
def safe_generate(prompt: str) -> dict:
    """
    Generate with content moderation.
    """
    # Check input
    moderation = client.moderations.create(input=prompt)
    if moderation.results[0].flagged:
        return {
            'error': 'Content policy violation',
            'categories': moderation.results[0].categories.dict()
        }

    # Generate
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    output = response.choices[0].message.content

    # Filter output
    filtered = filter_sensitive_output(output)

    return {'content': filtered}
```

```bash
╔════════════════════════════════════════════════════════════╗
║                   COST OPTIMIZATION STRATEGIES             ║
╚════════════════════════════════════════════════════════════╝

1. Model Selection Strategy
─────────────────────────────────────────────────────────────
```

```python
class SmartModelRouter:
    """
    Route requests to appropriate model based on complexity.
    """
    def __init__(self):
        self.complexity_threshold = 100  # tokens

    def analyze_complexity(self, prompt: str) -> str:
        """
        Determine if task needs GPT-4 or GPT-3.5 is enough.
        """
        # Simple heuristics
        keywords_needing_gpt4 = [
            'analyze', 'complex', 'detailed', 'explain in depth',
            'compare', 'evaluate', 'critique'
        ]

        prompt_lower = prompt.lower()
        needs_gpt4 = any(keyword in prompt_lower for keyword in keywords_needing_gpt4)

        # Check length
        if len(prompt.split()) > 200:
            needs_gpt4 = True

        return "gpt-4" if needs_gpt4 else "gpt-3.5-turbo"

    def route_request(self, prompt: str) -> str:
        """
        Route to appropriate model.
        """
        model = self.analyze_complexity(prompt)

        response = client.chat.completions.create(
            model=model,
            messages=[{"role": "user", "content": prompt}]
        )

        return response.choices[0].message.content

# Usage - saves money by using GPT-3.5 when possible!
router = SmartModelRouter()
result = router.route_request("What is 2+2?")  # Uses GPT-3.5
```

```bash
2. Prompt Compression
─────────────────────────────────────────────────────────────
```

```python
def compress_prompt(prompt: str, max_length: int = 500) -> str:
    """
    Compress long prompts to reduce token usage.
    """
    if len(prompt.split()) <= max_length:
        return prompt

    # Use GPT-3.5 to summarize the prompt
    summary = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {
                "role": "system",
                "content": "Compress this text while keeping key information."
            },
            {
                "role": "user",
                "content": prompt
            }
        ],
        max_tokens=max_length
    )

    return summary.choices[0].message.content

# Example: Long document analysis
long_document = "..." * 10000  # Very long text

# Instead of sending entire document
# compressed = compress_prompt(long_document)
# analysis = analyze_document(compressed)
```

```bash
3. Batch Processing
─────────────────────────────────────────────────────────────
```

```python
def batch_classify(items: list[str]) -> list[str]:
    """
    Classify multiple items in one API call.
    """
    # Combine items
    prompt = "Classify each of the following items:\n\n"
    for i, item in enumerate(items, 1):
        prompt += f"{i}. {item}\n"

    prompt += "\nProvide classifications in order."

    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    # Parse response
    classifications = response.choices[0].message.content.split('\n')
    return classifications

# Single call instead of 10!
items = ["item1", "item2", "item3", ...]
classifications = batch_classify(items)
```

```bash
4. Streaming for Better UX
─────────────────────────────────────────────────────────────
```

```python
def stream_response(prompt: str):
    """
    Stream response for better user experience.
    No additional cost, but feels faster!
    """
    stream = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}],
        stream=True
    )

    full_response = ""
    for chunk in stream:
        if chunk.choices[0].delta.content:
            content = chunk.choices[0].delta.content
            full_response += content
            print(content, end='', flush=True)

    return full_response
```

```bash
╔════════════════════════════════════════════════════════════╗
║                   MONITORING & ALERTS                      ║
╚════════════════════════════════════════════════════════════╝
```

```python
class APIMonitor:
    """
    Monitor API usage and send alerts.
    """
    def __init__(self, alert_threshold: float = 80.0):
        self.alert_threshold = alert_threshold
        self.daily_limit = 100.0
        self.daily_spent = 0.0

    def check_and_alert(self):
        """Check spending and alert if needed."""
        usage_percent = (self.daily_spent / self.daily_limit) * 100

        if usage_percent >= self.alert_threshold:
            self.send_alert(
                f"API spending at {usage_percent:.1f}% of daily limit! "
                f"${self.daily_spent:.2f} / ${self.daily_limit:.2f}"
            )

    def send_alert(self, message: str):
        """Send alert (email, Slack, etc.)."""
        # Example: Send to Slack
        import requests

        slack_webhook = os.environ.get("SLACK_WEBHOOK_URL")
        if slack_webhook:
            requests.post(slack_webhook, json={"text": f"⚠️ {message}"})

        # Example: Send email
        # send_email(to="admin@example.com", subject="API Alert", body=message)

    def record_call(self, cost: float):
        """Record API call."""
        self.daily_spent += cost
        self.check_and_alert()

# Usage
monitor = APIMonitor(alert_threshold=75.0)

# After each API call
response = client.chat.completions.create(...)
cost = calculate_cost(response.usage, "gpt-3.5-turbo")
monitor.record_call(cost)
```

```bash
╔════════════════════════════════════════════════════════════╗
║                   COST ESTIMATION TOOL                     ║
╚════════════════════════════════════════════════════════════╝
```

```python
class CostEstimator:
    """
    Estimate costs before making API calls.
    """
    PRICES = {
        'gpt-4': {'input': 0.03, 'output': 0.06},
        'gpt-3.5-turbo': {'input': 0.0005, 'output': 0.0015},
        'claude-opus': {'input': 0.015, 'output': 0.075},
        'claude-sonnet': {'input': 0.003, 'output': 0.015},
    }

    def estimate_tokens(self, text: str) -> int:
        """Rough token estimation."""
        return int(len(text.split()) * 1.3)

    def estimate_cost(self, prompt: str, model: str, max_tokens: int = 500) -> dict:
        """
        Estimate cost for API call.
        """
        input_tokens = self.estimate_tokens(prompt)
        output_tokens = max_tokens

        prices = self.PRICES.get(model, self.PRICES['gpt-3.5-turbo'])

        input_cost = (input_tokens * prices['input']) / 1000
        output_cost = (output_tokens * prices['output']) / 1000
        total_cost = input_cost + output_cost

        return {
            'estimated_input_tokens': input_tokens,
            'estimated_output_tokens': output_tokens,
            'estimated_total_tokens': input_tokens + output_tokens,
            'estimated_cost': total_cost,
            'cost_breakdown': {
                'input': input_cost,
                'output': output_cost
            }
        }

    def compare_models(self, prompt: str, max_tokens: int = 500) -> dict:
        """Compare costs across models."""
        comparisons = {}

        for model in self.PRICES:
            estimate = self.estimate_cost(prompt, model, max_tokens)
            comparisons[model] = estimate['estimated_cost']

        return comparisons

# Usage
estimator = CostEstimator()

prompt = "Explain quantum computing in detail"
estimate = estimator.estimate_cost(prompt, "gpt-4", max_tokens=1000)

print(f"Estimated cost: ${estimate['estimated_cost']:.6f}")
print(f"Estimated tokens: {estimate['estimated_total_tokens']}")

# Compare models
comparison = estimator.compare_models(prompt)
print("\nCost comparison:")
for model, cost in sorted(comparison.items(), key=lambda x: x[1]):
    print(f"{model}: ${cost:.6f}")
```

---

<div align="center">

## 🚀 Real-World Applications

</div>

### Building with AI APIs 💼

```python
# ═══════════════════════════════════════════
# REAL-WORLD APPLICATION EXAMPLES
# ═══════════════════════════════════════════

print("="*60)
print("REAL-WORLD APPLICATIONS")
print("="*60)

# ═══════════════════════════════════════════
# APPLICATION 1: AI CHATBOT
# ═══════════════════════════════════════════

"""
Complete chatbot implementation with:
- Conversation history
- Context management
- Cost tracking
- Error handling
"""

class AIChatbot:
    """
    Production-ready AI chatbot.
    """
    def __init__(self, system_prompt: str = "You are a helpful assistant."):
        self.system_prompt = system_prompt
        self.conversations = {}  # user_id -> messages
        self.cost_tracker = CostTracker()

    def get_conversation(self, user_id: str) -> list:
        """Get conversation history."""
        if user_id not in self.conversations:
            self.conversations[user_id] = [
                {"role": "system", "content": self.system_prompt}
            ]
        return self.conversations[user_id]

    def chat(self, user_id: str, message: str) -> dict:
        """
        Send message and get response.
        """
        # Validate input
        if not validate_input(message):
            return {"error": "Invalid input"}

        # Sanitize
        sanitized = sanitize_input(message)

        # Get conversation
        messages = self.get_conversation(user_id)
        messages.append({"role": "user", "content": sanitized})

        # Limit context (keep last 10 messages)
        if len(messages) > 21:  # 1 system + 10 pairs
            messages = [messages[0]] + messages[-20:]

        try:
            # API call with retry
            response = retry_with_exponential_backoff(
                lambda: client.chat.completions.create(
                    model="gpt-3.5-turbo",
                    messages=messages,
                    max_tokens=500,
                    temperature=0.7
                )
            )()

            # Extract response
            assistant_message = response.choices[0].message.content
            messages.append({"role": "assistant", "content": assistant_message})

            # Track cost
            self.cost_tracker.track_call(response.usage)

            return {
                "response": assistant_message,
                "tokens": response.usage.total_tokens,
                "cost": calculate_cost(response.usage, "gpt-3.5-turbo")
            }

        except Exception as e:
            logger.error(f"Chatbot error: {e}")
            return {"error": "Failed to generate response"}

    def reset_conversation(self, user_id: str):
        """Clear conversation history."""
        if user_id in self.conversations:
            del self.conversations[user_id]

    def get_stats(self) -> dict:
        """Get usage statistics."""
        return self.cost_tracker.report()

# Usage
bot = AIChatbot(system_prompt="You are a helpful customer service assistant.")

response = bot.chat("user123", "How do I reset my password?")
print(response['response'])

response = bot.chat("user123", "What if I don't have access to my email?")
print(response['response'])

print("\nStats:", bot.get_stats())

# ═══════════════════════════════════════════
# APPLICATION 2: CONTENT GENERATOR
# ═══════════════════════════════════════════

"""
Automated content generation system
"""

class ContentGenerator:
    """
    Generate various types of content.
    """
    def __init__(self):
        self.templates = {
            'blog_post': """Write a blog post about {topic}.
                Include: introduction, 3 main points, conclusion.
                Tone: {tone}
                Length: {length} words""",

            'social_media': """Create a {platform} post about {topic}.
                Tone: {tone}
                Include relevant hashtags.""",

            'email': """Write a {email_type} email about {topic}.
                Tone: {tone}
                Include subject line.""",
        }

    def generate_blog_post(
        self,
        topic: str,
        tone: str = "professional",
        length: int = 500
    ) -> dict:
        """Generate blog post."""
        prompt = self.templates['blog_post'].format(
            topic=topic,
            tone=tone,
            length=length
        )

        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a professional content writer."},
                {"role": "user", "content": prompt}
            ],
            max_tokens=1500,
            temperature=0.8  # More creative
        )

        content = response.choices[0].message.content

        # Generate SEO metadata
        seo_prompt = f"Generate SEO title, meta description, and 5 keywords for this blog post:\n\n{content[:500]}"

        seo_response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": seo_prompt}],
            max_tokens=200
        )

        return {
            'content': content,
            'seo': seo_response.choices[0].message.content,
            'word_count': len(content.split()),
            'tokens_used': response.usage.total_tokens + seo_response.usage.total_tokens
        }

    def generate_social_post(
        self,
        platform: str,
        topic: str,
        tone: str = "engaging"
    ) -> str:
        """Generate social media post."""
        prompt = self.templates['social_media'].format(
            platform=platform,
            topic=topic,
            tone=tone
        )

        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=200
        )

        return response.choices[0].message.content

    def generate_variations(self, text: str, num_variations: int = 3) -> list:
        """Generate variations of text."""
        prompt = f"Create {num_variations} variations of this text:\n\n{text}"

        response = client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=500
        )

        return response.choices[0].message.content.split('\n\n')

# Usage
generator = ContentGenerator()

# Generate blog post
blog = generator.generate_blog_post(
    topic="The Future of AI in Healthcare",
    tone="informative",
    length=800
)
print(f"Blog post generated ({blog['word_count']} words)")
print(blog['content'][:200] + "...")

# Generate social posts
tweet = generator.generate_social_post("Twitter", "AI in Healthcare", "exciting")
print(f"\nTweet: {tweet}")

# ═══════════════════════════════════════════
# APPLICATION 3: DOCUMENT ANALYZER
# ═══════════════════════════════════════════

"""
Analyze and extract insights from documents
"""

class DocumentAnalyzer:
    """
    Analyze documents using AI.
    """
    def __init__(self):
        self.client = OpenAI()

    def summarize(self, text: str, length: str = "short") -> str:
        """
        Summarize document.

        length: short (1 paragraph), medium (3 paragraphs), long (detailed)
        """
        length_instructions = {
            'short': 'one paragraph',
            'medium': 'three paragraphs',
            'long': 'comprehensive summary with key points'
        }

        prompt = f"Summarize this text in {length_instructions[length]}:\n\n{text}"

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=500 if length == 'short' else 1000
        )

        return response.choices[0].message.content

    def extract_key_points(self, text: str, num_points: int = 5) -> list:
        """Extract key points from text."""
        prompt = f"Extract {num_points} key points from this text:\n\n{text}"

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=300
        )

        # Parse bullet points
        content = response.choices[0].message.content
        points = [line.strip('- ').strip() for line in content.split('\n') if line.strip()]
        return points

    def sentiment_analysis(self, text: str) -> dict:
        """Analyze sentiment of text."""
        prompt = f"""Analyze the sentiment of this text.
        Provide:
        1. Overall sentiment (positive/negative/neutral)
        2. Confidence score (0-1)
        3. Key emotions detected

        Text: {text}"""

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=200,
            temperature=0.3  # More consistent
        )

        return {'analysis': response.choices[0].message.content}

    def extract_entities(self, text: str) -> dict:
        """Extract named entities (people, places, organizations)."""
        prompt = f"""Extract named entities from this text.
        Format as JSON with categories: people, places, organizations, dates.

        Text: {text}"""

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=300
        )

        try:
            import json
            return json.loads(response.choices[0].message.content)
        except:
            return {'raw': response.choices[0].message.content}

    def translate(self, text: str, target_language: str) -> str:
        """Translate text to target language."""
        prompt = f"Translate this text to {target_language}:\n\n{text}"

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[{"role": "user", "content": prompt}],
            max_tokens=len(text.split()) * 2  # Account for expansion
        )

        return response.choices[0].message.content

# Usage
analyzer = DocumentAnalyzer()

document = """
Artificial intelligence is rapidly transforming healthcare.
From diagnostic tools to personalized treatment plans, AI is
helping doctors make better decisions and improving patient outcomes.
"""

# Summarize
summary = analyzer.summarize(document, length="short")
print(f"Summary: {summary}")

# Extract key points
points = analyzer.extract_key_points(document, num_points=3)
print(f"\nKey points: {points}")

# Sentiment
sentiment = analyzer.sentiment_analysis(document)
print(f"\nSentiment: {sentiment}")

# ═══════════════════════════════════════════
# APPLICATION 4: IMAGE DESCRIPTION BOT
# ═══════════════════════════════════════════

"""
Analyze images and generate descriptions
"""

class ImageAnalyzer:
    """
    Analyze images with vision APIs.
    """
    def __init__(self):
        self.client = OpenAI()

    def describe_image(self, image_path: str, detail_level: str = "auto") -> dict:
        """
        Generate description of image.

        detail_level: low, high, auto
        """
        import base64

        # Read and encode image
        with open(image_path, "rb") as image_file:
            base64_image = base64.b64encode(image_file.read()).decode('utf-8')

        response = self.client.chat.completions.create(
            model="gpt-4-vision-preview",
            messages=[
                {
                    "role": "user",
                    "content": [
                        {"type": "text", "text": "Describe this image in detail."},
                        {
                            "type": "image_url",
                            "image_url": {
                                "url": f"data:image/jpeg;base64,{base64_image}",
                                "detail": detail_level
                            }
                        }
                    ]
                }
            ],
            max_tokens=500
        )

        return {
            'description': response.choices[0].message.content,
            'tokens': response.usage.total_tokens
        }

    def generate_alt_text(self, image_path: str) -> str:
        """Generate accessibility alt text for image."""
        import base64

        with open(image_path, "rb") as image_file:
            base64_image = base64.b64encode(image_file.read()).decode('utf-8')

        response = self.client.chat.completions.create(
            model="gpt-4-vision-preview",
            messages=[
                {
                    "role": "user",
                    "content": [
                        {
                            "type": "text",
                            "text": "Generate concise alt text for this image (max 125 characters)."
                        },
                        {
                            "type": "image_url",
                            "image_url": {
                                "url": f"data:image/jpeg;base64,{base64_image}"
                            }
                        }
                    ]
                }
            ],
            max_tokens=100
        )

        return response.choices[0].message.content

    def answer_about_image(self, image_path: str, question: str) -> str:
        """Answer questions about an image."""
        import base64

        with open(image_path, "rb") as image_file:
            base64_image = base64.b64encode(image_file.read()).decode('utf-8')

        response = self.client.chat.completions.create(
            model="gpt-4-vision-preview",
            messages=[
                {
                    "role": "user",
                    "content": [
                        {"type": "text", "text": question},
                        {
                            "type": "image_url",
                            "image_url": {
                                "url": f"data:image/jpeg;base64,{base64_image}"
                            }
                        }
                    ]
                }
            ],
            max_tokens=300
        )

        return response.choices[0].message.content

# Usage
# image_analyzer = ImageAnalyzer()
# description = image_analyzer.describe_image("photo.jpg")
# print(description['description'])

# ═══════════════════════════════════════════
# APPLICATION 5: VOICE ASSISTANT
# ═══════════════════════════════════════════

"""
Complete voice assistant with speech recognition and synthesis
"""

class VoiceAssistant:
    """
    Voice-enabled AI assistant.
    """
    def __init__(self):
        self.client = OpenAI()
        self.conversation_history = []

    def listen(self, audio_file_path: str) -> str:
        """
        Convert speech to text.
        """
        with open(audio_file_path, "rb") as audio_file:
            transcript = self.client.audio.transcriptions.create(
                model="whisper-1",
                file=audio_file,
                language="en"
            )
        return transcript.text

    def think(self, user_input: str) -> str:
        """
        Process input and generate response.
        """
        self.conversation_history.append({
            "role": "user",
            "content": user_input
        })

        response = self.client.chat.completions.create(
            model="gpt-3.5-turbo",
            messages=[
                {"role": "system", "content": "You are a helpful voice assistant. Keep responses concise."}
            ] + self.conversation_history,
            max_tokens=150
        )

        assistant_message = response.choices[0].message.content
        self.conversation_history.append({
            "role": "assistant",
            "content": assistant_message
        })

        return assistant_message

    def speak(self, text: str, output_path: str = "response.mp3") -> str:
        """
        Convert text to speech.
        """
        response = self.client.audio.speech.create(
            model="tts-1",
            voice="nova",
            input=text
        )

        response.stream_to_file(output_path)
        return output_path

    def process_voice_input(self, audio_input_path: str) -> dict:
        """
        Complete voice interaction: listen -> think -> speak
        """
        # Speech to text
        user_text = self.listen(audio_input_path)
        print(f"User said: {user_text}")

        # Generate response
        response_text = self.think(user_text)
        print(f"Assistant: {response_text}")

        # Text to speech
        audio_output = self.speak(response_text)

        return {
            'user_text': user_text,
            'response_text': response_text,
            'audio_output': audio_output
        }

# Usage
# assistant = VoiceAssistant()
# result = assistant.process_voice_input("user_recording.mp3")
# Play result['audio_output']

print("\n✅ Real-World Applications Complete")
```

---

<div align="center">

## 📚 Resources & Learning

</div>

### Continue Your AI API Journey 🚀

```
📘 Official Documentation
   • OpenAI API: https://platform.openai.com/docs
   • Anthropic Claude: https://docs.anthropic.com/
   • Google AI: https://ai.google.dev/
   • Hugging Face: https://huggingface.co/docs
   • Stability AI: https://platform.stability.ai/docs

📗 Tutorials & Guides
   • OpenAI Cookbook: https://cookbook.openai.com/
   • LangChain Docs: https://python.langchain.com/
   • Prompt Engineering Guide: https://www.promptingguide.ai/
   • AI Engineer Roadmap: https://roadmap.sh/ai-engineer

📙 API Playgrounds
   • OpenAI Playground: https://platform.openai.com/playground
   • Claude Chat: https://claude.ai/
   • Hugging Face Spaces: https://huggingface.co/spaces
   • Google AI Studio: https://makersuite.google.com/

🎥 Video Resources
   • OpenAI Developer Day
   • Anthropic YouTube Channel
   • AI Explained (YouTube)
   • Two Minute Papers

💡 Blogs & Newsletters
   • OpenAI Blog: https://openai.com/blog
   • Anthropic Blog: https://www.anthropic.com/news
   • The Batch (deeplearning.ai)
   • AI Breakdown Newsletter

🛠️ Tools & Libraries
   • LangChain: Framework for LLM apps
   • LlamaIndex: Data framework for LLMs
   • Semantic Kernel: Microsoft's SDK
   • Haystack: NLP framework
   • AutoGPT: Autonomous AI agents

💬 Communities
   • OpenAI Developer Forum
   • r/MachineLearning
   • r/OpenAI
   • AI Discord servers
   • Hugging Face Forums

📊 Cost Calculators
   • OpenAI Pricing Calculator
   • Claude API Pricing
   • Token Counter Tools
   • AI Cost Comparison Sites

🔧 Development Tools
   • Postman: API testing
   • Insomnia: API client
   • Bruno: Open-source API client
   • Cursor: AI-native IDE

📖 Books
   • "Building LLM Apps" (various authors)
   • "Prompt Engineering" guides
   • "AI API Integration" tutorials
   • Platform-specific cookbooks

🎓 Courses
   • OpenAI API Course (DeepLearning.AI)
   • LangChain Course
   • Full Stack LLM Bootcamp
   • AI Engineering courses
```

---

<div align="center">

## 🎯 Summary

</div>

### Key Takeaways 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   REMEMBER                                 ║
╚════════════════════════════════════════════════════════════╝

1. Choose the Right API
   • Text: OpenAI, Claude, Gemini
   • Images: DALL-E, Stable Diffusion
   • Speech: Whisper, ElevenLabs
   • Multi-modal: GPT-4V, Gemini Pro Vision

2. Optimize Costs
   • Use cheaper models when possible (GPT-3.5 vs GPT-4)
   • Cache responses
   • Batch requests
   • Monitor spending
   • Set budget limits

3. Security First
   • Never hardcode API keys
   • Use environment variables
   • Validate & sanitize inputs
   • Filter sensitive outputs
   • Monitor for abuse

4. Best Practices
   • Implement retry logic
   • Add rate limiting
   • Handle errors gracefully
   • Log API calls
   • Track costs
   • Monitor performance

5. User Experience
   • Use streaming for real-time feel
   • Show loading states
   • Handle errors elegantly
   • Provide fallbacks
   • Cache when possible

6. Production Ready
   • Error handling
   • Monitoring & alerting
   • Cost tracking
   • Rate limiting
   • Security measures
   • Testing

"AI APIs are the building blocks of the next generation of apps.
Choose wisely, optimize aggressively, and build responsibly." 🚀

═══════════════════════════════════════════════════════════

Quick Decision Guide:
─────────────────────────────────────────────────────────────

Need text generation?
  → Start with OpenAI GPT-3.5 (fast, cheap)
  → Upgrade to GPT-4 for complex tasks
  → Use Claude for long documents (200K context)

Need images?
  → DALL-E 3 for highest quality
  → Stable Diffusion for customization
  → Leonardo.ai for game assets

Need speech?
  → Whisper for transcription (best accuracy)
  → ElevenLabs for TTS (most natural)
  → OpenAI TTS for affordable TTS

Need multimodal?
  → GPT-4V for vision + language
  → Gemini Pro Vision for Google ecosystem

Budget conscious?
  → Gemini Pro (free tier)
  → Hugging Face (many free models)
  → GPT-3.5 (most affordable commercial)

Enterprise needs?
  → Azure OpenAI (SLA, support)
  → AWS Bedrock (AWS integration)
  → Google Vertex AI (GCP integration)

═══════════════════════════════════════════════════════════

Cost-Saving Tips:
─────────────────────────────────────────────────────────────
✅ Use GPT-3.5 instead of GPT-4 when possible (40x cheaper!)
✅ Cache responses (Redis/memcached)
✅ Compress prompts
✅ Batch multiple requests
✅ Set max_tokens limits
✅ Use streaming (better UX, same cost)
✅ Monitor and alert on spending
✅ Use free tiers for development
✅ Implement proper error handling (avoid wasted calls)
✅ Choose right model for task complexity

Security Checklist:
─────────────────────────────────────────────────────────────
☐ API keys in environment variables
☐ Input validation implemented
☐ Output filtering for sensitive data
☐ Rate limiting enabled
☐ Budget limits set
☐ Monitoring & alerts configured
☐ Error handling implemented
☐ Logging for audit trail
☐ Content moderation (if user-generated)
☐ Regular security audits

Performance Optimization:
─────────────────────────────────────────────────────────────
☐ Use streaming for better UX
☐ Cache frequent requests
☐ Implement retry with backoff
☐ Use connection pooling
☐ Minimize prompt size
☐ Batch when possible
☐ Choose optimal model
☐ Set appropriate timeouts
☐ Monitor latency
☐ Use CDN for assets

Production Launch Checklist:
─────────────────────────────────────────────────────────────
☐ API keys secured
☐ Error handling complete
☐ Rate limiting implemented
☐ Cost tracking enabled
☐ Monitoring & alerts set up
☐ Logging configured
☐ Backup plan for API failures
☐ User feedback mechanism
☐ Documentation complete
☐ Load testing done
☐ Security review passed
☐ Budget limits configured

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with 🌐 by MrDib, for AI developers**

_Remember: "The best AI API is the one that solves your problem efficiently and cost-effectively!"_ ✨

**Happy Building!** 🚀

</div>

---

### 🔗 Related Guides

- [AI Coding Assistants](./AI-Coding-Assistants.md)
- [ML Frameworks](../Machine-Learning/ML-Frameworks.md)
- [ML Platforms](../Machine-Learning/ML-Platforms.md)
- [Python Development](../../Development/Languages/Python.md)

---

<div align="center">

### 📊 API Comparison At-a-Glance

| Category             | Best Choice   | Runner-up         | Budget Option    |
| -------------------- | ------------- | ----------------- | ---------------- |
| **Text Generation**  | GPT-4         | Claude Opus       | GPT-3.5          |
| **Chat**             | GPT-3.5 Turbo | Claude Sonnet     | Gemini Pro       |
| **Long Context**     | Claude (200K) | GPT-4 Turbo       | Gemini Pro       |
| **Image Generation** | DALL-E 3      | Midjourney        | Stable Diffusion |
| **Speech-to-Text**   | Whisper       | AssemblyAI        | Google STT       |
| **Text-to-Speech**   | ElevenLabs    | OpenAI TTS        | Google TTS       |
| **Vision**           | GPT-4V        | Gemini Pro Vision | Claude 3         |
| **Embeddings**       | OpenAI Ada    | Cohere            | HuggingFace      |
| **Translation**      | GPT-4         | Claude            | Google Translate |

---

### 💰 Typical Monthly Costs

| Usage Level    | Estimated Cost | Recommended Stack                        |
| -------------- | -------------- | ---------------------------------------- |
| **Hobby**      | $0-10          | Free tiers (Gemini, HF) + GPT-3.5        |
| **Small App**  | $10-100        | GPT-3.5 + Whisper + Stable Diffusion     |
| **Medium App** | $100-500       | GPT-4 (limited) + GPT-3.5 + Premium APIs |
| **Large App**  | $500-5000      | GPT-4 + Claude + Enterprise APIs         |
| **Enterprise** | $5000+         | Azure OpenAI + AWS Bedrock + Custom      |

</div>

---
