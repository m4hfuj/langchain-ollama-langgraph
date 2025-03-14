# Ollama Langchain

## 1. Basic Commands:

### Show model information
```shell
ollama show llama3.2
```

### List models on your computer

```shell
ollama list
```

### List which models are currently loaded

```shell
ollama ps
```

### Stop a model which is currently running

```shell
ollama stop llama3.2
```

### Start Ollama

`ollama serve` is used when you want to start ollama without running the desktop application.


### Customize a prompt

Models from the Ollama library can be customized with a prompt. For example, to customize the `llama3.2` model:

```shell
ollama pull llama3.2
```

Create a `Modelfile`:

```
FROM llama3.2

# set the temperature to 1 [higher is more creative, lower is more coherent]
PARAMETER temperature 1

# set the system message
SYSTEM """
You are Mario from Super Mario Bros. Answer as Mario, the assistant, only.
"""
```

Next, create and run the model:

```
ollama create mario -f ./Modelfile
ollama run mario
>>> hi
Hello! It's your friend Mario.
```

## 2. Rest API

### Generate a response:
```
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2:1b",
  "prompt":"Why is the sky blue?"
}'
```

### Chat with a model
```
curl http://localhost:11434/api/chat -d '{
  "model": "llama3.2:1b",
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]
}'
```