# Matriz de equivalência semântica bilíngue EXP001-P0

Estado: `PASS`  
Política: SSSVL Bilingual Publication Policy v1.0  
Escopo: candidato público PUB-R2

Esta matriz registra a comparação técnica final entre as variantes em inglês e português brasileiro. Ela não cria evidência experimental. As identidades exatas em bytes de cada par constam em `source-to-translation-manifest.json`.

## Revisão por par

| Par | Conteúdo preservado | Resultado |
|---|---|---|
| ROOT-README | marcadores de estado, aviso de pesquisa independente, limitações, navegação | PASS |
| EXP001-INDEX | escopo do protocolo, navegação, estado proposto do witness | PASS |
| EXP001-PROTOCOL | pergunta, hipótese, classes D/P/H/O, controles, repetições, incerteza | PASS |
| EXP001-HYPOTHESES | H1–H8, H1₀–H8₀, observáveis, sentido de falsificação | PASS |
| EXP001-THREATS | ativos, ameaças, TB1–TB8, premissas rejeitadas, exclusões | PASS |
| EXP001-SCENARIOS | S01–S10 e os nove campos exigidos por cenário | PASS |
| EXP001-ORACLES | grafo de estados, invariantes, regras por cenário, tratamento de ambiguidade | PASS |
| EXP001-WITNESS | separação lógica, ausência de autoridade de comando, saúde, tratamento de falhas | PASS |
| EXP001-EVENT-SCHEMA | ID do schema, chaves, restrições, enums, sete identificadores de evento | PASS |
| EXP001-AUTHORITY | identificadores, contrato de grant, orçamento, regras de retry/replay/restart | PASS |
| EXP001-PROVENANCE | camadas P0–P7, custódia, isolamento, reprodutibilidade | PASS |
| EXP001-DECISIONS | PASS / FAIL / INCONCLUSIVE / ABORTED e precedência | PASS |
| EXP001-READINESS | 12 critérios documentais, gates físicos E1–E12, estados independentes | PASS |
| EXP001-SNAPSHOT | chaves/estados normativos, hashes de evidência, limites, derivação | PASS |
| FUTURE-ARCHIVAL-METADATA | idioma, versão, campos de commit/hash/DOI e limites de autorização | PASS |

## Controles de identificadores e sentido

| Controle | Equivalência exigida | Resultado |
|---|---|---|
| Hipóteses | H1–H8 e respectivas nulas mantêm o mesmo teste e sentido de rejeição | PASS |
| Cenários | S01–S10 mantêm precondições, autoridade/orçamento, estímulo, observações, witness, falha/ambiguidade, oráculo, aceitação e reprodutibilidade | PASS |
| Eventos | `COMMAND_RECEIVED`, `COMMAND_AUTHORIZED`, `COMMAND_DISPATCHED`, `EFFECT_ATTEMPTED`, `EFFECT_OBSERVED`, `EFFECT_INDEPENDENTLY_VERIFIED`, `EFFECT_RECONCILED` são identificadores idênticos em bytes | PASS |
| Fronteiras de confiança | TB1–TB8 mantêm os mesmos papéis internos/externos e requisitos de evidência | PASS |
| Identidades de autoridade | `authority_id`, `grant_id`, `intent_id`, `command_id`, `attempt_id`, `effect_id` e `boot_epoch` não mudam | PASS |
| Estados do ledger | `AVAILABLE`, `RESERVED_AMBIGUOUS`, `CONSUMED_VERIFIED`, `RELEASED_NO_EFFECT`, `EXHAUSTED` não mudam | PASS |
| Estados da tentativa anterior | `NO_EFFECT_CONFIRMED`, `EFFECT_CONFIRMED`, `AMBIGUOUS`, `PARTIAL`, `EVIDENCE_INCOMPLETE` não mudam | PASS |
| Oráculos | Ordem canônica, invariantes de orçamento e classificações esperadas S01–S10 são equivalentes | PASS |
| Decisões | `PASS`, `FAIL`, `INCONCLUSIVE` e `ABORTED` mantêm definições e precedência | PASS |
| Estados de evidência | `BLOCKED`, `NOT_AUTHORIZED`, `NOT_EXECUTED`, `NOT_QUALIFIED` e valores normativos BH-SDP permanecem inalterados quando o schema exige compatibilidade | PASS |
| Contagens | 8 hipóteses, 10 cenários, 9 campos por cenário, 7 eventos, 8 fronteiras, 12 critérios documentais, 12 gates físicos e 4 decisões conferem | PASS |
| Identidade Git | o commit NOS3 `5a3bdee6be9a2c67fdf994ae6db56d5c60395302` é idêntico | PASS |
| Limites científicos | ausência de execução, resultado adversarial, proveniência transitiva completa, qualificação de segurança e endosso NASA é igualmente explícita | PASS |

## Diferenças revisadas

O idioma da prosa e os links específicos de cada idioma diferem por projeto. O derivado português do schema traduz apenas título e descrição legíveis. ID do schema, nomes de campos, restrições, enumerações e eventos não mudam. A representação BH-SDP portuguesa traduz texto livre e adiciona metadados de derivação; estados normativos legíveis por máquina e referências aos hashes da fonte inglesa selada permanecem inalterados. Essas diferenças não alteram autoridade científica nem peso probatório.

Nenhum artefato pareado está em `REVIEW_REQUIRED`.

