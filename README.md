# Loja de moda feminina — Canindé (CE)

Plano de 90 dias (**03/11/2026 a 31/01/2027**) para montar e fazer funcionar uma loja multimarca de moda feminina adulta no Centro de Canindé. A meta de inauguração é **28/11/2026**, com limite em 05/12/2026.

O plano é feito por **8 agentes de IA**: um orquestrador, seis especialistas e um revisor independente. Eles rodam no **Claude Code** e trabalham só com os arquivos deste repositório: leem o contexto, gravam suas entregas e passam informação uns aos outros por meio de resumos.

## Os agentes

| Nº | Agente | Arquivo | Rodada |
|---|---|---|---|
| 0 | Orquestrador | `.claude/commands/orquestrar.md` | início e fim |
| 1 | Legalização, contabilidade e tributos | `.claude/agents/agente-1-legalizacao.md` | 1 |
| 2 | Design de interiores, layout e mobiliário | `.claude/agents/agente-2-design.md` | 1 |
| 4 | Compras, mix de produto e estoque | `.claude/agents/agente-4-compras.md` | 1 |
| 5 | Plano financeiro | `.claude/agents/agente-5-financeiro.md` | 1 e fechamento |
| 6 | Marca, marketing e inauguração | `.claude/agents/agente-6-marketing.md` | 2 |
| 7 | Operação, equipe e sistemas | `.claude/agents/agente-7-operacao.md` | 2 |
| 8 | Revisor independente | `.claude/agents/agente-8-revisor.md` | revisão |

Não há Agente 3 (Obras): a obra civil está sendo concluída pelo dono. A numeração foi mantida para combinar com o documento original dos prompts.

## Fluxo

```
/orquestrar perguntas    → o orquestrador faz as perguntas ao dono   → contexto/respostas-do-dono.md
/orquestrar cronograma   → cronograma-mestre e briefings             → entregas/00-orquestrador/, entregas/resumos/
/orquestrar rodada-1     → agentes 1, 2, 4 e 5 em paralelo
/orquestrar rodada-2     → agentes 6 e 7 (usam os resumos de 2 e 4)
/orquestrar fechamento   → agente 5 de novo, com os valores reais de 2, 4 e 6
/orquestrar revisao      → agente 8, com contexto limpo
/orquestrar consolidar   → plano final                              → entregas/00-orquestrador/plano-90-dias-final.md
```

Rodar só `/orquestrar` retoma da próxima etapa pendente em `entregas/STATUS.md`. Para refazer um agente específico, use `/rodar-agente N`.

## Estrutura

```
CLAUDE.md                      regras para o Claude neste repositório
.claude/commands/              orquestrador (/orquestrar) e /rodar-agente
.claude/agents/                os 7 agentes especialistas
contexto/contexto-comum.md     dados do projeto (planta, público, mix, números, fornecedores)
contexto/respostas-do-dono.md  respostas do dono (valem mais que o contexto comum)
entregas/STATUS.md             andamento de cada etapa
entregas/NN-nome/              entrega completa de cada agente
entregas/resumos/              os "RESUMO PARA O ORQUESTRADOR" de cada agente
```

## Como rodar

1. Instale o [Claude Code](https://docs.claude.com/en/docs/claude-code) e clone o repositório.
2. Dentro da pasta, rode `claude` e digite `/orquestrar`.
3. Responda às perguntas e confirme cada rodada.
4. Cada etapa vira commit numa branch. Você revisa o pull request e decide o merge.

Também dá para rodar pelo Claude na web, pedindo para trabalhar neste repositório.
