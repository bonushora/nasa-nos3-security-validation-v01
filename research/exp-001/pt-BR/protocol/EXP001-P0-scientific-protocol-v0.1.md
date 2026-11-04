# Protocolo científico EXP001-P0 v0.1

## Título

**Verificação independente de efeitos de comando sob repetição e recuperação em sistemas espaciais simulados**

## Estado e autoridade

`EXP001_P0_DOCUMENTATION_GREEN` pode ser PASS após validação documental. A execução física permanece `NOT_AUTHORIZED`.

- Programa: SSSVL — Space Systems Security Validation Lab.
- Governança: BH-SEP v2.3 / BH-SDP v2.3.
- Referência do objeto de estudo: NASA NOS3 no commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`.
- Proveniência transitiva: `BLOCKED`.
- Execução de NOS3/cFS/F´/contêiner/simulador: `NOT_AUTHORIZED`.
- Experimentos adversariais: `NOT_EXECUTED`.
- Segurança experimental: `NOT_QUALIFIED`.

Este protocolo é um projeto de pesquisa independente. Ele não afirma que o NOS3 atualmente viola, implementa ou garante qualquer propriedade proposta.

## Pergunta de pesquisa

Efeitos do sistema observados de forma independente podem ser distinguidos com confiabilidade da autorização de comando, do despacho, dos reconhecimentos, da telemetria e dos logs do executor sob repetição, replay, interrupção e recuperação?

## Hipótese principal

Autorização de comando, despacho, conclusão do efeito e verificação independente do efeito são estados diferentes. Um reconhecimento bem-sucedido ou log do executor não estabelece necessariamente que ocorreu um efeito, e a ausência de reconhecimento não estabelece que nenhum efeito ocorreu.

As hipóteses testáveis e nulas estão em [hipóteses](hypotheses-and-null-hypotheses.md).

## Classificação científica

Cada afirmação usa uma das quatro classes:

- **D — documentado:** comportamento descrito na baseline documental fixa do NOS3, como caminhos de comando/telemetria, modelos de simulador, interfaces mediadas pelo NOS Engine e caminhos de comando fora de banda.
- **P — proposto:** instrumentação de laboratório, witness independente, esquema de eventos, fixture de falha ou oráculo especificado aqui, mas ainda não implementado.
- **H — hipotético:** propriedade de segurança ou confiabilidade a ser testada, nunca presumida verdadeira.
- **O — observado:** resultado produzido por experimento autorizado. Em P0 não existem resultados de classe O.

Uma afirmação arquitetural D não prova uma propriedade H. Instrumentação P só se torna evidência O após implementação, calibração, estado saudável e execução sob identidade experimental congelada.

## Unidade experimental e variáveis

A futura unidade experimental é uma execução isolada de um cenário contra um objeto/configuração congelado, com `experiment_id` e `run_id` únicos.

Variáveis independentes incluem cenário, número de tentativas, replay, ponto de interrupção, época de reinício, escalonamento concorrente e falhas controladas de reconhecimento/telemetria/log. Variáveis dependentes incluem progressão dos estados, contagem independente de efeitos, estado final, reconciliação, completude da evidência, incerteza temporal e divergência entre executor, telemetria e witness.

Devem ser controlados: identidade de fonte, gitlinks, imagens, binários, ferramentas, XML/configuração, dicionários, tabelas cFS/F´, semente, estado inicial, tempo simulado, taxa de tick, recursos, topologia, concessões de autoridade, orçamentos de efeito, versão do oráculo e versão do witness.

## Baselines comparadoras

1. **B0 controle negativo:** transporte/formato válido, mas autorização negada; zero despacho e zero efeito.
2. **B1 controle nominal:** um comando autorizado, um despacho, um efeito verificado independentemente e canais auxiliares consistentes.
3. **B2 controle do witness:** transição sintética conhecida entregue diretamente à fixture do witness, sem execução do sistema.
4. **B3 controle sem comando:** mesma duração e estado inicial, mas nenhum comando.
5. **B4 controle de instrumentação:** mesma fixture benigna com witness habilitado/desabilitado, quando autorizado, para estimar perturbação.

Comparação cFS versus F´ só é válida após demonstrar equivalência suficiente de instrumentação e semântica para a métrica declarada.

## Modelo de medição e incerteza

Cada evento registra tick simulado, tempo monotônico do produtor, `boot_epoch`, sequência e limite de incerteza. Ordem de relógio de parede entre processos não é causalidade. Causalidade usa identificadores e vínculos explícitos; tempo é evidência auxiliar.

Antes de qualquer execução física, a calibração deve limitar resolução temporal, atraso de captura, perda, janela de reordenação, backpressure, granularidade do estado e perturbação da instrumentação. Se o oráculo depender de ordem mais estreita que a incerteza combinada, o resultado é `INCONCLUSIVE`.

## Repetições e escalonamento

P0 não inventa uma contagem universal de repetições antes de medir variância. Uma futura pré-inscrição deve fixar a contagem por justificativa de potência ou precisão antes da coleta. No mínimo, fixtures determinísticas devem reproduzir em três repetições limpas; escalonamentos estocásticos usam conjunto de sementes pré-inscrito adequado ao intervalo de confiança. Execuções com witness não saudável não contam como repetições bem-sucedidas.

A ordem dos cenários deve ser randomizada ou contrabalançada quando houver carryover. Cada execução começa em reset verificado ou estado de recuperação explicitamente declarado.

## Limite do procedimento

Uma futura execução, sob nova autoridade, deverá:

1. verificar todos os gates e a identidade imutável;
2. resetar e atestar o estado inicial;
3. iniciar e verificar a saúde do witness;
4. emitir a concessão e o orçamento pré-inscritos;
5. aplicar exatamente um cronograma de estímulo;
6. capturar todos os canais sem alterar a classificação;
7. parar nos critérios de aborto;
8. reconciliar efeitos independentemente de ACKs/logs;
9. preservar evidência bruta antes da análise; e
10. avaliar o oráculo determinístico pré-inscrito.

Essas etapas são especificações, não autorização de execução.

## Plano de análise

Saídas primárias: conformidade da máquina de estados, contagem de efeitos versus orçamento, despachos/efeitos sem par, duplicações, consumo de autoridade, completude e reconciliação final. Saídas secundárias: latências e divergências entre canais, sempre com incerteza.

Nenhum registro ausente é imputado como sucesso. ACK ou log do executor não substitui evidência independente. Observações exploratórias ficam separadas dos testes pré-inscritos.

## Decisão e parada

Resultados possíveis: `PASS`, `FAIL`, `INCONCLUSIVE` ou `ABORTED`, conforme [regras de decisão](../acceptance/decision-rules.md). Escape de contenção, identidade divergente, witness não saudável, excesso de recurso, estado não resetável, endpoint operacional inesperado ou alvo ambíguo exige `ABORTED`.

## Contratos relacionados

- [Modelo de ameaças e fronteiras](threat-model-and-trust-boundaries.md)
- [Cenários sintéticos](synthetic-fault-scenarios.md)
- [Oráculos determinísticos](deterministic-oracles.md)
- [Independent Effect Witness](../evidence-contract/independent-effect-witness-contract.md)
- [Autoridade e retries](../evidence-contract/authority-accounting-and-retry-semantics.md)
- [Proveniência e reprodutibilidade](../evidence-contract/evidence-provenance-and-reproducibility.md)
- [Matriz de prontidão](../acceptance/experimental-readiness-matrix.md)

