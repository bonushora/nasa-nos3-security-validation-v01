# SSSVL — Pesquisa de validação de segurança sobre NASA NOS3

[English](README.en.md) · [Índice bilíngue](README.md)

O SSSVL (Space Systems Security Validation Lab) é um programa de pesquisa independente que desenvolve métodos reprodutíveis para validar efeitos relevantes à segurança em software espacial simulado. Este repositório contém a baseline documental e o protocolo científico bilíngue EXP001-P0 do projeto `NASA-NOS3-SECURITY-VALIDATION-v0.1`.

> **Esta é uma iniciativa de pesquisa independente, sem afiliação, patrocínio ou endosso da NASA.**

NASA NOS3, NASA cFS e F´ são objetos de pesquisa distintos. Seu uso ou citação não estabelece endosso, prontidão operacional, qualificação de segurança ou aptidão para voo.

## Estado atual

```text
PUB_R1_PUBLICATION_GREEN=PASS
EXP001_P0_DOCUMENTATION_GREEN=PASS
BILINGUAL_PUBLICATION_GREEN=PASS
NOS3_TRANSITIVE_PROVENANCE=BLOCKED
NOS3_EXECUTION=NOT_AUTHORIZED
ADVERSARIAL_EXPERIMENTS=NOT_EXECUTED
EXPERIMENTAL_SECURITY=NOT_QUALIFIED
```

PUB-R1 já publicou a baseline documental inglesa validada no commit `778eadc9e9c091657370ba01322ac0ddf7585f2d`. Os arquivos históricos EN-R1 mantêm suas declarações originais de autorização/publicação como evidência selada. O estado acima descreve o candidato bilíngue PUB-R2 e não reescreve esses registros.

## EXP001-P0

**Verificação independente de efeitos de comando sob repetição e recuperação em sistemas espaciais simulados** é um protocolo científico experimental, não um relatório de experimentos executados.

A hipótese central é que autorização, despacho, conclusão do efeito e verificação independente são estados diferentes. ACK ou log do executor não prova necessariamente que um efeito ocorreu, e ACK ausente não prova que nenhum efeito ocorreu.

O EXP001-P0 fornece:

- hipóteses testáveis e nulas H1–H8;
- cenários sintéticos S01–S10;
- contrato do Independent Effect Witness;
- semântica canônica de comando, autoridade, tentativa e efeito;
- oráculos determinísticos e regras PASS/FAIL/INCONCLUSIVE/ABORTED;
- requisitos de proveniência, custódia, isolamento e reprodutibilidade; e
- gates documentais e físicos.

O witness independente é proposto e especificado contratualmente, mas não foi implementado nem calibrado. Nenhum NOS3, cFS, F´, contêiner, simulador ou experimento adversarial foi executado.

## Navegação

- [Índice bilíngue EXP001-P0](research/exp-001/README.md)
- [Protocolo científico](research/exp-001/pt-BR/protocol/EXP001-P0-scientific-protocol-v0.1.md)
- [Hipóteses](research/exp-001/pt-BR/protocol/hypotheses-and-null-hypotheses.md)
- [Cenários sintéticos](research/exp-001/pt-BR/protocol/synthetic-fault-scenarios.md)
- [Independent Effect Witness](research/exp-001/pt-BR/evidence-contract/independent-effect-witness-contract.md)
- [Schema canônico](research/exp-001/pt-BR/evidence-contract/canonical-command-effect-event-schema.json)
- [Oráculos determinísticos](research/exp-001/pt-BR/protocol/deterministic-oracles.md)
- [Matriz de prontidão](research/exp-001/pt-BR/acceptance/experimental-readiness-matrix.md)
- [Revisão de equivalência](research/exp-001/publication/equivalence-matrix.pt-BR.md)
- [Revisão de divulgação](research/exp-001/publication/disclosure-review.pt-BR.md)

## Evidência e limitações

A referência superior fixa do NOS3 continua no commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`. O grafo transitivo não está congelado: 44 gitlinks candidatos permanecem `PARTIAL`, três entradas permanecem `UNAVAILABLE` e a proveniência recursiva está bloqueada.

Assim, a prontidão para experimento físico está bloqueada. PASS documental não estabelece propriedade de segurança, vulnerabilidade, exactly-once, autorização operacional, qualificação de voo ou certificação.

## Histórico do repositório

Os caminhos existentes `docs/`, `governance/`, `evidence/` e `archive/` são a baseline inglesa publicada anteriormente. PUB-R2 adiciona derivados científicos bilíngues sem renomear ou mover silenciosamente o material histórico selado.

Todos os nomes NASA, NOS3, cFS, F´, CCSDS e de terceiros pertencem aos respectivos titulares e identificam somente objetos ou fontes de pesquisa.

