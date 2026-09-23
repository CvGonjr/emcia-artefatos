# Plano de Implementação do Estúdio de Trabalho

*Conversão da arquitetura planejada em um Code Plugin completo, de F0 a P10*

| | | | |
|---|---|---|---|
| **Código** | EMCIA-IMP-01 | **Versão** | 0.2 |
| **Data** | 17/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 1 — Planejamento | **Passo** | Ação 1.9 |

## 1. Objetivo

Converter a arquitetura do EMCIA-ARQ-01 em um plano de implementação para a Sprint 2, levando o Code Plugin do percurso parcial existente até a cobertura integral do método: F0 a P10, cinco fases, cinco entregáveis ao cliente, seis autorizações internas de emissão, dezoito habilidades HB, quatro agentes AG e cinco itens inegociáveis operantes.

## 2. Escopo e aplicação

O plano aplica-se à implementação interna do Estúdio de Trabalho no Claude Code e às ações 2.1 a 2.6 da Sprint 2. O resultado técnico deve estar disponível antes das ações 2.7 a 2.9, que constroem, executam e selam a representação declarada.

A implementação completa do percurso não amplia a reivindicação da PoC: P6 a P10 serão instrumentados e seus artefatos serão produzidos, mas as fases F3 e F4 não serão apresentadas como validadas em operação real da solução do cliente.

## 3. Conteúdo

### 3.1 Estado de partida e alvo

| Dimensão | Estado de partida | Alvo da Sprint 2 |
|---|---:|---:|
| Etapas operacionais | 8 — F0 a P5 | 13 — F0 a P10 |
| Fases com fechamento | 2 e meia | 5 |
| Autorizações emitíveis | 4 | 6 |
| Habilidades HB | 13 sem código estável | 18 com código estável |
| Agentes AG | 2 sem código estável | 4 com código estável |
| Itens inegociáveis operantes | 1 | 5 |

O caminho para completar o plugin não é apenas engenharia de software. Habilidade é procedimento com critério de saída; portanto, instrumentos ainda não formalizados precisam ser escritos antes de virarem skill.

### 3.2 Decisões documentais adotadas nesta versão

1. **Procedência:** a implementação documental continua usando exclusivamente **D — declarada, I — inferida e V — verificada**. Alterações de taxonomia podem ser avaliadas durante a aplicação, mas não entram nesta versão do plano.
2. **Correspondência de entregáveis:** vale a estrutura controlada do relatório e do método: **E4 encerra P6–P7; E5 encerra P8–P10**.
3. **P3b e P7:** são pontos humanos do percurso. O Code Plugin pode organizar insumos e registrar a sessão, mas não oferece comando que substitua a decisão humana correspondente.
4. **P10:** é recorrente. O playbook deve declarar cadência e o estado precisa registrar a última verificação.

### 3.3 Pacote 1 — Correção de base

| Item | Natureza | Critério de pronto |
|---|---|---|
| Proteção de escrita em `caso/` e `registro/` | Código | Processo do agente não grava por fora do núcleo. |
| Códigos HB e AG nas habilidades e agentes | Mapeamento | Toda implementação remete ao catálogo EMCIA-CAT-01. |
| Critério de verificação executável | Código | Agente não carrega sem critério verificável. |
| Geração do documento após autorização | Código | `emitir` autoriza e o gerador materializa o artefato sem contornar o portão. |
| Suíte negativa acumulada | Teste | Negativa produz evento e não altera o estado. |

### 3.4 Pacote 2 — Fechar F1

| Item | Natureza | Resultado |
|---|---|---|
| Roteiro de levantamento | Redação | Procedimento aplicável em P3b, sem automatizar o julgamento. |
| Instrumentação de P3b | Redação + código | Sessão humana registrada; nenhuma skill conclui a etapa por agente. |
| CTX-01 convertido em procedimento | Redação + código | Regras verificadas entram no contexto com D/I/V e autoria. |
| AG-01 e AG-02 mapeados | Código | Habilidades e critérios de verificação ligados aos códigos oficiais. |
| Portão E2 | Código | E2 só emite com linha de base, sessão e regras com autoria. |

### 3.5 Pacote 3 — Fechar F2

| Item | Natureza | Resultado |
|---|---|---|
| AG-03 — especificação | Código | HB-11, HB-12 e HB-14 mapeadas ao agente. |
| Blueprint em duas partes | Redação + código | E3-D sempre disponível após P4/P5; E3-E apenas quando há caso agêntico. |
| Portão E3 | Código | A decisão tecnológica antecede a especificação por camadas. |

### 3.6 Pacote 4 — Implementar F3

