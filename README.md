# Pax Historia: Custom AI Backend Hook

Tampermonkey userscript that replaces **Pax Historia**'s default AI backend with multiple providers. Use your own API keys or local proxies (Ollama, LM Studio, Copilot API) for AI chats and actions.

## Supported Providers

| Provider | API Key | Description |
|----------|---------|-------------|
| **Google AI Studio** | Yes | Gemini (including Thinking models) |
| **OpenRouter** | Yes | Multiple models via [openrouter.ai](https://openrouter.ai) |
| **OpenAI** | Yes | Direct OpenAI API (GPT-4, etc.) |
| **Groq** | Yes | Fast inference, free tier available |
| **Ollama** | No | Local models at `http://localhost:11434` |
| **LM Studio** | No | Local models at `http://localhost:1234` |
| **Together AI** | Yes | Open and fine-tuned models |
| **Fireworks AI** | Yes | Fast inference API |
| **Mistral AI** | Yes | Mistral models |
| **Anthropic (Claude)** | Yes | Claude models |
| **Copilot API** | No | Local proxy via [copilot-api](https://github.com/caozhiyuan/copilot-api) |
| **Generic** | Optional | Any OpenAI-compatible API (custom Base URL) |

## Features

- **12 providers**: Google, OpenRouter, OpenAI, Groq, Ollama, LM Studio, Together, Fireworks, Mistral, Anthropic, Copilot, Generic
- **Connection test**: Verifies Base URL for Copilot, LM Studio, Ollama, Generic before saving
- **Model selector**: Auto-loads models from local proxies (Copilot, LM Studio)
- **Thinking Budget**: Configurable for Gemini models
- **Indicator badge**: Shows current provider and model in the header (click to open settings)
- **Privacy**: Prompts go to your chosen provider, not the game's default backend

## Installation

1. Install **Tampermonkey** in your browser (Chrome, Firefox, Edge).
2. Create a new script in Tampermonkey.
3. Copy and paste the contents of `PaxHistoriaAIHook.user.js`.
4. Save (Ctrl+S).

## Configuration

1. Open [Pax Historia](https://paxhistoria.co).
2. Click **Tampermonkey** icon and select **"Open AI Settings"**, or click the indicator badge in the header.
3. Choose provider and configure:

### Google AI Studio
- **API Key**: [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
- **Model**: e.g. `gemini-3-flash-preview`
- **Thinking Budget**: 4096 (recommended)

### OpenRouter
- **API Key**: [openrouter.ai/keys](https://openrouter.ai/keys)
- **Model**: e.g. `google/gemini-2.0-flash-thinking-exp:free`

### OpenAI / Groq / Together / Fireworks / Mistral / Anthropic
- **API Key**: From each provider's dashboard
- **Model**: Provider-specific model ID

### Ollama / LM Studio (local)
- **Base URL**: `http://localhost:11434` (Ollama) or `http://localhost:1234` (LM Studio)
- **Model**: Name of loaded model. Use "Test" to list available models (LM Studio).

### Copilot API (no API key)
- **Provider**: Copilot API (local)
- **Base URL**: `http://localhost:4141` 
(default). The [copilot-api](https://github.com/
caozhiyuan/copilot-api) proxy must be running.
- **Model**: Use "Test connection" to load 
models and select one (e.g. `gpt-4.1`, 
`claude-opus-4.6`).

### Generic (OpenAI-compatible)
- **Base URL**: e.g. `https://api.openai.com/v1` or Azure/custom endpoint
- **Model**: Model ID
- **API Key (optional)**: Leave empty for local or public endpoints

5. Save and reload the page.

## Troubleshooting

- **"No events" error**: Model did not return valid JSON. Try a more capable model or increase thinking budget.
- **Network error**: Check Base URL and that the proxy (Ollama, LM Studio, Copilot) is running.
- **Script not loading**: Ensure Tampermonkey has the required permissions (`GM_xmlhttpRequest`, `@connect *`).
- **API errors**: Check browser console (F12) for `[PAX AI]` logs.

## Troubleshooting

- **"No events" error**: The model did not return valid JSON. Try a more capable model or increase the thinking budget.
- **Copilot API: Network error or no connection**: Ensure the proxy is running (`npx copilot-api@latest start`) and the Base URL is correct.
- **Script not working**: Check that the script is enabled in Tampermonkey and that you have accepted the requested permissions (including `GM_xmlhttpRequest` for Copilot API).
- **API errors**: Check the browser console (F12) for logs tagged with `[PAX AI]`.

## Disclaimer

This script is for educational and personal use only. Use at your own risk.