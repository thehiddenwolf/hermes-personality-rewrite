# hermes-personality-rewrite

A Hermes agent plugin that intercepts final LLM outputs using the `transform_llm_output` hook and refines them using a smaller local LLM (such as Llama-3.1 8B or Gemma 2 9B) to fit the agent's personality anchor and purge AI slopisms.

## Installation

Clone this repository into your Hermes plugins directory:

```bash
cd ~/.hermes/plugins/
git clone https://github.com/thehiddenwolf/hermes-personality-rewrite.git personality-rewrite
```

Then enable it in your `~/.hermes/config.yaml` file:

```yaml
plugins:
  enabled:
    - personality-rewrite
```

## Configuration

Add the following task configuration under the `auxiliary:` block of your `~/.hermes/config.yaml`:

```yaml
auxiliary:
  personality_rewrite:
    provider: ollama-cloud # or ollama, openrouter, etc.
    model: deepseek-v4-flash # or llama3.1:8b-instruct-fp16, gemma2:9b-instruct-fp16, etc.
    base_url: 'http://127.0.0.1:11435' # point to your local 4090 Ollama server if running locally
    api_key: ''
    timeout: 30
    extra_body: {}
```