| Item | Natureza | Resultado |
|---|---|---|
| Protocolo de campo por passo | Redação | P6 e P7 possuem entrada, atividade, saída e encerramento. |
| P6 — inserção no fluxo | Redação + código | Estado futuro e ponto de inserção documentados. |
| P7 — autonomia e governança | Redação + código | Atividade humana de fechamento; sem comando que defina autonomia. |
| Inegociável 2 | Código | E4 não emite sem termo de autonomia com três listas. |
| E4 — Guia operacional | Código + template | Geração autorizada após P6/P7. |

### 3.7 Pacote 5 — Implementar F4

| Item | Natureza | Resultado |
|---|---|---|
| P8 — casos de teste | Redação + código | Todo caso crítico possui saída esperada; HB-15/HB-16 integradas. |
| P9 — medição | Redação + código | Ao menos uma métrica de resultado comparável à linha de base; HB-17 integrada. |
| P10 — recalibragem | Redação + código | Cadência por nível, responsável nomeado e última verificação registrada; HB-18 integrada. |
| AG-04 — avaliação | Código | HB-15 a HB-18 mapeadas com critérios verificáveis. |
| Inegociáveis 3, 4 e 5 | Código | E5 recusa caso de teste sem saída esperada, métricas apenas de uso ou responsável não nominal. |
| E5 — Relatório de piloto | Código + template | Produzido em simulação sem alegação de operação real da solução do cliente. |

### 3.8 Relação com as ações da Sprint 2

| Ação | Papel na implementação completa |
|---|---|
| 2.1 | Fecha o roteiro de levantamento, caminho crítico de P3b. |
| 2.2 | Converte CTX-01 em instrumento registrável. |
| 2.3 | Escreve o protocolo de campo necessário a P6–P10. |
| 2.4 | Formaliza leitura de volta, divergência e demais procedimentos transversais. |
| 2.5 | Completa camada de agente/protocolos e o Code Plugin F0–P10; mapeia 18 HB e 4 AG; integra base curada. |
| 2.6 | Completa contexto e dados do caso, com D/I/V e versionamento. |
| 2.7–2.9 | Usa o ambiente concluído para construir, executar e selar o braço declarado. |

### 3.9 Testes adicionais para o percurso completo

A suíte existente deve ganhar os testes negativos abaixo, preservando os anteriores.

| # | Prova |
|---:|---|
| 14 | E4 não emite sem termo de autonomia. |
| 15 | E5 não aceita caso de teste sem saída esperada. |
| 16 | E5 não emite se todas as métricas forem de uso. |
| 17 | E5 não emite com responsável pela recalibragem definido apenas como área. |
| 18 | P7 recusa tentativa de decisão de autonomia por agente. |
| 19 | Etapa recorrente sem cadência declarada não carrega. |
| 20 | Agente sem critério de verificação declarado não carrega. |

### 3.10 Riscos de implementação

| Risco | Sinal | Tratamento |
|---|---|---|
| Código avançar antes dos instrumentos | Skill com descrição genérica e sem critério de saída | Redação antecede implementação. |
| Confundir cobertura com validação operacional | F3/F4 descritas como resultado real | Marcar P6–P10 como execução/simulação da PoC. |
| Deriva de procedência | Nova taxonomia entrar no código antes da decisão do método | D/I/V é contrato desta versão. |
| Portões incompletos | E4/E5 emitíveis sem inegociáveis | Testes 14–20 entram no DoD. |
| Estado recorrente invisível | P10 sem data da última verificação | Cadência e última execução ficam no estado. |

## 4. Condição de aceite

O plano está pronto quando outro implementador consegue executar a Sprint 2 sem decidir novamente o escopo: sabe que o alvo é F0–P10, quais instrumentos bloqueiam cada pacote, quais quatro agentes e dezoito habilidades precisam estar mapeados, como E4 e E5 fecham, quais cinco itens inegociáveis devem operar e quais testes demonstram as novas travas.

## 5. Referências

- EMCIA-ARQ-01 — Arquitetura do Estúdio de Trabalho.
- EMCIA-ESP-01 — Especificação executável do Estúdio de Trabalho.
- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-VER-01 — Plano de verificação.
- EMCIA-LMC-01 — Lean Model Canvas do Estúdio de Trabalho.
- EMCIA-ONI-01 — Onion Planning da implementação do Code Plugin.
- Plano — do percurso parcial ao percurso completo (documento interno, setembro de 2026).

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 17/09/2026 | Celso do Vale | Versão inicial do plano de implementação. | — |
| 0.2 | 17/09/2026 | Celso do Vale | Plano ampliado para o percurso completo F0–P10, com cinco pacotes, cinco inegociáveis e testes 14–20. | — |
