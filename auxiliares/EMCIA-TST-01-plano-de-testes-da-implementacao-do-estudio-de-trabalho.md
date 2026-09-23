# Plano de Testes da Implementação do Estúdio de Trabalho

*Verificação técnica do Code Plugin e dos controles executáveis do método F0–P10*

| | | | |
|---|---|---|---|
| **Código** | EMCIA-TST-01 | **Versão** | 0.1 |
| **Data** | 17/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 1 — Planejamento | **Passo** | Ação 1.9 |

## 1. Objetivo

Definir como será verificada a implementação do Estúdio de Trabalho em formato Code Plugin, demonstrando que o software representa corretamente o método EMCIA de F0 a P10, aplica as travas de camada, preserva a procedência D/I/V, controla o avanço entre etapas, condiciona a emissão dos entregáveis aos itens inegociáveis e deixa evidência auditável de toda recusa.

O EMCIA-TST-01 testa **conformidade da implementação com o método**. Ele não substitui o EMCIA-VER-01, que verifica a hipótese metodológica por comparação entre a execução declarada e a execução em campo. Também não avalia se a solução empresarial especificada para o cliente produz resultado operacional.

## 2. Escopo e aplicação

Entram no plano de testes: `eiac-nucleo`, `eiac-campo`, `registro/playbook.json`, estado do caso, guardas, validadores, geração de eventos, selamento, habilidades HB, agentes AG, etapas F0–P10, portões de E1–E5 e os cinco itens inegociáveis.

A taxonomia documental de procedência desta versão permanece **D — declarada, I — inferida e V — verificada**. Alterações posteriores de implementação não mudam este contrato sem revisão formal do documento.

Ficam fora: desempenho intrínseco do modelo de linguagem, implantação da solução empresarial do cliente, integrações reais com ERP/CRM/portais e comprovação de resultado financeiro do caso de uso.

## 3. Conteúdo

### 3.1 Princípios de teste

1. **Negativa precisa deixar rastro.** Uma tentativa proibida só é considerada corretamente bloqueada quando o estado válido permanece inalterado e o evento correspondente é registrado.
2. **Controle positivo é obrigatório.** Uma trava que recusa tudo também está quebrada; por isso cada grupo crítico precisa de ao menos um cenário válido que passe.
3. **Comportamento correto não é prova de trava.** O modelo pode obedecer às instruções sem acionar a guarda. A verificação deve provocar deliberadamente a violação.
4. **Mesma habilidade, nível diferente, resultado diferente.** A fronteira deslocável precisa ser testada em pares de cenários.
5. **Método e software são testados separadamente.** O TST-01 verifica se o software cumpre o contrato; o VER-01 verifica se o método produz a evidência esperada.
6. **F3 e F4 são verificadas como percurso e portão, não como resultado operacional real da solução do cliente.**

### 3.2 Objetos sob teste

| Objeto | O que precisa ser demonstrado |
|---|---|
| `eiac-nucleo` | Guardas, validação, estado, portões, eventos e selamento operam sem depender de julgamento do LLM. |
| `eiac-campo` | Apenas habilidades compatíveis com a camada vigente podem ser carregadas; procedimentos humanos não são substituídos por comandos de agente. |
| Playbook do caso | Toda etapa declara camada por nível, modalidade, portão, inegociáveis e, quando aplicável, cadência e critério de verificação. |
| Registro do caso | Escrita passa pelo núcleo; procedência D/I/V e autoria são obrigatórias; fontes citadas são rastreáveis. |
| Percurso F0–P10 | O caso avança apenas quando os critérios de encerramento e portões correspondentes são satisfeitos. |
| Entregáveis E1–E5 | A emissão é autorizada somente quando os requisitos da fase e os inegociáveis aplicáveis estão cumpridos. |

### 3.3 Classes de teste

| Classe | Finalidade | Evidência mínima |
|---|---|---|
| Estrutural | Validar schema, playbook, códigos e campos obrigatórios. | saída do validador + arquivo rejeitado/aceito |
| Guarda | Provar que uma tentativa fora da camada é recusada. | código de retorno + `TentativaNegada` |
| Procedência e fonte | Impedir registro sem D/I/V, autoria ou fonte válida. | recusa/aceite + evento com referência |
| Estado e portões | Impedir avanço ou emissão prematuros. | estado anterior/posterior + evento |
| Selamento e auditoria | Provar autoria humana, imutabilidade relativa e trilha. | commit/evento/autor |
| Fronteira por nível | Provar que a mesma etapa muda de comportamento conforme N1/N2/N3. | par de testes com resultados opostos |
| Percurso completo | Demonstrar F0–P10 e E1–E5 em simulação controlada. | registro do percurso + entregáveis autorizados |
| Integração com a superfície | Provar que o Claude Code realmente aciona as travas e não apenas obedece às instruções. | execução dentro de um caso + eventos de recusa |

### 3.4 Linha de base da suíte atual

