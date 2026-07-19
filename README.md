# AIOX Cockpit — Issues

Rastreador público de bugs e feedback do **AIOX Cockpit** (o produto em si é um repositório privado).

- **Testers/alunos:** relate problemas aqui (ou ao time) — inclua seu SO (macOS/Windows), a versão do Cockpit (canto da barra superior) e o que você fazia quando ocorreu.
- **Nunca inclua** senhas, tokens, e-mails de terceiros ou conteúdo dos seus terminais em issues.
- O time triage cada relato, cruza com o backlog interno e atualiza o status aqui.

| Label | Significado |
|---|---|
| `bug` / `enhancement` | tipo |
| `os:mac` / `os:windows` / `os:both` | plataforma |
| `severity:crash` / `severity:major` / `severity:minor` | severidade |
| `status:known` / `status:investigating` / `status:fixed-pending-release` | estado |

## 🩺 Diagnóstico automático — `/aiox-doctor`

Teve um problema com o Cockpit? Você não precisa escrever a issue na mão. Instale a skill de
diagnóstico no seu Claude Code (uma vez):

**macOS/Linux:**
```bash
mkdir -p ~/.claude/skills/aiox-doctor && curl -fsSL https://raw.githubusercontent.com/SynkraAI/aiox-cockpit-issues/main/skills/aiox-doctor/SKILL.md -o ~/.claude/skills/aiox-doctor/SKILL.md
```

**Windows (PowerShell):**
```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills\aiox-doctor" | Out-Null; Invoke-WebRequest https://raw.githubusercontent.com/SynkraAI/aiox-cockpit-issues/main/skills/aiox-doctor/SKILL.md -OutFile "$env:USERPROFILE\.claude\skills\aiox-doctor\SKILL.md"
```

Depois, em qualquer terminal (FORA do Cockpit se ele estiver crashando), abra o `claude` e conte o problema:

```
/aiox-doctor o cockpit fecha sozinho depois de uns minutos
```

A skill examina sua máquina (dependências, PATH, antivírus, logs, crash reports), **conserta o que
for do seu ambiente**, e — com a sua aprovação do texto — publica a issue aqui automaticamente.
Ela nunca envia dados sem te mostrar antes.
