# Especificação de cenários sintéticos EXP001-P0

Todos os cenários são especificações classe P, não execuções. Nenhum afirma não conformidade existente do NOS3. Entradas, autoridade, estado e falhas devem ser sintéticos e não operacionais.

## S01 — Comando único bem-sucedido e efeito único verificado

- **Preconditions:** estado inicial limpo e atestado; witness saudável; um alvo determinístico.
- **Authority/effect budget:** G1 permite uma intenção e exatamente um efeito; uma tentativa inicial.
- **Stimulus:** enviar um comando autorizado sem falha injetada.
- **Expected observations:** os sete estados canônicos ocorrem uma vez em ordem causal; ACK/log/telemetria são auxiliares consistentes.
- **Witness requirements:** estado antes/depois, contagem, saúde e vínculo causal independentes.
- **Failure/ambiguity:** zero ou múltiplos efeitos, evento obrigatório ausente, witness não saudável ou estado final incerto.
- **Deterministic oracle:** uma intenção autorizada, um despacho, um efeito verificado e orçamento reconciliado 1/1.
- **Acceptance:** PASS somente com oráculo e saúde completos; caso contrário FAIL, INCONCLUSIVE ou ABORTED.
- **Reproducibility:** identidades, semente, estado, grant, bytes, timing e três repetições limpas congelados.

## S02 — Comando rejeitado antes do despacho

- **Preconditions:** estado limpo; witness saudável; comando estruturalmente válido fora do escopo ou explicitamente negado.
- **Authority/effect budget:** G2 permite zero efeitos para comando/alvo.
- **Stimulus:** enviar uma vez o comando negado.
- **Expected observations:** `COMMAND_RECEIVED` e `COMMAND_AUTHORIZED` negativo; nenhum despacho, tentativa ou efeito.
- **Witness requirements:** observação independente de não mudança durante toda a janela e evidência de saúde/drops.
- **Failure/ambiguity:** despacho/efeito, decisão ausente, mudança de fundo ou janela incompleta.
- **Deterministic oracle:** negação ligada ao comando; despacho 0; delta independente 0; orçamento 0/0.
- **Acceptance:** PASS para rejeição correta; FAIL para despacho/efeito atribuível; INCONCLUSIVE se não mudança não for demonstrável.
- **Reproducibility:** política/versão, bytes, janela, tolerância e controle negativo fixos.

## S03 — Comando despachado sem efeito

- **Preconditions:** witness saudável; fixture capaz de suprimir efeito depois do despacho sem mudar autorização.
- **Authority/effect budget:** uma intenção autorizada; máximo de um efeito.
- **Stimulus:** autorizar/despachar uma vez e suprimir no ponto pós-despacho/pré-efeito.
- **Expected observations:** recepção, autorização, despacho e tentativa; nenhum efeito independente; reconciliação falha/timeout explícita.
- **Witness requirements:** estado independente e janela suficiente para distinguir atraso de ausência.
- **Failure/ambiguity:** efeito tardio, resolução insuficiente ou ponto de supressão sem evidência.
- **Deterministic oracle:** um despacho/tentativa, zero efeito verificado e nenhuma possibilidade tardia na janela justificada.
- **Acceptance:** PASS se nenhum efeito e nenhum falso sucesso; FAIL se log do executor prevalecer contra o estado.
- **Reproducibility:** hook, janela, tolerância, estado inicial e repetições fixos.

## S04 — Efeito concluído com reconhecimento perdido

- **Preconditions:** caminho nominal, captura independente e fixture de drop de ACK pós-efeito.
- **Authority/effect budget:** uma intenção e exatamente um efeito; retry inicialmente desabilitado.
- **Stimulus:** executar e descartar o ACK após a conclusão.
- **Expected observations:** estados de efeito até verificação; ACK ausente; reconciliação registra o efeito.
- **Witness requirements:** evidência independente de ACK, log e transporte de telemetria.
- **Failure/ambiguity:** ACK descartado no ponto errado, estado antigo ou conclusão não estabelecida.
- **Deterministic oracle:** efeito verificado 1, ACK 0, orçamento 1/1.
- **Acceptance:** PASS se ACK ausente não significar ausência; FAIL se novo orçamento surgir automaticamente.
- **Reproducibility:** ponto de drop, marcador causal, timeout e snapshot preservados.

## S05 — Retry após conclusão ambígua

- **Preconditions:** primeira tentativa pode concluir com resposta perdida; política de retry pré-inscrita.
- **Authority/effect budget:** uma intenção, orçamento agregado 1 em A1/A2, salvo nova concessão explícita.
- **Stimulus:** perder resposta de A1 e enviar A2 com mesmo `intent_id` e novo `attempt_id`.
- **Expected observations:** ambas mantêm G5; reconciliação impede/detecta segundo efeito; ambiguidade persiste até estado independente.
- **Witness requirements:** identidade/contagem durável entre retries e épocas; deduplicação do executor não basta.
- **Failure/ambiguity:** tentativas sem vínculo, primeiro efeito não resolvido ou contagem imprecisa.
- **Deterministic oracle:** efeitos verificados agregados ≤1; segundo efeito sem grant novo é FAIL.
- **Acceptance:** PASS para um efeito contabilizado ou retry suprimido; INCONCLUSIVE se a contagem continuar ambígua.
- **Reproducibility:** timeout, chave de idempotência, linhagem, cronograma, grant e estado final fixos.