Na revisão de 17/09/2026, o arquivo `testes/negativos.sh` do repositório `CvGonjr/emcia-marketplace` contém **26 verificações executáveis**: 22 negativas e 4 controles positivos. A numeração do script vai de 1 a 25 e inclui o caso `2b`; o TST-01 cria IDs estáveis próprios para não depender dessa numeração operacional.

| ID TST | Script | Tipo | Prova | Esperado |
|---|---:|---|---|---|
| TST-001 | 1 | Negativo | Carregar habilidade EX4 por agente | Recusa. |
| TST-002 | 2 | Negativo | Escrita direta em `caso/` | Recusa. |
| TST-003 | 2b | Negativo | Bash redirecionando escrita para `caso/` | Recusa. |
| TST-004 | 3 | Negativo | Gravar asserção sem procedência | Recusa. |
| TST-005 | 4 | Positivo | Gravar asserção válida | Aceite. |
| TST-006 | 5 | Negativo | Encerrar P3b sem sessão registrada | Recusa. |
| TST-007 | 6 | Negativo | Usar identificador de agente como autor | Recusa. |
| TST-008 | 7 | Negativo | Emitir E2 com portão fechado | Recusa. |
| TST-009 | 8 | Negativo | Carregar playbook sem lista de inegociáveis | Recusa. |
| TST-010 | 9 | Negativo | Em N3, carregar habilidade de P1 classificada como EX3 | Recusa. |
| TST-011 | 10 | Positivo | Em N1, carregar a mesma habilidade de P1 classificada como EX2 | Aceite. |
| TST-012 | 11 | Negativo | Operar etapa pós-F0 sem nível apurado | Recusa. |
| TST-013 | 12 | Negativo | Encerrar F0 sem nível | Recusa. |
| TST-014 | 13 | Negativo | Playbook com camada plana em vez de camada por nível | Recusa. |
| TST-015 | 14 | Negativo | Apurar nível inexistente no playbook | Recusa. |
| TST-016 | 15 | Negativo | Apurar nível com autor-agente | Recusa. |
| TST-017 | 16 | Positivo | Apuração válida de nível por pessoa | Grava nível e evento `NivelApurado`. |
| TST-018 | 17 | Positivo | Encerrar F0 após nível válido | Aceite. |
| TST-019 | 18 | Negativo | Selar caso com autor-agente | Recusa pelo motivo de autoria. |
| TST-020 | 19 | Negativo | Selar fora de repositório Git | Recusa pelo motivo correto. |
| TST-021 | 20 | Positivo | Selamento válido | Commit com autor nomeado + `SeloAplicado`. |
| TST-022 | 21 | Negativo | Selar novamente sem alteração | Recusa por ausência de mudança. |
| TST-023 | 22 | Comparativo | Consultar fronteira em N2 e N1 | Aviso de fronteira muda com o nível. |
| TST-024 | 23 | Negativo | Verificar P3b em níveis distintos | P3b permanece não delegável. |
| TST-025 | 24 | Negativo | Citar documento que não existe em `fontes/` | Recusa. |
| TST-026 | 25 | Positivo | Citar documento presente em `fontes/` | Grava e registra hash na trilha. |

### 3.5 Extensão obrigatória para o percurso completo F0–P10

A cobertura integral exige, no mínimo, os testes adicionais abaixo. Eles não substituem os 26 atuais.

| ID TST | Requisito | Tipo | Pré-condição / tentativa | Resultado esperado |
|---|---|---|---|---|
| TST-027 | Inegociável 2 / P7 | Negativo | Solicitar emissão de E4 sem termo de autonomia válido | E4 recusado; estado inalterado; evento registrado. |
| TST-028 | Inegociável 3 / P8 | Negativo | Registrar caso de teste sem saída esperada e tentar satisfazer P8/E5 | P8 não fecha e E5 permanece bloqueado. |
| TST-029 | Inegociável 4 / P9 | Negativo | Tentar emitir E5 com métricas exclusivamente de uso | E5 recusado. |
| TST-030 | Inegociável 5 / P10 | Negativo | Definir apenas uma área como responsável pela recalibragem | E5 recusado até existir pessoa nomeada. |
| TST-031 | Fronteira humana / P7 | Negativo | Agente tenta definir ou concluir autonomia | Recusa + `TentativaNegada`; nenhuma decisão de autonomia é gravada. |
| TST-032 | Recorrência / P10 | Negativo | Playbook declara etapa recorrente sem cadência | Playbook não carrega. |
| TST-033 | Critério de verificação | Negativo | Agente/HB declarado sem critério de verificação | Playbook não carrega. |
| TST-034 | Percurso completo | Positivo E2E | Executar caso controlado de F0 a P10 com todos os requisitos satisfeitos | Todas as etapas encerram na ordem; E1–E5 são autorizados; trilha completa sem bypass. |

### 3.6 Suíte de integração na superfície Claude Code

A suíte de scripts chama diretamente o núcleo e **não prova sozinha** que o Claude Code realmente aciona as guardas. Por isso, antes da aplicação da PoC, deve existir uma rodada de integração dentro de um caso real de teste.

