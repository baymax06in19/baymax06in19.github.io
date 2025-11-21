Connecting With Large Language Models (LLMs)

Large Language Models (LLMs) such as GPT, Qwen, Llama, and Mistral can be accessed through APIs, self-hosted servers, or cloud providers.
This guide explains the common methods, how they work, and how to get started.

🧠 What Is an LLM?

A Large Language Model (LLM) is an AI system trained to understand and generate human language.
LLMs can perform tasks such as:

answering questions

writing code

summarizing text

translating languages

generating content

creating chatbots

Connecting to an LLM usually means sending text input and receiving text output using an API.

🔌 Ways to Connect to an LLM
1. Cloud Providers (Hosted LLMs)

Many platforms host LLMs and provide an API you can call:

OpenAI

Anthropic

Google Gemini

Alibaba Qwen

Meta Llama via providers like Together, Fireworks, Groq

HuggingFace Inference API

These services typically require:

an API key

using the provider’s URL

specifying the model you want to use

Example (OpenAI-compatible)
from openai import OpenAI

client = OpenAI(api_key="YOUR_API_KEY")

response = client.chat.completions.create(
    model="gpt-4.1",
    messages=[{"role": "user", "content": "Hello!"}]
)

print(response.choices[0].message["content"])

2. Self-Hosted LLM Servers

You can run your own models locally or on a server using tools like:

Ollama

LM Studio

vLLM

Text Generation WebUI

OpenAI-compatible gateways

Self-hosting lets you:

avoid API costs

run custom models

use private data safely

Example (OpenAI-compatible local server)
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:8000/v1",
    api_key="none"
)

response = client.chat.completions.create(
    model="qwen2.5-coder",
    messages=[{"role": "user", "content": "Write a Python function."}]
)

print(response.choices[0].message["content"])

3. Browser-Based or Embedded LLMs

You can also run small models directly in the browser using:

WebGPU

TinyLlama, WebLLM

Transformers.js

These models are lightweight but run fully client-side, with no server needed.

🧱 Structure of an LLM Request

Most LLM APIs share a similar structure:

1. URL (endpoint)

Examples:

https://api.openai.com/v1/chat/completions

http://localhost:8000/v1/chat/completions

2. Model

Example: "gpt-4.1" or "qwen2.5:7b"

3. Messages

A conversation formatted like:

[
  { "role": "user", "content": "Hello!" },
  { "role": "assistant", "content": "Hi there!" }
]

4. Your API key

Some servers may disable authentication