## S06 — Entrega duplicada e replay

- **Preconditions:** estado limpo; fixture duplica entrega e repete bytes; política de freshness fixa.
- **Authority/effect budget:** uma intenção, orçamento agregado 1; duplicatas/replays não recebem nova autoridade.
- **Stimulus:** entregar duas vezes em hop controlado e repetir dentro/fora da janela.
- **Expected observations:** classificação duplicata/replay, identidade preservada, rejeição/idempotência e nenhum efeito excedente.
- **Witness requirements:** digest dos bytes, sequência por hop, freshness e contagem independente.
- **Failure/ambiguity:** origem/hop desconhecido, janela incerta ou bytes viram nova intenção sem grant.
- **Deterministic oracle:** um grant; total de efeitos ≤1; cada entrega extra contabilizada.
- **Acceptance:** FAIL para segundo efeito não concedido; PASS para classificação correta; INCONCLUSIVE para hop incompleto.
- **Reproducibility:** hop, quantidade, atraso, janela, bytes e semente registrados.

## S07 — Reinício antes da conclusão do efeito

- **Preconditions:** journal persistente; restart controlado após autorização/despacho e antes do efeito observado.
- **Authority/effect budget:** uma intenção, orçamento 1 entre épocas.
- **Stimulus:** reiniciar no limite pré-efeito e permitir recuperação.
- **Expected observations:** novo `boot_epoch`, intenção preservada/abandonada explicitamente, nenhum efeito oculto e reconciliação determinística.
- **Witness requirements:** continuidade independente, estados antes/depois, marcador de restart e gaps.
- **Failure/ambiguity:** fronteira sem evidência, mudança em intervalo cego ou ledger perdido.
- **Deterministic oracle:** efeito final 0 com cancelamento ou 1 sob grant original; nunca não contabilizado.
- **Acceptance:** PASS para recuperação reconciliada; FAIL para duplicação/não autorização; INCONCLUSIVE para intervalo cego.
- **Reproducibility:** gatilho, marcador, persistência, timeout e estado inicial fixos.

## S08 — Reinício após efeito e antes do log de sucesso

- **Preconditions:** hook pós-efeito/pré-log; witness e ledger persistentes.
- **Authority/effect budget:** uma intenção, um efeito total entre restarts.
- **Stimulus:** concluir/verificar o efeito e reiniciar antes de persistir log/ACK.
- **Expected observations:** efeito verificado na época anterior, log ausente e recuperação sem repetição.
- **Witness requirements:** registro pré-restart durável e cadeia contínua.
- **Failure/ambiguity:** timing incerto, journal não durável ou efeito reversível sem traço.
- **Deterministic oracle:** contagem permanece 1; recuperação reconcilia e não cria orçamento.
- **Acceptance:** FAIL se repetir sem grant; PASS para um efeito; INCONCLUSIVE se continuidade falhar.
- **Reproducibility:** posição do hook, flush, época, estado final e cronograma preservados.

## S09 — Comandos concorrentes com autoridade compartilhada

- **Preconditions:** duas intenções distintas sobre estado compartilhado; regra de serialização/comutatividade e scheduler determinístico/semente.
- **Authority/effect budget:** grant compartilhado com limites por intenção e agregado; sem empréstimo implícito.
- **Stimulus:** liberar ambos conforme cronograma pré-inscrito.
- **Expected observations:** linhagens separadas, ordem/resultado permitido, ledger completo e estado final verificado.
- **Witness requirements:** IDs causais, granularidade suficiente, evidência do scheduler e nenhuma autoridade de comando.
- **Failure/ambiguity:** intermediários não resolvidos, cronograma divergente ou histórias finais sem atribuição.
- **Deterministic oracle:** multiconjunto de efeitos e estado final correspondem a resultado permitido e ao orçamento.
- **Acceptance:** PASS para resultado permitido e atribuído; FAIL para perda/duplicação/excesso; INCONCLUSIVE para causalidade ambígua.
- **Reproducibility:** barreira, semente, scheduler, estado, divisão de autoridade e repetições registrados.

## S10 — Telemetria ou log inconsistente com estado independente

- **Preconditions:** observador independente saudável; fixture altera apenas canal auxiliar.
- **Authority/effect budget:** um efeito permitido ou controle negativo de zero efeito.
- **Stimulus:** produzir o resultado declarado enquanto telemetria/log relata o oposto.
- **Expected observations:** divergência explícita; canal auxiliar não prevalece sobre estado independente.
- **Witness requirements:** evidência independente, proveniência do canal, sequência/drop/filtro e saúde.
- **Failure/ambiguity:** witness deriva do canal, estado antigo ou manipulação afeta o efeito real.
- **Deterministic oracle:** classificação segue o estado independente e marca o canal como contraditório.
- **Acceptance:** PASS se detectar/classificar; FAIL se evidência falsa virar prova; INCONCLUSIVE se independência falhar.
- **Reproducibility:** canal, transformação, timing, estado, contradição e controle fixos.

## Restrições globais

Todo cenário exige esquema canônico, identidade imutável, autoridade sintética, orçamento explícito, witness calibrado, oráculo pré-inscrito, preservação bruta e quatro estados de decisão. Evidência insuficiente nunca vira PASS.

