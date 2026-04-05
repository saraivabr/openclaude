# Início Rápido do OpenClaude para Windows

Este guia usa o **Windows PowerShell**.

> **Dica:** Procure "PowerShell" no Menu Iniciar para abri-lo.

---

## Passo 1: Instalar o Node.js

Instale o Node.js 20 ou mais recente em:

- `https://nodejs.org/`

Depois, abra o PowerShell e verifique:

```powershell
node --version
npm --version
```

Você deverá ver algo como `v20.x.x` e `10.x.x`. Se aparecer um erro, reinicie o PowerShell e tente novamente.

---

## Passo 2: Instalar o OpenClaude

```powershell
npm install -g @gitlawb/openclaude
```

> O `-g` significa instalação global — o comando `openclaude` ficará disponível em qualquer pasta do PowerShell.

---

## Passo 3: Escolha um Provedor

Escolha **apenas uma** das opções abaixo:

---

### Opção A: OpenAI

> **Quando usar:** Você tem uma chave de API da OpenAI e quer a configuração mais simples.

Substitua `sk-sua-chave-aqui` pela sua chave real.

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_API_KEY="sk-sua-chave-aqui"
$env:OPENAI_MODEL="gpt-4o"

openclaude
```

---

### Opção B: DeepSeek

> **Quando usar:** Você quer um modelo alternativo ao OpenAI com API compatível.

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_API_KEY="sk-sua-chave-aqui"
$env:OPENAI_BASE_URL="https://api.deepseek.com/v1"
$env:OPENAI_MODEL="deepseek-chat"

openclaude
```

---

### Opção C: Ollama (modelo local, sem API)

> **Quando usar:** Você quer rodar um modelo **localmente** sem pagar por tokens de API.

Primeiro, instale o Ollama para Windows:

- `https://ollama.com/download/windows`

Depois, baixe um modelo e inicie o OpenClaude:

```powershell
ollama pull llama3.1:8b

$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_BASE_URL="http://localhost:11434/v1"
$env:OPENAI_MODEL="llama3.1:8b"

openclaude
```

> Nenhuma chave de API é necessária para modelos locais do Ollama.

---

### Opção D: LM Studio (modelo local, sem API)

> **Quando usar:** Você prefere uma interface gráfica para gerenciar modelos locais.

Primeiro, instale o LM Studio:

- `https://lmstudio.ai/`

Depois, dentro do LM Studio:

1. Baixe um modelo (ex.: Llama 3.1 8B, Mistral 7B)
2. Vá para a aba **"Developer"**
3. Selecione seu modelo e ative o servidor pelo botão de toggle

Então execute:

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_BASE_URL="http://localhost:1234/v1"
$env:OPENAI_MODEL="nome-do-seu-modelo"
# $env:OPENAI_API_KEY="lmstudio"  # opcional: alguns usuários precisam de uma chave fictícia

openclaude
```

Substitua `nome-do-seu-modelo` pelo nome do modelo exibido no LM Studio.

> Nenhuma chave de API é necessária para modelos locais do LM Studio (mas descomente a linha `OPENAI_API_KEY` se encontrar erros de autenticação).

---

## Passo 4: E se o comando `openclaude` não for encontrado?

Feche o PowerShell, abra um novo e tente novamente:

```powershell
openclaude
```

---

## Passo 5: E se o provedor falhar?

### Para OpenAI ou DeepSeek

- verifique se a chave de API é válida
- verifique se você copiou a chave completamente

### Para Ollama

- verifique se o Ollama está instalado
- verifique se o Ollama está em execução
- verifique se o modelo foi baixado com sucesso (`ollama list`)

### Para LM Studio

- verifique se o LM Studio está instalado
- verifique se o LM Studio está em execução
- verifique se o servidor está ativado (toggle na aba "Developer")
- verifique se um modelo está carregado no LM Studio
- verifique se o nome do modelo bate com o que você definiu em `OPENAI_MODEL`

---

## Passo 6: Atualizar o OpenClaude

```powershell
npm install -g @gitlawb/openclaude@latest
```

---

## Passo 7: Desinstalar o OpenClaude

```powershell
npm uninstall -g @gitlawb/openclaude
```

---

## Precisa de Configuração Avançada?

Use:

- [Configuração Avançada](configuracao-avancada.md)
