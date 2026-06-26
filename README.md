# AI_Workflows-Ornith-1.0
How to run the new Ornith-1.0 models locally.

I tested this on a MacBook Air M4 16GB RAM. For that reason I used the 9B model with Q4_K_M quantization (~5.6GB, fits comfortably).
The process is the same for the other models, just swap in the correct name.

### Ollama

Install ollama:
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Pull and run the model in one step (Ollama downloads it automatically the first time):
```bash
ollama run hf.co/deepreinforce-ai/Ornith-1.0-9B-GGUF:Q4_K_M
```

Run `ollama list` to see installed models and find the exact name.

### Using it in opencode

Note: if you have low memory, opencode might struggle, since it loads a large context into RAM on top of the model.

Add the model to `opencode.json`:
```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama (local)",
      "options": {
        "baseURL": "http://localhost:11434/v1"
      },
      "models": {
        "hf.co/deepreinforce-ai/Ornith-1.0-9B-GGUF:Q4_K_M": {
          "name": "Ornith 1.0 9B Q4"
        }
      }
    }
  }
}
```

Then run opencode and select the model.