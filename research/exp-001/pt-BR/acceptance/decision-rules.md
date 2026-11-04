# Regras de decisão EXP001-P0

## Vocabulário

### PASS

Todos os invariantes pré-inscritos são satisfeitos; autoridade/efeitos estão completos; evidência independente é saudável e suficiente; proveniência/configuração conferem; nenhum aborto ocorreu; e todo efeito está reconciliado. PASS vale apenas para hipótese, objeto, configuração e janela testados.

### FAIL

Evidência completa, saudável e atribuível demonstra violação: efeito sem grant, contagem acima do orçamento, duplicação de recuperação, contradição não detectada ou classificação determinística errada. FAIL não representa evidência ausente ou impossibilidade de executar.

### INCONCLUSIVE

A execução ficou contida, mas a evidência não decide: gap do witness, incerteza excessiva, efeito ambíguo, janela incompleta, causalidade não resolvida, repetições insuficientes ou comparador inválido. Evidência insuficiente nunca é PASS.

### ABORTED

A execução deve parar ou fica inválida por escape de contenção, mismatch de identidade/proveniência, endpoint operacional, autoridade de comando no witness, estado não resetável, excesso de recurso, desvio não aprovado ou perda do controle de parada. Não se conclui PASS/FAIL de segurança.

## Precedência

1. Validar autorização, identidade, proveniência, contenção e stop control; falha produz `ABORTED` ou impede iniciar.
2. Validar schema, custódia, saúde, calibração, completude e incerteza; insuficiência decisiva produz `INCONCLUSIVE`.
3. Avaliar invariantes; violação demonstrada produz `FAIL`.
4. Confirmar todos os critérios e repetições; só então `PASS`.

A precedência não esconde violação demonstrada por causa de telemetria auxiliar ausente. O rastreio registra cada achado.

## Requisitos universais de PASS

- identidade exata e cenário autorizado;
- autoridade sintética e orçamento explícito;
- IDs causais para cada tentativa/efeito;
- witness independente, saudável e sem autoridade de comando;
- janela e incerteza calibradas;
- evidência bruta selada antes do oráculo;
- oráculo/rastreio reproduzidos;
- controle negativo e reset válidos;
- repetições satisfeitas; e
- nenhum efeito parcial/não resolvido omitido.

## Condições universais de FAIL

- efeito verificado sem grant;
- efeitos acima do orçamento;
- comando negado produz despacho/efeito;
- retry/replay cria efeito adicional não autorizado;
- restart duplica ou oculta efeito sob evidência completa;
- canal do executor é aceito como prova independente;
- contradição obrigatória não aparece apesar de witness saudável; ou
- estado final/multiconjunto viola o conjunto permitido.

## Interpretação

PASS de cenário não estabelece segurança, exactly-once, prontidão operacional, qualificação de voo ou comportamento fora da configuração. “Nenhuma falha observada” não significa “seguro”.

