# Modelo de ameaças e fronteiras de confiança EXP001-P0

## Ativos e objetivos

Ativos: autoridade, orçamento de efeito, linhagem comando/efeito, estado, tempo simulado, estado do witness, evidência bruta, configuração, proveniência e classificação. O objetivo é contabilização confiável: cada efeito observado é ligado a autoridade permitida ou permanece explicitamente não resolvido; evidência ausente ou apenas do executor nunca vira prova.

## Atores e falhas

- operador/fixture legítimo com autoridade sintética limitada;
- remetente não autorizado ou de replay;
- receptor, autorizador, dispatcher e executor;
- produtores de telemetria/log/ACK;
- modelo/provedor de estado;
- witness independente e custodiante;
- falhas não maliciosas de rede, fila, scheduler, relógio, armazenamento e restart;
- componente, dependência, configuração ou instrumento comprometido/defeituoso.

## Fronteiras explícitas

| Fronteira | Lado interno | Lado externo/independente | Evidência exigida |
|---|---|---|---|
| TB1 autoridade | emissor e política | transporte/handler | grant ID, escopo, validade, orçamento, decisão |
| TB2 recepção/despacho | ingresso, autorização e dispatcher | interface/modelo de efeito | eventos separados de recepção, autorização e despacho |
| TB3 executor/efeito | handler/driver/mutação | observador read-only | estado antes/depois, identidade e incerteza |
| TB4 executor/witness | logs e contadores do executor | processo/credencial/storage do witness | proveniência e saúde independentes |
| TB5 sistema/telemetria | pipeline de TO/evento/log | captura independente | sequência, drops, filtros e divergência |
| TB6 ciclo de vida | processo/boot epoch | store persistente | identidade de restart, continuidade e recuperação |
| TB7 experimento/controle | orquestrador | avaliador/store bruto | pré-inscrição, entradas imutáveis e separação de papéis |
| TB8 supply chain | fonte/build/imagem/config | verificador de identidade | proveniência recursiva, hashes e SBOM/attestation |

TB8 está aberta porque a proveniência transitiva do NOS3 está `BLOCKED`; a execução física não está pronta.

## Ameaças à validade

- ACK/log emitido antes da conclusão;
- efeito concluído com ACK/telemetria/log perdido;
- duplicação, replay, retry ou recuperação duplica efeito;
- restart perde intenção, conclusão ou consumo de autoridade;
- concorrência disputa estado/orçamento;
- filtros ou contadores derivados ocultam divergência;
- witness compartilha fonte/falha com o executor;
- perda, reordenação ou backpressure cria falsa ausência;
- relógios sugerem ordem inexistente;
- reset incompleto carrega estado;
- deriva de proveniência/configuração invalida comparação;
- oráculo é alterado após observar resultados.

## Premissas rejeitadas

Não se presume exactly-once; pacote/CRC/MAC válido não implica autorização operacional; despacho não implica efeito; ACK/log não prova efeito; ausência de telemetria/ACK não prova ausência; dois canais derivados do executor não são independentes; verdade simulada não é witness automático; contêiner não é por si só fronteira de segurança; documentação não é evidência experimental.

## Falhas do witness

O witness pode perder, duplicar, reordenar, corromper ou atrasar registros; compartilhar falhas; observar estado antigo; perturbar timing; perder journal; ou ser comprometido. Heartbeat, gaps, drops, incerteza, continuidade, independência e calibração devem ser evidência. Falha decisiva produz `INCONCLUSIVE` ou `ABORTED`, nunca PASS.

## Exclusões

P0 não testa hardware de voo, redes operacionais, credenciais reais, efeitos físicos/radiação, força criptográfica ou certificação. Não afirma vulnerabilidade do NOS3.

