# OpenClaude para Usuários Não-Técnicos

Este guia é para quem quer o caminho de configuração mais fácil possível.

Você **não** precisa:
- compilar o código-fonte
- instalar o Bun
- entender toda a base de código

Se você consegue copiar e colar comandos em um terminal, você consegue configurar isso.

---

## O que o OpenClaude faz?

O OpenClaude permite que você use um **assistente de codificação com IA** a partir do seu terminal, conectando-se a diferentes provedores de modelos, como:

- **OpenAI** (GPT-4o, etc.)
- **DeepSeek**
- **Gemini** (Google)
- **Ollama** (modelos locais, sem precisar de internet)
- **Codex**

> Para a maioria dos usuários iniciantes, **OpenAI é a opção mais fácil** para começar.

---

## Antes de Começar

Você vai precisar de:

1. **Node.js 20 ou mais recente** instalado no seu computador — [baixe aqui](https://nodejs.org/)
2. Uma **janela de terminal** aberta (Prompt de Comando, PowerShell, Terminal, etc.)
3. Uma **chave de API do seu provedor** — a menos que você vá usar um modelo local como o Ollama

---

## Caminho Mais Rápido (resumo)

1. Instale o OpenClaude com npm
2. Defina 3 variáveis de ambiente
3. Execute `openclaude`

> Não sabe o que são "variáveis de ambiente"? Sem problema — os guias abaixo mostram o passo a passo exato.

---

## Escolha seu Sistema Operacional

- **Windows:** [Início Rápido para Windows](inicio-rapido-windows.md)
- **macOS / Linux:** [Início Rápido para macOS / Linux](inicio-rapido-mac-linux.md)

---

## Qual Provedor Devo Escolher?

### OpenAI

Escolha este se:

- você quer a configuração mais fácil
- você já tem uma chave de API da OpenAI

> Você pode obter uma chave de API em [platform.openai.com](https://platform.openai.com).

---

### Ollama

Escolha este se:

- você quer rodar modelos **localmente** no seu computador
- você não quer depender de uma API em nuvem para testes
- você não quer pagar por tokens de API

> Baixe o Ollama em [ollama.com/download](https://ollama.com/download).

---

### Codex

Escolha este se:

- você já usa o Codex CLI
- você já tem autenticação do Codex ou ChatGPT configurada

---

## Como Saber se Funcionou?

Após executar `openclaude`, a CLI deve iniciar e aguardar o seu prompt.

Nesse ponto, você pode pedir para ela:

- explicar código
- editar arquivos
- executar comandos
- revisar mudanças

---

## Problemas Comuns

### Erro: `openclaude: command not found`

**Causa:** O npm instalou o pacote, mas o seu terminal ainda não foi atualizado.

**Solução:**

1. Feche o terminal atual
2. Abra um novo terminal
3. Execute `openclaude` novamente

---

### Erro: Chave de API inválida

**Causa:** A chave está errada, expirada ou foi copiada incorretamente.

**Solução:**

1. Obtenha uma chave nova no site do seu provedor
2. Cole-a novamente com cuidado
3. Execute `openclaude` novamente

---

### Ollama não está funcionando

**Causa:** O Ollama não está instalado ou não está em execução.

**Solução:**

1. Instale o Ollama em `https://ollama.com/download`
2. Inicie o Ollama
3. Tente novamente

---

## Quer Mais Controle?

Se você quer builds a partir do fonte, perfis avançados de provedor, diagnósticos ou fluxos de trabalho baseados em Bun, use:

- [Configuração Avançada](configuracao-avancada.md)