| ID | Tentativa na superfície | Esperado |
|---|---|---|
| INT-01 | Escrever diretamente em `caso/teste.md` | Bloqueio com evento. |
| INT-02 | Ler skill humana de levantamento de regras | Bloqueio citando a camada humana. |
| INT-03 | Editar `registro/estado.json` diretamente | Bloqueio. |
| INT-04 | Em N3, carregar habilidade de P1 | Bloqueio. |
| INT-05 | Em N1, carregar a mesma habilidade de P1 | Permissão. |
| INT-06 | Consultar `registro/eventos.jsonl` após as negativas | Uma ocorrência auditável por bloqueio. |
| INT-07 | Percorrer F0–P10 pelo fluxo normal do Code Plugin | Percurso encerra sem escrita direta, sem bypass e com portões respeitados. |

### 3.7 Matriz requisito × teste

| Requisito | Origem | Teste principal |
|---|---|---|
| Habilidade humana não carrega para agente | CAT-01 / G1 | TST-001, INT-02 |
| Escrita direta é proibida | G2 | TST-002, TST-003, INT-01, INT-03 |
| Etapa humana dependente exige sessão | G3 / P3b | TST-006 |
| Nenhuma etapa pós-F0 sem nível | G4 | TST-012, TST-013 |
| Fronteira desloca com o nível | CAT-01 | TST-010, TST-011, TST-023, INT-04, INT-05 |
| Autor é pessoa nomeada | I-7 | TST-007, TST-016, TST-019, TST-021 |
| Procedência D/I/V é obrigatória | I-1 / método | TST-004, TST-005 |
| Fonte documental citada precisa existir | Integridade da evidência | TST-025, TST-026 |
| Playbook precisa de inegociáveis | I-9 | TST-009 |
| Termo de autonomia condiciona E4 | Inegociável 2 | TST-027 |
| Caso de teste exige saída esperada | Inegociável 3 | TST-028 |
| E5 exige métrica de resultado | Inegociável 4 | TST-029 |
| E5 exige pessoa responsável | Inegociável 5 | TST-030 |
| P7 é humano | CAT-01 / P7 | TST-031 |
| P10 recorrente exige cadência | P10 | TST-032 |
| Todo agente precisa de critério verificável | ESP-01 | TST-033 |
| Percurso integral opera sem bypass | ARQ/IMP/ESP | TST-034, INT-07 |

### 3.8 Evidência e registro do resultado

Cada execução deve registrar: ID do teste; versão do plugin; versão do playbook; commit do repositório; data; executor; pré-condição; comando ou ação; resultado esperado; resultado observado; código de retorno quando houver; evento emitido; arquivos alterados; status `aprovado`, `reprovado` ou `bloqueado`; e defeito associado quando aplicável.

O relatório de execução será consolidado posteriormente no **EMCIA-RTE-01 — Relatório de Testes da Implementação do Estúdio de Trabalho**. O TST-01 define o que deve ser provado; o RTE-01 registra o que aconteceu.

### 3.9 Critérios de regressão

- Falha de teste negativo indica regressão de trava; a correção recai sobre a implementação, não sobre a expectativa do teste.
- Controle positivo que deixa de passar indica bloqueio excessivo e também é regressão.
- Alteração em guarda, validador, playbook, estado, portão ou selamento exige execução da suíte completa.
- Nenhuma alteração crítica é considerada pronta apenas porque o Claude Code se comportou corretamente; ao menos uma tentativa deliberada de violação precisa atingir a trava.

## 4. Condição de aceite

O EMCIA-TST-01 está pronto quando existe rastreabilidade entre requisitos do método e testes; a linha de base atual está inventariada; os requisitos adicionais de F0–P10 possuem casos definidos; a integração na superfície Claude Code está separada da suíte direta de scripts; e os critérios de resultado e evidência permitem que um terceiro execute os testes sem decidir novamente o que significa aprovação.

Para considerar o **Code Plugin apto à aplicação da PoC**, todos os testes críticos negativos devem passar, os controles positivos devem permanecer funcionais, toda negativa deve produzir evento auditável, nenhuma tentativa proibida pode alterar o estado válido e o cenário TST-034/INT-07 deve completar F0–P10 sob os portões previstos. Esse aceite demonstra conformidade técnica do Estúdio de Trabalho, não validação operacional da solução empresarial do cliente.

## 5. Referências

- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-ARQ-01 — Arquitetura do Estúdio de Trabalho.
- EMCIA-IMP-01 — Plano de implementação do Estúdio de Trabalho.
- EMCIA-ESP-01 — Especificação executável do Estúdio de Trabalho.
- EMCIA-VER-01 — Plano de verificação do método.
- Guia do Engenheiro de Campo — Estúdio, setembro de 2026.
- Plano — do percurso parcial ao percurso completo, setembro de 2026.
- Repositório `CvGonjr/emcia-marketplace`, arquivo `testes/negativos.sh`, consulta em 17/09/2026.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 17/09/2026 | Celso do Vale | Versão inicial: inventário da suíte existente, extensão F0–P10, testes de integração na superfície e critérios de aceite. | — |
