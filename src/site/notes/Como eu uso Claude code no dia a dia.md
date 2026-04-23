---
{"dg-publish":true,"permalink":"/como-eu-uso-claude-code-no-dia-a-dia/","tags":["gardenEntry"],"dg-note-properties":{}}
---

# Como eu uso Claude Code no dia a dia

> Nota viva — atualizada conforme meu uso evolui.

Não uso Claude Code como um autocomplete glorificado.
Uso como um par de desenvolvimento que cuida do mecânico
enquanto eu fico no estratégico.

## O princípio central

A maioria das pessoas usa IA para escrever código mais rápido.
Eu uso para **não precisar pensar em certas coisas**.

Existe uma diferença enorme entre os dois.

Velocidade é um efeito colateral. O ganho real é foco.

## O que é diferente no meu setup: Hooks

A parte que mais muda o jogo não é o modelo — é a automação
em volta dele.

Uso hooks do Claude Code para:

- **Notificações** — quando uma tarefa longa termina, recebo
  um sinal. Não fico policiando o terminal.
- **Triggers automáticos** — certas ações disparam outros
  agentes ou scripts sem intervenção minha.
- **Pipeline de PR** — o pr-watcher monitora o canal do Beeper
  e aciona revisões de código automaticamente.

O resultado: Claude Code trabalha em background enquanto
eu estou em outra coisa.

## Como eu estruturo uma sessão

1. Abro com um `CLAUDE.md` que já carrega o contexto do projeto
2. Defino o objetivo da sessão em uma frase
3. Delego a execução — testes, boilerplate, refactor
4. Reviso o resultado com olhos de arquiteto, não de digitador

## O que eu *não* delego

- Decisões de arquitetura que vão durar anos
- Code review final antes de merge
- Qualquer coisa que eu não consiga explicar pra outra pessoa

## Próximas ideias pra explorar

- [ ] Orquestração multi-agent para tarefas paralelas
- [ ] MCP servers customizados para o contexto do MELI
- [ ] Hooks para registrar horas de on-call automaticamente

---

*Relacionado: [[projetos/pr-watcher\|projetos/pr-watcher]], [[engenharia/mcp-servers\|engenharia/mcp-servers]]*