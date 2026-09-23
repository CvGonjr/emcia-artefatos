# Arquitetura do Estúdio de Trabalho

*Arquitetura executável do método completo F0–P10 e recorte da prova de conceito*

| | | | |
|---|---|---|---|
| **Código** | EMCIA-ARQ-01 | **Versão** | 0.2 |
| **Data** | 17/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 1 — Planejamento | **Passo** | Ação 1.9 |

## 1. Objetivo

Fixar a arquitetura do Estúdio de Trabalho utilizado pelo engenheiro de campo e o alvo funcional do Code Plugin: instrumentar o método completo, da Fase 0 ao Passo 10, mantendo separadas a infraestrutura substituível, as regras determinísticas do método e o julgamento humano. O documento define a organização em plugins, o playbook por caso, a estrutura dos registros, o recorte das camadas construídas na PoC e as condições arquiteturais que a implementação da Sprint 2 precisa satisfazer.

## 2. Escopo e aplicação

Aplica-se ao ambiente interno de apoio à Engenharia de IA de Campo. O usuário primário é o engenheiro de campo; a organização participante é usuária do serviço, não do Code Plugin.

O alvo da implementação é o percurso integral: **F0 e P1 a P10**, representados em treze etapas operacionais quando o Passo 3 é desdobrado em preparação, levantamento presencial e confronto. A implementação deve fechar as cinco fases, tornar operantes os cinco itens inegociáveis, mapear as dezoito habilidades HB e os quatro agentes AG e permitir a emissão dos cinco entregáveis ao cliente. Internamente, o E3 possui dois portões — decisão e especificação — e por isso o motor trata seis autorizações emitíveis.

O escopo não inclui software de produção para o cliente, integração com ERP, CRM, correio eletrônico ou portais, nem operação real da solução especificada. P6 a P10 são instrumentados pelo Code Plugin e podem produzir seus artefatos e portões em simulação; a PoC não reivindica validação operacional das fases F3 e F4 em ambiente produtivo.

## 3. Conteúdo

### 3.1 Princípios de desenho

A arquitetura segue cinco princípios: o método precede a ferramenta; a fronteira entre delegável e humano é contrato, não prompt; procedência permanece documentalmente nas marcas **D — declarada, I — inferida e V — verificada**; a infraestrutura genérica é substituível; e cada caso congela o playbook com que foi aberto.

> **Regra de arquitetura:** constrói-se o que carrega o método; integra-se o que carrega a função. Guardas, portões, procedência D/I/V, estado e critérios de passagem precisam ser reproduzíveis fora do modelo de linguagem.

### 3.2 Usuário e superfície prioritária

| Decisão | Definição |
|---|---|
| Usuário primário | Engenheiro de campo que conduz o método. |
| Superfície inicial | Claude Code. |
| Forma de distribuição | Code Plugin composto por `eiac-nucleo` e `eiac-campo`. |
| Unidade de trabalho | Um caso por organização/processo, em repositório próprio. |
| Cobertura | F0 a P10, cinco fases. |
| Portabilidade | Método, playbook e registros independem da interface e do modelo. |

### 3.3 Separação entre núcleo e campo

| Componente | Responsabilidade | Conhece o método |
|---|---|---|
| `eiac-nucleo` | Guardas, validação D/I/V, estado, portões, selamento, eventos e autorização de escrita/emissão. | Não. Lê o playbook do caso. |
| `eiac-campo` | Habilidades, comandos, subagentes, referências, instrumentos e templates que representam F0–P10. | Sim. É a representação operacional do método. |

A separação impede que regras da EMCIA fiquem presas ao motor. O núcleo conhece abstrações como caso, etapa, nível, camada, portão, asserção e entregável; o componente de campo conhece fases, passos, instrumentos, agentes e habilidades.

### 3.4 Cobertura funcional do percurso

| Fase | Etapas no Code Plugin | Fechamento | Observação |
|---|---|---|---|
| F0 — Enquadramento | F0 | E1 | Triagem, nível e enquadramento. |
| F1 — Alinhamento e diagnóstico | P1, P2, P3a, P3b, P3d | E2 | P3b permanece presencial e sem comando de agente. |
| F2 — Desenho e arquitetura | P4, P5 | E3-D e E3-E | E3-E só abre quando P5 conclui que há caso agêntico. |
| F3 — Operacionalização e governança | P6, P7 | E4 | P7 fecha a autonomia por decisão humana; o agente pode apenas preparar a minuta. |
| F4 — Piloto, mensuração e calibragem | P8, P9, P10 | E5 | Na PoC, os artefatos são produzidos sem alegar operação real da solução do cliente. |

### 3.5 Playbook e isolamento do caso

Cada engajamento recebe uma cópia versionada do playbook. Ela declara as etapas F0–P10, camada por nível, modalidade, habilidades autorizadas, itens inegociáveis, portões, cadência de etapa recorrente e critérios de verificação dos agentes. Atualizações do plugin não alteram silenciosamente um caso em andamento.

