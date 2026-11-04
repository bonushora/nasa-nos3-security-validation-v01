# Contrato de proveniência e reprodutibilidade EXP001-P0

## Identidade experimental

Antes da execução, um manifesto canônico vincula:

- versões do protocolo, hipótese, cenário, oráculo e schema;
- snapshot de governança e autorização;
- commit/tree do NOS3 e gitlinks recursivos;
- identidade cFS/F´ sem modificar workspaces independentes;
- hashes de fonte, toolchain, dependências, imagem, binário, configuração, dicionário e tabela;
- SBOMs/attestations;
- software/configuração/calibração do witness;
- grant sintético, bytes, falhas, seed, estado, timing, recursos e topologia;
- código de análise e formato normalizado.

O manifesto recebe `experiment_identity_digest`. Qualquer mismatch é outro experimento e bloqueia comparação.

## Camadas

| Camada | Evidência |
|---|---|
| P0 governança | autoridade, risco, stop authority e snapshot |
| P1 fonte | repositório, commit, tree e gitlinks recursivos |
| P2 build | versões, entradas, invocação e ambiente |
| P3 artefatos | binários, imagens, configurações e SHA-256 |
| P4 execução | cenário, seed, grant, comando e falhas |
| P5 instrumentação | witness, schema, calibração e saúde |
| P6 saídas brutas | eventos, capturas, estados e logs |
| P7 análise | oráculo, rastreio, achados e decisão |

P1 do NOS3 está incompleta porque a proveniência transitiva está `BLOCKED`; a execução continua bloqueada mesmo com P0 documental PASS.

## Custódia

Evidência bruta é append-only, recebe hash na captura e é selada antes da análise. O manifesto registra caminho relativo, media type, tamanho, SHA-256, produtor, tempo, custódia e derivação/redação. Originais nunca são sobrescritos.

Mudanças de custódia serão autenticadas por implementação futura aprovada. Segredos e credenciais operacionais não entram no conjunto.

## Pacote reprodutível

Contém manifesto, índice bruto, eventos normalizados, entrada/saída do oráculo, rastreio, incerteza/calibração, desvios e revisão humana. Deve permitir reconstruir a mesma entrada e decisão, sem alegar recriar efeito físico.

## Comparadores, repetição e isolamento

Baselines e controles mantêm identidade, instrumentação, recursos e janela, variando apenas o fator pré-inscrito. Ordem, reset, seeds, repetições, exclusões e parada são fixados antes de examinar dados.

Execução futura exige redes não operacionais isoladas, chaves/dados sintéticos, egress explícito, limites, reset/cleanup, nenhum endpoint operacional e stop authority. Witness/storage devem obedecer ao nível de independência.

## Falhas de reprodutibilidade

Identidade ausente, dependência mutável, desvio não registrado, hash divergente, reset incompleto, seed desconhecido, oráculo ausente ou custódia quebrada impede PASS e produz `INCONCLUSIVE` ou `ABORTED`.

