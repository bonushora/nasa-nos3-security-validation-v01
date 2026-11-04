# Requisitos de oráculos determinísticos EXP001-P0

## Entradas

O oráculo consome conjunto imutável de eventos, saúde do witness, ledger de autoridade, estados inicial/final, cenário, modelo de incerteza e manifesto de proveniência. Não consulta estado mutável após selar a evidência.

## Grafo canônico

```text
COMMAND_RECEIVED
  -> COMMAND_AUTHORIZED(allow|deny)
  -> COMMAND_DISPATCHED
  -> EFFECT_ATTEMPTED
  -> EFFECT_OBSERVED
  -> EFFECT_INDEPENDENTLY_VERIFIED
  -> EFFECT_RECONCILED
```

Um caminho permitido pode parar quando ocorre falha. Um caminho negado não pode produzir despacho/efeito atribuível. Evidência intermediária ausente não é inferida.

## Determinismo

Com os mesmos bytes canônicos, versão do oráculo, cenário e incerteza, a avaliação produz achados normalizados idênticos e o mesmo resultado. Regras são versionadas, ordenadas, sem efeitos colaterais e independentes de discricionariedade pós-inscrição.

O oráculo deve:

1. validar schema e hashes;
2. rejeitar identidades misturadas;
3. montar causalidade por IDs, não só timestamps;
4. verificar escopo, validade e orçamento;
5. contar efeitos sem apagar repetições reais;
6. distinguir evidência ausente, contraditória, tardia, parcial e não saudável;
7. aplicar incerteza e janelas;
8. avaliar aborto antes de PASS/FAIL;
9. emitir rastreio de regras e IDs; e
10. manter efeitos não resolvidos no ledger.

## Invariantes

- `verified_effects(intent) <= authorized_effect_budget(intent)`, salvo novo grant separado.
- Retries compartilham grant e orçamento por padrão.
- `COMMAND_DISPATCHED` não implica `EFFECT_OBSERVED`.
- ACK/log/telemetria não implica `EFFECT_INDEPENDENTLY_VERIFIED`.
- Ausência desses canais não implica zero efeito.
- Negação exige zero despacho/efeito atribuível.
- Cada efeito é reconciliado ou fica `UNRESOLVED`.
- Witness não saudável em intervalo decisivo proíbe PASS.

## Resumo por cenário

| Cenário | Condição decisiva |
|---|---|
| S01 | exatamente um efeito verificado/reconciliado sob orçamento 1 |
| S02 | negação, zero despachos e zero efeitos |
| S03 | um despacho/tentativa, zero efeito e falha explícita |
| S04 | um efeito verificado com ACK ausente |
| S05 | tentativas ligadas; efeitos agregados ≤1 |
| S06 | duplicatas/replays identificados; efeitos ≤1 |
| S07 | pós-recuperação 0 ou 1 sob grant original |
| S08 | exatamente um efeito pré-restart; nenhuma duplicação |
| S09 | efeitos/estado pertencem ao conjunto concorrente permitido |
| S10 | estado independente governa; contradição aparece |

## Incerteza

A janela deve exceder a latência máxima justificada mais incerteza de captura. Diferenças abaixo da resolução são ambíguas. Eventos sem ordem causal estabelecível são concorrentes/desconhecidos.

Ambiguidade decisiva produz `INCONCLUSIVE`; falha de contenção/identidade produz `ABORTED`. Implementar o oráculo exige revisão e autorização separadas.

