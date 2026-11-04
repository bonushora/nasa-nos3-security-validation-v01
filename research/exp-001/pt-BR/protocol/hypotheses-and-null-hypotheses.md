# Hipóteses e hipóteses nulas EXP001-P0

Todas as hipóteses tratam de futuras observações controladas. Nenhuma descreve propriedade já demonstrada do NOS3.

| ID | Hipótese testável | Hipótese nula | Observável primário | Regra de falsificação/rejeição |
|---|---|---|---|---|
| H1 | Recepção, autorização, despacho, observação, verificação independente e reconciliação são estados distinguíveis. | H1₀: esses estados não podem ser distinguidos com confiabilidade. | caminho de eventos por `intent_id` | Rejeitar H1 se os estados exigidos não puderem ser atribuídos separadamente. |
| H2 | ACK ou log de sucesso do executor, isoladamente, é insuficiente para provar conclusão do efeito. | H2₀: ACK/log de sucesso sempre concorda com o efeito verificado. | ACK/log versus estado independente | Um único desacordo válido apoia H2; rejeição exige cobertura suficiente sem desacordos. |
| H3 | Ausência de ACK, isoladamente, é insuficiente para provar ausência de efeito. | H3₀: todo ACK ausente corresponde a nenhum efeito verificado. | cenário de perda de ACK | Um efeito verificado com ACK ausente rejeita H3₀. |
| H4 | Retries podem ser contabilizados no escopo original e orçamento agregado sem criar autoridade silenciosa. | H4₀: tentativas não podem ser distinguidas nem limitadas pelo orçamento. | concessão, tentativas e consumo | Rejeitar H4 se houver tentativa sem linhagem ou efeito excedente sem nova concessão. |
| H5 | A reconciliação distingue interrupção pré-efeito de interrupção pós-efeito/pré-log quando a evidência está completa. | H5₀: as posições são observacionalmente indistinguíveis. | épocas, journal e estado final | Rejeitar H5 se o oráculo não distinguir os pontos dentro da incerteza declarada. |
| H6 | Witness separado e sem autoridade detecta desacordo entre executor/log/telemetria e estado independente. | H6₀: o witness não adiciona evidência discriminante. | detecção de divergência e controle falso-positivo | Rejeitar H6 se o witness derivar do executor ou falhar nos controles. |
| H7 | Entrega duplicada e replay são distinguíveis de novo comando autorizado por identidades e freshness. | H7₀: replay/duplicata e nova intenção são indistinguíveis. | linhagem e decisão de replay | Rejeitar H7 se bytes repetidos consumirem novo orçamento sem autorização explícita. |
| H8 | Comandos concorrentes sob autoridade compartilhada podem ser reconciliados com serialização e orçamento declarados. | H8₀: efeitos concorrentes não podem ser atribuídos ou orçados. | grafo causal, cronograma, estado e ledger | Rejeitar H8 se uma execução válida produzir efeito final não contabilizado ou não classificável. |

## Tratamento estatístico e lógico

H2 e H3 são hipóteses de contraexemplo: um desacordo sólido refuta a afirmação universal nula. H1 e H4–H8 exigem limiares pré-definidos de completude e repetibilidade antes da execução; P0 não inventa limiares sem calibração.

Comparações múltiplas, confiança, tamanho de efeito e regras de parada devem ser pré-inscritos. Execução subdimensionada ou com evidência incompleta é `INCONCLUSIVE`, nunca apoio por ausência de falha observada.

