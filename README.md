# nevoa-handoff

Skill para transformar o estado atual de uma sessão em um handoff curto, estruturado e acionável para outro agente continuar o trabalho sem precisar redescobrir contexto.

## O que a skill faz

Ao ser chamada, a skill analisa a conversa e o estado atual do trabalho e gera um arquivo `handoff.md` no diretório temporário do sistema operacional.

O objetivo não é criar um resumo completo da conversa. O objetivo é transferir apenas o estado necessário para que uma nova sessão consiga continuar o trabalho com segurança e com o mínimo de retrabalho.

Ela identifica e organiza:

- o objetivo mais provável da próxima sessão;
- o estado atual do trabalho;
- decisões que já foram tomadas;
- restrições, convenções e preferências que precisam ser preservadas;
- artefatos relevantes e onde encontrá-los;
- o que já foi concluído;
- dúvidas que continuam realmente abertas;
- os próximos passos recomendados;
- skills que podem ser úteis para a continuação.

## Sem pergunta de contexto

A skill não pergunta ao usuário qual será o objetivo da próxima sessão.

Ela infere esse objetivo a partir da conversa atual, do trabalho em andamento e das pendências existentes.

Se o usuário já tiver informado explicitamente o foco da próxima sessão, essa informação tem prioridade.

## Preserva decisões já tomadas

Um dos principais objetivos do handoff é impedir que a nova sessão volte a discutir decisões que já foram fechadas.

A skill separa claramente:

- contexto estabelecido;
- decisões tomadas;
- hipóteses ou suposições;
- questões ainda abertas;
- próximas ações.

Isso ajuda o próximo agente a continuar de onde o anterior parou, em vez de reiniciar discovery ou reinterpretar decisões sem necessidade.

## Não duplica documentação existente

Specs, design docs, ADRs, issues, pull requests, commits, diffs, arquivos de código e outros artefatos existentes não devem ser copiados para o handoff.

A skill referencia esses artefatos pelo caminho ou URL e explica em uma linha por que cada um é relevante.

Os artefatos referenciados continuam sendo a fonte de verdade para os detalhes já documentados.

## Estrutura do handoff

O arquivo gerado utiliza, quando aplicável, esta estrutura:

~~~md
# Session Handoff

## Next Session Objective
## Current State
## Decisions Made
## Constraints and Conventions
## Relevant Artifacts
## Work Completed
## Open Questions
## Recommended Next Steps
## Suggested Skills
~~~

Nem toda seção precisa conter conteúdo. O objetivo é manter o documento pequeno e operacional.

## Suggested Skills

Quando outras skills puderem ajudar na continuação do trabalho, o handoff registra:

- o nome exato da skill;
- quando ou por que o próximo agente deveria utilizá-la.

Isso evita que a nova sessão precise descobrir novamente quais ferramentas ou workflows fazem sentido para aquela etapa.

## Segurança

O handoff não deve carregar segredos ou dados sensíveis desnecessários.

A skill orienta o agente a omitir ou substituir por placeholders informações como:

- API keys;
- tokens;
- senhas;
- private keys;
- credenciais;
- connection strings com segredos;
- endereços pessoais;
- dados pessoais que não sejam necessários para continuar o trabalho.

Quando a existência do valor for importante, o contexto pode ser preservado sem revelar o segredo.

Exemplo:

~~~
API_TOKEN=<configured in environment>
~~~

## Resultado esperado

Um bom handoff deve permitir que um agente novo responda rapidamente a seis perguntas:

1. O que estamos fazendo?
2. Onde o trabalho parou?
3. O que já foi decidido?
4. Quais artefatos são a fonte de verdade?
5. O que ainda está em aberto?
6. Qual é a próxima ação?

A prioridade é continuidade, não histórico.

## Skill

A implementação completa está em [SKILL.md](./SKILL.md).
