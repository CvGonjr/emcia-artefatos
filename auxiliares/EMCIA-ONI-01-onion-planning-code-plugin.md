# Onion Planning da Implementação do Code Plugin

*Planejamento enxuto até o nível de sprint — ciclo de uma semana*

| | | | |
|---|---|---|---|
| **Código** | EMCIA-ONI-01 | **Versão** | 0.1 |
| **Data** | 17/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 1 — Planejamento | **Passo** | Ação 1.9 |

## 1. Objetivo

Traduzir o planejamento do Estúdio de Trabalho em horizontes concêntricos, da visão do PFC até uma sprint de implementação de uma semana. O documento para no nível de sprint: tarefas diárias permanecem no quadro operacional e não fazem parte deste artefato.

## 2. Escopo

O onion planning cobre a implementação do Code Plugin do percurso completo F0–P10. Não planeja a implantação da solução empresarial do cliente.

## 3. Camadas do planejamento

| Camada | Horizonte | Decisão |
|---|---|---|
| Visão | PFC | Demonstrar que o método EMCIA pode ser aplicado com automação onde há inteligência delegável e bloqueio onde é exigido julgamento humano. |
| Produto / PoC | Projeto | Estúdio de Trabalho em Code Plugin, usado pelo engenheiro de campo, independente do modelo e da interface. |
| Release do percurso completo | Sprint 2 | F0–P10 carregáveis; cinco fases fecháveis; cinco inegociáveis operantes; 18 HB e 4 AG codificados; E1–E5 geráveis sob portão. |
| Sprint | **1 semana** | Fechar base técnica e instrumentos ausentes, implementar P6–P10 e concluir testes negativos do percurso completo. |

## 4. Objetivo da sprint de uma semana

**Ao final da semana, o Code Plugin deve percorrer F0–P10 sem lacunas estruturais, aplicar D/I/V, bloquear as atividades humanas definidas pelo método, condicionar E2/E4/E5 aos cinco itens inegociáveis e produzir os cinco entregáveis da PoC, sem alegar validação operacional da solução do cliente.**

## 5. Backlog da sprint

| Pacote | Conteúdo | Dependência | Saída de aceite |
|---|---|---|---|
| P1 — Base | Proteção de escrita, códigos HB/AG, verificação executável, gerador de documento | Nenhuma | Guardas e geração funcionando sem bypass. |
| P2 — F1 | Roteiro de levantamento, P3b instrumentado, CTX-01, AG-01/AG-02 | Instrumentos escritos | E2 emitível com inegociável 1. |
| P3 — F2 | AG-03 e blueprint em duas partes | P2 | E3-D/E3-E sob portões corretos. |
| P4 — F3 | Protocolo de campo, P6, P7, termo de autonomia | Protocolo escrito | E4 emitível com inegociável 2. |
| P5 — F4 | P8, P9, P10, AG-04, cadência, métricas e testes | P4 | E5 emitível com inegociáveis 3–5. |

## 6. Definition of Done da sprint

- 13 etapas F0–P10 presentes no playbook;
- 18 habilidades HB e 4 agentes AG com código oficial;
- P3b e P7 não concluíveis por agente;
- P10 exige cadência, responsável nominal e registro da última verificação;
- D/I/V é a única taxonomia documental de procedência;
- E4 fecha P6–P7 e E5 fecha P8–P10;
- cinco inegociáveis operantes;
- testes 14–20 adicionados à suíte, sem regressão dos anteriores;
- geração dos documentos ocorre apenas depois da autorização do portão;
- limitações de F3/F4 em simulação estão declaradas.

## 7. Fora da sprint

Interface própria, integrações empresariais, camada corporativa de controle, operação contínua, implantação da solução do cliente e comprovação de resultado operacional.

## 8. Condição de aceite

O onion planning está pronto quando as quatro camadas de horizonte são coerentes entre si e a sprint de uma semana possui objetivo, cinco pacotes, dependências e Definition of Done suficientes para orientar o quadro operacional sem decompor o trabalho em agenda diária.

## 9. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 17/09/2026 | Celso do Vale | Versão inicial do Onion Planning até o nível de sprint. | — |
