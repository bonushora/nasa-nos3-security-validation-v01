# Matriz de aceitação e prontidão experimental EXP001-P0

## Aceitação documental

| # | Entregável/controle | Evidência | Resultado |
|---:|---|---|---|
| 1 | Protocolo científico v0.1 | pergunta, design, controles, incerteza e procedimento | PASS |
| 2 | Hipóteses e nulas | H1–H8 com observáveis/falsificação | PASS |
| 3 | Ameaças e fronteiras | TB1–TB8, premissas e falhas do witness | PASS |
| 4 | Contrato do witness | separação, sem autoridade, saúde e accounting | PASS |
| 5 | Schema canônico | sete eventos e campos exigidos | PASS |
| 6 | Autoridade e retries | grant, intenção, tentativa, efeito, budget, replay/restart | PASS |
| 7 | Cenários sintéticos | S01–S10 com nove campos | PASS |
| 8 | Oráculos | grafo, invariantes, incerteza e regras | PASS |
| 9 | Decisão em quatro estados | PASS/FAIL/INCONCLUSIVE/ABORTED | PASS |
| 10 | Proveniência/reprodutibilidade | P0–P7, custódia, isolamento e comparadores | PASS |
| 11 | Matriz e estados independentes | gates documentais e físicos separados | PASS |
| 12 | Snapshot BH-SDP v2.3 | hashes, estados, limites e próxima fase | PASS |

`EXP001_P0_DOCUMENTATION_GREEN=PASS` só vale após validar arquivos, links, JSON, identificadores, cenários e hashes. Não autoriza execução.

## Gates físicos

| Gate | Requisito | Estado | Recuperação |
|---|---|---|---|
| E1 | autorização de execução e stop authority | `NOT_AUTHORIZED` | nova missão delimitada |
| E2 | proveniência recursiva NOS3 | `BLOCKED` | tree/gitlinks/reachability incompletos |
| E3 | checkout/ambiente isolado aprovado | `NÃO_EXECUTADO` | materialização não autorizada |
| E4 | hashes de ferramentas/imagens/binários/config | `NÃO_EXECUTADO` | provisionamento autorizado |
| E5 | credenciais sintéticas/endpoints não operacionais | `NÃO_EXECUTADO` | fixture ausente |
| E6 | witness implementado sem autoridade | `NÃO_EXECUTADO` | somente contrato |
| E7 | calibração e incerteza | `NÃO_EXECUTADO` | depende da implementação |
| E8 | oráculo implementado/testado | `NÃO_EXECUTADO` | regras documentais apenas |
| E9 | contenção, egress, recursos, reset/cleanup | `NÃO_EXECUTADO` | ambiente ausente |
| E10 | cenário/seeds/repetições/parada | `DEFERRED` | calibração/potência |
| E11 | dry run em fixture não-NOS3 | `NÃO_EXECUTADO` | exige autoridade |
| E12 | revisão humana pré-inscrição | `DEFERRED` | após E1–E10 |

`EXP001_EXECUTION_READINESS=BLOCKED`

## Estados independentes

```text
EXP001_P0_DOCUMENTATION_GREEN=PASS
EXP001_EXECUTION_READINESS=BLOCKED
NOS3_TRANSITIVE_PROVENANCE=BLOCKED
NOS3_EXECUTION=NOT_AUTHORIZED
ADVERSARIAL_EXPERIMENTS=NOT_EXECUTED
EXPERIMENTAL_SECURITY=NOT_QUALIFIED
REMOTE_MUTATION=NOT_AUTHORIZED
```

## Próxima fase mínima

Recomenda-se `EXP001-P1 — Offline Witness and Oracle Fixture`, somente sob nova autoridade, contra fixture sintética não-NOS3. O contato com NOS3 permanece proibido até E1–E12 passarem.

