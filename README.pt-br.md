# OpenClaude

OpenClaude é uma CLI de agente de codificação de código aberto para provedores de modelos em nuvem e locais.

Use APIs compatíveis com OpenAI, Gemini, GitHub Models, Codex, Ollama, Atomic Chat e outros backends suportados — tudo dentro de um único fluxo de trabalho no terminal: prompts, ferramentas, agentes, MCP, comandos slash e saída em streaming.

[![PR Checks](https://github.com/Gitlawb/openclaude/actions/workflows/pr-checks.yml/badge.svg?branch=main)](https://github.com/Gitlawb/openclaude/actions/workflows/pr-checks.yml)
[![Release](https://img.shields.io/github/v/tag/Gitlawb/openclaude?label=release&color=0ea5e9)](https://github.com/Gitlawb/openclaude/tags)
[![Discussions](https://img.shields.io/badge/discussions-open-7c3aed)](https://github.com/Gitlawb/openclaude/discussions)
[![Security Policy](https://img.shields.io/badge/security-policy-0f766e)](SECURITY.md)
[![License](https://img.shields.io/badge/license-MIT-2563eb)](LICENSE)

> 📖 Você está lendo a versão em **Português (Brasil)**. [Read in English](README.md)

[Início Rápido](#início-rápido) | [Guias de Configuração](#guias-de-configuração) | [Provedores](#provedores-suportados) | [Build a partir do Fonte](#build-a-partir-do-fonte-e-desenvolvimento-local) | [Extensão VS Code](#extensão-vs-code) | [Comunidade](#comunidade)

---

## Por que usar o OpenClaude?

- **Uma única CLI** para APIs em nuvem e backends de modelos locais
- **Salve perfis de provedores** dentro do aplicativo com `/provider`
- **Compatível com vários serviços**: OpenAI, Gemini, GitHub Models, Codex, Ollama, Atomic Chat e outros provedores
- **Fluxos de trabalho de agente de codificação em um só lugar**: bash, ferramentas de arquivo, grep, glob, agentes, tasks, MCP e ferramentas web
- **Extensão VS Code** incluída para integração de lançamento e suporte a temas

---

## Início Rápido

### Instalação

> **Pré-requisito:** Node.js 20 ou mais recente. [Baixe aqui](https://nodejs.org/).

```bash
npm install -g @gitlawb/openclaude
```

> Se após a instalação aparecer a mensagem `ripgrep not found`, instale o ripgrep no seu sistema e verifique se `rg --version` funciona no terminal antes de iniciar o OpenClaude.

### Iniciando

```bash
openclaude
```

Dentro do OpenClaude:

- digite `/provider` para configurar e salvar um perfil de provedor
- digite `/onboard-github` para configuração interativa com GitHub Models

---

### Configuração mais rápida com OpenAI

**macOS / Linux:**

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_API_KEY=sk-sua-chave-aqui
export OPENAI_MODEL=gpt-4o

openclaude
```

**Windows PowerShell:**

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_API_KEY="sk-sua-chave-aqui"
$env:OPENAI_MODEL="gpt-4o"

openclaude
```

> Substitua `sk-sua-chave-aqui` pela sua chave real da API OpenAI.

---

### Configuração mais rápida com Ollama (modelo local)

O Ollama permite rodar modelos de IA **localmente**, sem precisar de chave de API.

**macOS / Linux:**

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_BASE_URL=http://localhost:11434/v1
export OPENAI_MODEL=qwen2.5-coder:7b

openclaude
```

**Windows PowerShell:**

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_BASE_URL="http://localhost:11434/v1"
$env:OPENAI_MODEL="qwen2.5-coder:7b"

openclaude
```

---

## Guias de Configuração

### Para iniciantes

- [Configuração para Não-Técnicos](docs/pt-br/configuracao-nao-tecnica.md)
- [Início Rápido — Windows](docs/pt-br/inicio-rapido-windows.md)
- [Início Rápido — macOS / Linux](docs/pt-br/inicio-rapido-mac-linux.md)

### Para usuários avançados

- [Configuração Avançada](docs/pt-br/configuracao-avancada.md)
- [Instalação no Android](ANDROID_INSTALL.md)

---

## Provedores Suportados

| Provedor | Como configurar | Observações |
| --- | --- | --- |
| OpenAI-compatível | `/provider` ou variáveis de ambiente | Funciona com OpenAI, OpenRouter, DeepSeek, Groq, Mistral, LM Studio e outros servidores `/v1` compatíveis |
| Gemini | `/provider` ou variáveis de ambiente | Suporta chave de API, access token ou fluxo ADC local |
| GitHub Models | `/onboard-github` | Onboarding interativo com credenciais salvas |
| Codex | `/provider` | Usa credenciais existentes do Codex quando disponíveis |
| Ollama | `/provider` ou variáveis de ambiente | Inferência local sem necessidade de chave de API |
| Atomic Chat | configuração avançada | Backend local para Apple Silicon |
| Bedrock / Vertex / Foundry | variáveis de ambiente | Integrações adicionais para ambientes suportados |

---

## O que funciona

- **Fluxos de trabalho de codificação com ferramentas**: Bash, leitura/escrita/edição de arquivos, grep, glob, agentes, tasks, MCP e comandos slash
- **Respostas em streaming**: Saída de tokens em tempo real e progresso das ferramentas
- **Chamada de ferramentas (tool calling)**: Loops de múltiplas etapas com chamadas ao modelo, execução de ferramentas e respostas de acompanhamento
- **Imagens**: Entradas de imagem via URL e base64 para provedores que suportam visão
- **Perfis de provedores**: Configuração guiada com suporte a `.openclaude-profile.json`
- **Backends de modelos locais e remotos**: APIs em nuvem, servidores locais e inferência local em Apple Silicon

---

## Notas sobre Provedores

O OpenClaude suporta múltiplos provedores, mas o comportamento não é idêntico entre todos eles.

- Funcionalidades específicas da Anthropic podem não existir em outros provedores
- A qualidade das ferramentas depende muito do modelo selecionado
- Modelos locais menores podem ter dificuldades com fluxos longos de múltiplas etapas
- Alguns provedores impõem limites de saída menores que os padrões da CLI — o OpenClaude se adapta quando possível

> **Dica:** Para melhores resultados, use modelos com forte suporte a chamadas de ferramentas/funções.

---

## Roteamento de Agentes

O OpenClaude pode direcionar diferentes agentes para diferentes modelos por meio de configuração. Isso é útil para otimização de custos ou divisão de trabalho por capacidade do modelo.

Adicione ao `~/.claude/settings.json`:

```json
{
  "agentModels": {
    "deepseek-chat": {
      "base_url": "https://api.deepseek.com/v1",
      "api_key": "sk-sua-chave"
    },
    "gpt-4o": {
      "base_url": "https://api.openai.com/v1",
      "api_key": "sk-sua-chave"
    }
  },
  "agentRouting": {
    "Explore": "deepseek-chat",
    "Plan": "gpt-4o",
    "general-purpose": "gpt-4o",
    "frontend-dev": "deepseek-chat",
    "default": "gpt-4o"
  }
}
```

Quando nenhuma correspondência de roteamento é encontrada, o provedor global continua sendo o fallback.

> **Atenção:** Os valores de `api_key` em `settings.json` são armazenados em texto simples. Mantenha este arquivo privado e não o envie para controle de versão.

---

## Busca e Fetch na Web

Por padrão, o `WebSearch` funciona em modelos não-Anthropic usando DuckDuckGo. Isso oferece ao GPT-4o, DeepSeek, Gemini, Ollama e outros provedores compatíveis com OpenAI um caminho gratuito de busca na web.

> **Atenção:** O fallback para DuckDuckGo funciona raspando resultados de busca e pode sofrer limitações de taxa, bloqueios, ou estar sujeito aos Termos de Serviço do DuckDuckGo. Se quiser uma opção mais confiável, configure o Firecrawl.

Para backends nativos da Anthropic e respostas do Codex, o OpenClaude mantém o comportamento nativo de busca na web do provedor.

O `WebFetch` funciona, mas seu caminho básico de HTTP + HTML-para-markdown ainda pode falhar em sites renderizados por JavaScript ou em sites que bloqueiam requisições HTTP simples.

### Configurando Firecrawl (opcional)

Defina uma chave de API do [Firecrawl](https://firecrawl.dev) se quiser comportamento de busca/fetch mais robusto:

```bash
export FIRECRAWL_API_KEY=sua-chave-aqui
```

Com o Firecrawl ativado:

- `WebSearch` pode usar a API de busca do Firecrawl (DuckDuckGo continua como caminho gratuito padrão para modelos não-Claude)
- `WebFetch` usa o endpoint de scraping do Firecrawl, lidando corretamente com páginas renderizadas por JavaScript

O plano gratuito em [firecrawl.dev](https://firecrawl.dev) inclui 500 créditos. A chave é opcional.

---

## Build a partir do Fonte e Desenvolvimento Local

```bash
bun install
bun run build
node dist/cli.mjs
```

### Comandos úteis durante o desenvolvimento

| Comando | O que faz |
| --- | --- |
| `bun run dev` | Inicia o servidor de desenvolvimento |
| `bun test` | Executa os testes unitários |
| `bun run test:coverage` | Gera relatório de cobertura |
| `bun run security:pr-scan -- --base origin/main` | Verifica segurança nas mudanças do PR |
| `bun run smoke` | Verificação rápida de inicialização |
| `bun run doctor:runtime` | Valida o ambiente de execução |
| `bun run verify:privacy` | Verifica conformidade de privacidade |

---

## Testes e Cobertura

O OpenClaude usa o executor de testes integrado do Bun para testes unitários.

**Executar todos os testes:**

```bash
bun test
```

**Gerar cobertura de testes:**

```bash
bun run test:coverage
```

**Abrir o relatório visual de cobertura:**

```bash
open coverage/index.html
```

**Rebuildar apenas a interface do relatório (se já tiver `coverage/lcov.info`):**

```bash
bun run test:coverage:ui
```

**Executar testes por área específica:**

```bash
bun run test:provider
bun run test:provider-recommendation
bun test caminho/para/arquivo.test.ts
```

**Validação recomendada antes de abrir um PR:**

1. `bun run build`
2. `bun run smoke`
3. `bun run test:coverage` — para cobertura mais ampla quando sua mudança afeta o runtime compartilhado ou lógica de provedor
4. `bun test ...` focado — para os arquivos e fluxos que você alterou

A saída de cobertura é gravada em `coverage/lcov.info`, e o OpenClaude também gera um mapa de calor no estilo git-activity em `coverage/index.html`.

---

## Estrutura do Repositório

```
openclaude/
├── src/              # CLI e runtime principal
├── scripts/          # Scripts de build, verificação e manutenção
├── docs/             # Documentação de configuração, contribuição e projeto
├── python/           # Helpers Python independentes e seus testes
├── vscode-extension/ # Extensão VS Code
├── .github/          # Automação, templates e configuração de CI
└── bin/              # Entrypoints da CLI
```

---

## Extensão VS Code

O repositório inclui uma extensão VS Code em [`vscode-extension/openclaude-vscode`](vscode-extension/openclaude-vscode) para integração de lançamento do OpenClaude, interface de painel de controle com reconhecimento de provedor e suporte a temas.

---

## Segurança

Se você acredita ter encontrado um problema de segurança, consulte [SECURITY.md](SECURITY.md).

---

## Comunidade

- Use [GitHub Discussions](https://github.com/Gitlawb/openclaude/discussions) para perguntas, ideias e conversas da comunidade
- Use [GitHub Issues](https://github.com/Gitlawb/openclaude/issues) para bugs confirmados e trabalho de funcionalidades acionáveis

---

## Contribuindo

Contribuições são bem-vindas!

Para mudanças maiores, abra uma issue primeiro para que o escopo fique claro antes da implementação.

**Comandos de validação úteis:**

```bash
bun run build
bun run test:coverage
bun run smoke
bun test ...  # focado nas áreas que você tocou
```

---

## Aviso Legal

O OpenClaude é um projeto comunitário independente e não é afiliado, endossado ou patrocinado pela Anthropic.

O OpenClaude originou-se da base de código do Claude Code e foi substancialmente modificado para suportar múltiplos provedores e uso aberto. "Claude" e "Claude Code" são marcas registradas da Anthropic PBC. Consulte [LICENSE](LICENSE) para detalhes.

---

## Licença

Consulte [LICENSE](LICENSE).