| Área | Conteúdo | Regra |
|---|---|---|
| `registro/` | playbook, estado, eventos e selos | Escrita apenas por caminhos autorizados do núcleo. |
| `metodo/` | documentos controlados do método | Leitura e versão congelada no caso. |
| `contexto/` | termos, entidades, regras e fontes | Conteúdo curado e marcado D/I/V. |
| `rascunho/` | propostas de pessoa ou agente | Não é evidência aceita. |
| `caso/` | asserções e artefatos aceitos | Sem escrita direta pelo agente. |

### 3.6 Arquitetura de referência em cinco camadas

| Camada | Função | Tratamento na PoC | Ação |
|---|---|---|---|
| Controle | Governança transversal de plataforma. | Referência arquitetural; a plataforma corporativa de controle não é construída. | Fora de 2.5/2.6 |
| Agente | Modelo, orquestração, skills, ferramentas e base curada. | Construída e completada para F0–P10. | 2.5 |
| Protocolos | Acesso controlado a arquivos, documentos e capacidades. | Construída com sistema de arquivos e MCP quando necessário. | 2.5 |
| Contexto | Termos, entidades, regras e fontes do caso. | Construída; regras críticas só entram após validação humana. | 2.6 |
| Dados | Documentos, amostras e fontes do caso. | Construída como repositório versionado com D/I/V. | 2.6 |

Os controles determinísticos específicos do método ficam no `eiac-nucleo`; isso não equivale à construção de uma plataforma corporativa completa de identidade, cofre, gateway e sandbox.

### 3.7 Fronteira entre construir e integrar

| Objeto | Decisão | Justificativa |
|---|---|---|
| Modelo de linguagem | Integrar | Motor substituível. |
| Claude Code / harness | Integrar | Superfície e infraestrutura de execução. |
| Skills HB e agentes AG | Construir | Materializam o catálogo e o percurso F0–P10. |
| Playbook, estado, portões e validadores | Construir | Regras que precisam ser determinísticas. |
| MCP / sistema de arquivos | Configurar e integrar | Capacidade de acesso, não conhecimento do método. |
| Base de referência curada | Construir conteúdo e governança | Consulta controlada com fonte identificada. |
| Interface própria | Adiar | Não é necessária para provar a tese da PoC. |

### 3.8 Cinco itens inegociáveis

| # | Exigência | Passo | Efeito no Code Plugin |
|---|---|---|---|
| 1 | Linha de base registrada antes do piloto | P3 | E2 não fecha sem registro válido. |
| 2 | Termo de autonomia escrito | P7 | E4 não emite sem as três listas. |
| 3 | Casos de teste com saída esperada | P8 | E5 não avança sem conjunto revisado. |
| 4 | Ao menos uma métrica de resultado | P9 | Métrica apenas de uso não satisfaz o portão. |
| 5 | Responsável nomeado pela recalibragem | P10 | Área sem pessoa nomeada não satisfaz o portão. |

### 3.9 Limite da PoC

A cobertura integral do Code Plugin não altera o limite acadêmico. O plugin deve conseguir percorrer F0–P10, produzir os artefatos correspondentes e bloquear omissões estruturais. Isso não significa construir a solução empresarial do cliente nem afirmar que P6–P10 foram validados em produção. Nas fases finais, a evidência é a capacidade do método de produzir especificação, guia, casos de teste, plano de medição e rotina de calibragem sob portões coerentes.

## 4. Condição de aceite

Este artefato está pronto quando a arquitetura explicita a cobertura F0–P10, os dois plugins e sua separação, as cinco camadas de referência e o recorte das quatro camadas construídas, a estrutura isolada do caso, os cinco inegociáveis, a procedência D/I/V, os cinco entregáveis com seis autorizações internas e a distinção entre implementação do Code Plugin e validação operacional da solução do cliente.

## 5. Referências

- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-TRI-01 — Instrumento de triagem.
- EMCIA-VER-01 — Plano de verificação.
- EMCIA-GLO-01 — Glossário do método.
- EMCIA-IMP-01 — Plano de implementação do Estúdio de Trabalho.
- EMCIA-ESP-01 — Especificação executável do Estúdio de Trabalho.
- EMCIA-LMC-01 — Lean Model Canvas do Estúdio de Trabalho.
- EMCIA-ONI-01 — Onion Planning da implementação do Code Plugin.
- Plano — do percurso parcial ao percurso completo (documento interno, setembro de 2026).

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 17/09/2026 | Celso do Vale | Versão inicial da arquitetura do Estúdio. | — |
| 0.2 | 17/09/2026 | Celso do Vale | Cobertura ampliada para F0–P10; cinco inegociáveis; D/I/V preservado; alinhamento das fases F3 e F4 ao relatório. | — |
