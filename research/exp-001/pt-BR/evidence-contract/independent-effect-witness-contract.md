# Contrato do Independent Effect Witness EXP001-P0

## Finalidade

O witness estabelece se e como um efeito ocorreu, independentemente de ACK, telemetria e logs do executor. Ele não decide autorização e não pode emitir comandos.

## Separação obrigatória

O witness deve ser logicamente separado do executor e não pode possuir credencial de envio, escrita no command bus, controle de simulador ou grant utilizável contra o sistema. Privilégio mínimo read-only é obrigatório.

Para fixture contida inicial, exige-se ao menos processo, credencial, journal append-only e interface de captura distintos. Host/kernel/rede/relógio/storage compartilhados são riscos comuns declarados. Fases mais fortes separam host, caminho, relógio e armazenamento.

Logs do executor, ACKs, contadores do handler e telemetria derivada são apenas evidência auxiliar. Dois canais derivados do mesmo fato não são dois witnesses independentes.

## Observações obrigatórias

O witness registra eventos canônicos para:

- estado antes da janela;
- tentativa de efeito em fronteira não pertencente ao executor, quando disponível;
- mudança ou não mudança com incerteza;
- identidade e contagem verificadas independentemente;
- reconciliação com intenção, autoridade, tentativa e orçamento;
- heartbeat, sequência, drops, backpressure, restart, clock e saúde do journal.

Os sete tipos canônicos permanecem distintos, e estados desconhecidos/ausentes não são preenchidos por inferência.

## Fontes em ordem de independência

1. interface read-only de estado não controlada pelo handler;
2. provider/sensor redundante de fonte distinta;
3. captura em outro hop de transporte/abstração;
4. invariante de estado final calculada independentemente;
5. telemetria, ACKs e logs apenas como corroboração.

A fonte real e os domínios de falha compartilhados devem ser declarados. “Verdade simulada” não é independente se o executor a escreve/controla.

## Journal e continuidade

O journal é append-only e encadeado por hash. Registros carregam sequência, digest anterior, `boot_epoch`, tempo monotônico, tick e digest canônico. Checkpoints preservam head/sequence fora do ciclo do executor.

Restart cria nova época. A recuperação verifica a cadeia e preserva todo efeito não resolvido. Gap, truncamento ou head incompatível produz `EVIDENCE_INCOMPLETE`.

## Saúde

Evidências obrigatórias: atestação/configuração; heartbeat; continuidade de sequência; drops/backpressure; storage/flush; fonte/resolução/drift/incerteza do clock; marcadores de restart/shutdown; calibração e versão. Saúde insuficiente no intervalo decisivo proíbe PASS.

## Contabilização de efeitos

`effect_id` não se confunde com `command_id` ou `attempt_id`. Registros duplicados são deduplicados por identidade; efeitos reais repetidos continuam separados. Mudanças parciais/reversíveis permanecem como efeitos parciais.

Estados finais: `VERIFIED_AND_RECONCILED`, `VERIFIED_UNRECONCILED`, `NOT_OBSERVED_WITH_COMPLETE_WINDOW`, `PARTIAL`, `AMBIGUOUS` ou `EVIDENCE_INCOMPLETE`.

## Falhas e tratamento

| Falha | Tratamento |
|---|---|
| gap/drop decisivo | `INCONCLUSIVE`, salvo evidência redundante exata |
| descontinuidade do journal/hash | `ABORTED` ou `INCONCLUSIVE` |
| autoridade de comando descoberta | `ABORTED`; independência inválida |
| fonte antiga/derivada | `INCONCLUSIVE` |
| incerteza maior que a fronteira | `INCONCLUSIVE` |
| witness altera estado | `ABORTED` |
| falha comum compromete ambos | `INCONCLUSIVE` ou `ABORTED` |

## Gate de implementação

Este contrato é documental. Código, implantação, calibração e contenção não existem em P0 e exigem autorização separada.

