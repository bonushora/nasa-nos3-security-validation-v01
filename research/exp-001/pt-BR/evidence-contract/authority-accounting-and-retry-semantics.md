# Contabilização de autoridade e semântica de retry EXP001-P0

## Separação de identidades

- `authority_id`: principal/pseudônimo.
- `grant_id`: uma decisão e escopo explícitos.
- `intent_id`: resultado lógico pretendido.
- `command_id`: conteúdo/instância canônica.
- `attempt_id`: entrega ou retry individual.
- `effect_id`: efeito real ou parcialmente observado.

Essas identidades nunca são intercambiáveis.

## Contrato de concessão

Cada intenção permitida requer grant com emissor, sujeito, alvo, operação, restrições, validade, máximo de tentativas quando aplicável, orçamento agregado, digest da política/versão e revogação. Credencial de transporte ou pacote válido não é grant.

Negação, expiração, revogação, mismatch ou política desconhecida produz zero autoridade de despacho e orçamento zero.

## Orçamento de efeito

O orçamento limita efeitos reais, não mensagens/ACKs. O consumo ocorre quando o efeito é verificado ou quando o orçamento fica conservadoramente reservado sob ambiguidade. Tentativa ambígua não restaura orçamento automaticamente.

Estados do ledger: `AVAILABLE`, `RESERVED_AMBIGUOUS`, `CONSUMED_VERIFIED`, `RELEASED_NO_EFFECT` e `EXHAUSTED`, sempre com IDs de evidência.

## Regra de retry

Retry cria novo `attempt_id` sob o mesmo `intent_id`, `grant_id`, escopo e orçamento agregado. Não cria autoridade. Nova autoridade só existe com grant separado e `new_authority_explicit=true`; timeout, restart, repetição do usuário ou nova sequência não bastam.

Antes do retry, a tentativa anterior deve ser:

- `NO_EFFECT_CONFIRMED`: orçamento pode ser liberado conforme o grant;
- `EFFECT_CONFIRMED`: não repetir sem nova concessão;
- `AMBIGUOUS`: orçamento continua reservado e o retry deve ser seguro ou retido;
- `PARTIAL`: ação restante precisa ser definida; ou
- `EVIDENCE_INCOMPLETE`: sem PASS e sem reset silencioso.

## Replay e duplicatas

Duplicata preserva a linhagem ou é rejeitada. Replay recebe zero novo grant. Freshness, nonce, sequência e janela são decisões separadas de sintaxe e validade criptográfica.

## Restart

Autoridade/orçamento sobrevivem ao restart salvo expiração/revogação explícita. Novo `boot_epoch` não cria grant. A recuperação carrega o ledger, reconcilia efeitos e mantém toda reserva ambígua.

## Concorrência

Autoridade compartilhada declara limites por intenção e agregado, mais serialização/comutatividade. O mesmo token não pode ser gasto duas vezes. Causalidade ambígua mantém orçamento reservado e proíbe PASS.

## Invariantes fail-closed

- efeitos não excedem concessões aplicáveis;
- ACK, log, timeout ou restart não concede autoridade;
- efeito não resolvido permanece no ledger;
- liberar orçamento exige evidência positiva de não efeito;
- grant novo não legitima retroativamente efeito anterior; e
- evidência insuficiente nunca produz PASS.

