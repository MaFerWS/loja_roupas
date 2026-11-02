# Loja de moda feminina em Canindé — plano de 90 dias com agentes

Este repositório guarda os agentes que montam o plano de 90 dias (03/11/2026 a 31/01/2027) da loja de moda feminina adulta do dono (MF) no Centro de Canindé (CE), e tudo o que eles produzem.

## Como funciona

- **Orquestrador (Agente 0):** é o comando `/orquestrar`, em `.claude/commands/orquestrar.md`. Roda na conversa principal, porque só ela fala com o dono e chama os outros agentes.
- **Especialistas:** são subagentes em `.claude/agents/`, numerados 1, 2, 4, 5, 6, 7 e 8. **Não existe Agente 3**: a obra civil está sendo concluída pelo dono e está dentro das normas.
- **Dados de entrada:** `contexto/contexto-comum.md` (o projeto) e `contexto/respostas-do-dono.md` (as respostas do dono, que valem mais que o contexto comum).
- **Saídas:** cada agente grava a entrega completa em `entregas/NN-nome/` e o bloco "RESUMO PARA O ORQUESTRADOR" em `entregas/resumos/NN-nome.md`. Os agentes passam informação uns aos outros só por esses resumos.
- **Andamento:** fica em `entregas/STATUS.md`.

## Regras para o Claude neste repositório

- Responda ao dono em português, direto, explicando o porquê de cada passo. O dono não tem experiência em varejo de moda.
- Antes de cada rodada de agentes, diga o que vai rodar e espere o "ok" do dono.
- **Git:** nunca faça commit nem push direto na `main`. Trabalhe numa branch (`plano/<etapa>`) e faça commit ao fim de cada etapa. **Push e pull request só com autorização do dono, e o merge é sempre dele.**
- Não invente leis, taxas nem preços. Cada número é marcado como PESQUISADO (fonte e data) ou ESTIMATIVA (premissa).
- Se o dono corrigir algum dado, atualize `contexto/` primeiro e depois rode de novo os agentes afetados (`/rodar-agente N`).
