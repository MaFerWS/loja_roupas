---
description: Roda um único agente especialista do plano de 90 dias (1, 2, 4, 5, 6, 7 ou 8), fora da ordem do orquestrador — útil para refazer uma entrega depois de mudar o contexto.
argument-hint: "<número do agente> [observação para o agente]"
---

Rode o agente número $ARGUMENTS.

1. Mapeie o número para o subagente: 1 → `agente-1-legalizacao`, 2 → `agente-2-design`, 4 → `agente-4-compras`, 5 → `agente-5-financeiro`, 6 → `agente-6-marketing`, 7 → `agente-7-operacao`, 8 → `agente-8-revisor`. O número 3 não existe (a obra é do dono); se pedirem o 3, avise e pare.
2. Confira em `entregas/STATUS.md` se as dependências dele já rodaram (6 e 7 dependem de 2 e 4; o fechamento do 5 depende de 2, 4 e 6; o 8 depende de todos). Se faltar alguma, avise o dono e pergunte se quer rodar assim mesmo, com premissas.
3. Chame o subagente com: "Execute o seu trabalho conforme o seu arquivo de instruções." Acrescente a observação do dono, se houver.
4. Atualize `entregas/STATUS.md`, mostre ao dono o RESUMO PARA O ORQUESTRADOR e as perguntas que o agente deixou.
5. Faça commit na branch de trabalho. Não faça push sem o dono autorizar.
