---
{"dg-publish":true,"permalink":"/projetos/como-fazer-review-de-pr-de-forma-automagica/","tags":["engenharia","ai","claude","golang"],"dg-note-properties":{"tags":["engenharia","ai","claude","golang"]}}
---

# Construindo o pr-watcher: A Jornada de um Agente Autônomo em Go


Neste post, vamos mergulhar nos bastidores da criação do **pr-watcher**, um daemon robusto escrito em Go projetado para revolucionar a forma como revisamos e gerenciamos Pull Requests usando o poder do **Claude Code**.

## 🚀 A Visão

O problema era claro: revisões manuais são gargalos, falhas de CI consomem tempo precioso e conflitos de merge são irritantes. A solução? Um agente que não só observa, mas **age**.


## 🏗️ A Arquitetura

Desde o dia 1, seguimos os princípios de **Clean Architecture** e o **Standard Go Project Layout**. A ideia foi separar a lógica de negócio (Pipeline) dos detalhes de infraestrutura (GitHub API, Git CLI, Terminal).

### Fases do Desenvolvimento


### 1. O Nascimento (Bootstrap & Core)

Começamos com a fundação: um carregador de configuração YAML com suporte a variáveis de ambiente e a entidade básica de um PR. Logo em seguida, implementamos o motor de execução:

- **Git Worktrees**: A chave para o paralelismo. O daemon cria diretórios isolados para cada tarefa, permitindo processar múltiplos PRs sem sujar o ambiente principal.

- **GitHub Client**: Uma abstração sobre a API REST para listar, comentar e gerenciar labels.

  

### 2. O Cérebro (Pipeline & Orquestração)

Criamos um orquestrador modular. Cada PR passa por uma série de fases:

1. **Review**: O Claude analisa o código.

2. **Deconflict**: O Claude resolve conflitos de merge via rebase.

3. **Fix CI**: O robô lê logs de erro e faz push de correções.

### 3. O Toque Humano (Modo Interativo)

Nem tudo deve ser automático. Implementamos o **Modo Interativo**:

- Integração com **Tmux** e **Terminal/iTerm2** no macOS.

- O daemon abre uma janela de terminal automaticamente e "te chama" para colaborar com o Claude quando necessário.

### 4. Confiabilidade e Observabilidade

Para rodar em produção, adicionamos:

- **Métricas Prometheus**: Monitoramento de PRs processados e saúde do daemon.

- **Logs Estruturados**: Opção de saída em JSON para ferramentas de análise.

- **Notificações**: Alertas no Desktop, Slack e via Webhooks.


### 5. Monitoramento Híbrido (O "Pulo do Gato")

Evoluímos de um simples *polling* para um modelo **Híbrido**:

- **Webhooks**: Reações instantâneas a eventos do GitHub.

- **Polling Fallback**: Uma rede de segurança que verifica tudo a cada 30 minutos, garantindo que nada escape.

## 🛠️ Como foi construído

Este projeto foi desenvolvido de forma colaborativa entre um humano e um agente de IA (Gemini CLI), utilizando:

- **Subagent-Driven Development**: Especialistas para cada tarefa.

- **Conventional Commits**: Um histórico de git limpo e profissional.

- **TDD (Test Driven Development)**: Garantindo que a expansão de caminhos (`~/`) e configurações funcionassem antes mesmo do código estar pronto.


## 📈 Resultado Final

O `pr-watcher` hoje é capaz de:

- Detectar um novo PR.

- Notificar o time no Slack.

- Resolver conflitos de merge sozinho.

- Sugerir melhorias de código.

- Abrir um iTerm2 na sua frente para uma revisão em dupla.


O código está disponível e pronto para ser containerizado via Docker ou rodar como um serviço nativo no macOS.

  
---

*Este post resume o esforço de engenharia para criar um assistente de desenvolvimento que realmente faz o trabalho pesado.*