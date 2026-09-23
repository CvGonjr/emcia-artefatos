# Plano de implementação do Estúdio

*Conversão da arquitetura planejada em componentes executáveis da Sprint 2*

|                 |                         |               |            |
|-----------------|-------------------------|---------------|------------|
| **Código**      | EMCIA-IMP-01            | **Versão**    | 0.1        |
| **Data**        | 17/09/2026              | **Estado**    | Em revisão |
| **Responsável** | Celso do Vale           | **Aprovação** | pendente   |
| **Fase**        | Sprint 1 — Planejamento | **Passo**     | Ação 1.9   |

## 1. Objetivo

Converter a arquitetura definida no EMCIA-ARQ-01 em um plano de implementação para a Sprint 2, estabelecendo sequência, dependências, responsabilidades técnicas, critérios de pronto e evidências esperadas para as camadas de Agente, Protocolos, Contexto e Dados.

## 2. Escopo e aplicação

Aplica-se à implementação interna do Estúdio da EMCIA, prioritariamente como plugins do Claude Code operados pelo engenheiro de campo. Organiza as ações 2.5 e 2.6 e suas dependências sobre 2.1 a 2.4, preparando o ambiente para a execução declarada das ações 2.7 a 2.9.

Não inclui construção da camada corporativa de Controle, interface SaaS, integrações com sistemas empresariais, implantação da solução do cliente nem operação contínua. A integração de modelo de linguagem e harness utiliza componentes de mercado.

## 3. Conteúdo

### 3.1 Entradas obrigatórias da Sprint 1

| **Entrada**       | **Uso na implementação**                                                   |
|-------------------|----------------------------------------------------------------------------|
| **EMCIA-MET-01**  | Define fases, passos, cortes, encerramentos e inegociáveis.                |
| **EMCIA-CAT-01**  | Define camadas de execução e habilidades delegáveis.                       |
| **EMCIA-TRI-01**  | Fornece regra determinística de apuração do nível.                         |
| **EMCIA-E1 a E5** | Define portões e artefatos que o percurso precisa produzir.                |
| **EMCIA-VER-01**  | Define selamento e desenho de verificação.                                 |
| **EMCIA-GLO-01**  | Fixa vocabulário e códigos usados pelo playbook e pelos comandos.          |
| **EMCIA-ARQ-01**  | Define a arquitetura, o recorte das quatro camadas e a superfície inicial. |
| **EMCIA-ESP-01**  | Define contratos executáveis, invariantes, estado e regras de transição.   |

### 3.2 Estratégia de implementação

A implementação segue uma ordem que reduz decisões tardias: primeiro os instrumentos são formalizados; depois são convertidos em contratos e habilidades; em seguida as quatro camadas são montadas e integradas; por último o braço declarado utiliza o ambiente já fechado. Nenhuma skill de método deve ser criada antes de existir um instrumento com entrada, saída e critério de encerramento.

1. Concluir ou revisar os instrumentos das ações 2.1 a 2.4.
2. Congelar os contratos do EMCIA-ESP-01 que afetam playbook, procedência, estado e escrita.
3. Montar a estrutura dos plugins eiac-nucleo e eiac-campo e o template de caso.
4. Implementar a camada do Agente e a camada de Protocolos, incluindo base curada e acessos.
5. Implementar a camada de Contexto e a camada de Dados, incluindo schemas, procedência e versionamento.
6. Executar testes de integração e negativos antes de usar o Estúdio no braço declarado.
7. Executar 2.7, 2.8 e 2.9 e selar a execução declarada.

### 3.3 Pacotes de trabalho

| **Pacote**                  | **Ação** | **Conteúdo**                                                                          | **Saída verificável**                                                      |
|-----------------------------|----------|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **PT-01 — Base executável** | 2.5      | Estrutura dos plugins, carregador de playbook, comandos de núcleo e template de caso. | Caso abre, lê o playbook e reporta estado sem depender de prompt.          |
| **PT-02 — Camada Agente**   | 2.5      | Modelo integrado, harness, skills permitidas, subagentes e base de referência curada. | Agente executa apenas capacidades autorizadas e produz saída estruturada.  |
| **PT-03 — Protocolos**      | 2.5      | Sistema de arquivos e MCPs necessários ao caso, com contratos de leitura/escrita.     | Acesso ocorre somente pelos canais declarados e com fonte identificada.    |
| **PT-04 — Contexto**        | 2.6      | Termos, entidades, regras e fontes com autoria, procedência e campos do P5.           | Regra válida pode ser recuperada, versionada e confrontada com sua origem. |
| **PT-05 — Dados**           | 2.6      | Documentos e amostras do caso, catálogo de fontes e versionamento.                    | Toda evidência usada pelo Estúdio aponta para fonte e versão.              |
| **PT-06 — Integração**      | 2.5/2.6  | Fluxo rascunho → validação → caso; portões e eventos.                                 | Tentativa proibida falha e deixa rastro; tentativa válida avança.          |

### 3.4 Ação 2.5 — Camada do Agente e Protocolos

A ação 2.5 constrói as duas camadas que tornam as atividades delegáveis operáveis no Estúdio. “Construir a camada” não significa desenvolver um modelo ou harness proprietário: esses componentes são integrados. O trabalho próprio está no contexto operacional, nas skills, nos contratos de ferramentas, na base curada, nos adaptadores e nos limites de acesso.

| **Componente**           | **Tratamento**                                                    | **Critério de pronto**                                                  |
|--------------------------|-------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Modelo de linguagem**  | Integrar componente de mercado.                                   | Pode ser substituído sem alterar playbook, schemas ou regras do núcleo. |
| **Harness/orquestração** | Integrar componente de mercado.                                   | Executa skills e ferramentas sem conter regra de domínio.               |
| **Skills**               | Construir a partir dos instrumentos.                              | Cada skill declara camada de execução, insumo, saída e verificação.     |
| **Subagentes**           | Configurar somente onde agrupamento de skills acrescenta clareza. | Nenhum agente reúne habilidades de EX3 ou EX4.                          |
| **Base curada**          | Construir acervo controlado.                                      | Cada item possui fonte, data e limite de uso.                           |
| **Sistema de arquivos**  | Configurar como protocolo básico.                                 | Leitura e escrita obedecem ao contrato do caso.                         |
| **MCP**                  | Integrar servidores estritamente necessários.                     | Sem acesso aberto a sistemas fora do recorte da PoC.                    |

### 3.5 Ação 2.6 — Camada de Contexto e Dados

A ação 2.6 materializa os ativos que o trabalho de campo produz e que os agentes internos consomem. O objetivo não é criar uma ontologia autônoma, mas manter conhecimento empresarial verificável e rastreável. A camada de contexto recebe conteúdo somente pelos caminhos previstos no método; a camada de dados preserva as fontes usadas para sustentar cada afirmação.

| **Objeto**            | **Campos mínimos**                                                                                         | **Critério de pronto**                                            |
|-----------------------|------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
| **Termo**             | nome, definição, origem, versão                                                                            | Não possui sinônimo conflitante não resolvido.                    |
| **Entidade**          | identificador, atributos relevantes, relações                                                              | É referenciável pelas regras sem ambiguidade.                     |
| **Regra**             | enunciado, autor, fonte, determinismo, frequência, consequência, decisor, entradas, exceções, estabilidade | Pode sustentar o P5 e possui procedência suficiente para revisão. |
| **Fonte**             | tipo, localização, data/versão, responsável                                                                | É possível reencontrar a evidência que sustentou a asserção.      |
| **Documento do caso** | arquivo, hash/versão ou referência estável, data de entrada                                                | Mudança posterior não sobrescreve silenciosamente a versão usada. |

### 3.6 Estrutura de repositório prevista

| **Local**                      | **Conteúdo previsto**                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------|
| **emcia-marketplace/**         | Plugins, decisões, testes, comandos, scripts e template de caso; sem dado de cliente. |
| **eiac-nucleo/**               | Guardas, validação, estado, transições, emissão e comandos transversais.              |
| **eiac-campo/**                | Skills, comandos, subagentes, referências e instrumentos do método.                   |
| **~/casos/\<caso\>/registro/** | playbook.json, estado e eventos do engajamento.                                       |
| **~/casos/\<caso\>/metodo/**   | versões controladas dos artefatos EMCIA aplicáveis.                                   |
| **~/casos/\<caso\>/contexto/** | termos, entidades, regras e fontes.                                                   |
| **~/casos/\<caso\>/rascunho/** | saídas ainda não aceitas.                                                             |
| **~/casos/\<caso\>/caso/**     | asserções e artefatos aceitos.                                                        |

### 3.7 Dependências e sequência crítica

| **Dependência**                | **Bloqueia**                        | **Regra de planejamento**                                                               |
|--------------------------------|-------------------------------------|-----------------------------------------------------------------------------------------|
| **Procedência definida**       | schemas, gravação e contexto        | Não codificar schema final enquanto a taxonomia vigente estiver em conflito documental. |
| **Instrumento escrito**        | skill correspondente                | Skill é conversão de procedimento; não se inventa procedimento no código.               |
| **Playbook válido**            | abertura do caso                    | Caso não opera sem etapas, camadas, modalidade, portões e inegociáveis.                 |
| **Nível apurado**              | etapas posteriores à F0             | Sem nível, aplica-se postura restritiva e não se avança.                                |
| **Sessão de campo registrada** | confrontos que dependem de presença | Não produzir evidência de campo sem sessão registrada.                                  |
| **Testes negativos mínimos**   | uso no braço declarado              | O Estúdio não entra em 2.7–2.9 antes de provar que recusa o proibido.                   |

### 3.8 Evidências previstas para o relatório

A implementação deve produzir evidência representativa, não uma reprodução integral do repositório. As evidências previstas são:

- estrutura dos dois plugins e do template de caso;
- trecho do playbook mostrando camada por nível, modalidade e portão;
- execução de um comando válido no Claude Code;
- tentativa bloqueada por camada ou escrita indevida, acompanhada do evento correspondente;
- exemplo de asserção com procedência validada;
- estrutura da camada de contexto com uma regra completa; e
- registro do selamento da execução declarada antes do campo.

### 3.9 Riscos de implementação

| **Risco**                                   | **Sinal**                                                        | **Tratamento**                                                 |
|---------------------------------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| **Método migrar para prompts**              | regra crítica aparece apenas em CLAUDE.md ou instrução de agente | Mover para schema, validador, playbook ou permissão.           |
| **Código definir procedimento inexistente** | skill não possui documento de origem                             | Bloquear a conversão e retornar à ação 2.1–2.4.                |
| **Superfície virar dependência**            | regra só funciona no Claude Code                                 | Manter contratos de domínio e playbook independentes da UI.    |
| **Acesso excessivo**                        | agente consulta fonte fora do recorte                            | Menor privilégio; protocolos explícitos e base curada.         |
| **Mistura de casos**                        | arquivo de cliente aparece no marketplace ou em outro caso       | Separação física e versionamento por repositório.              |
| **Teste comprovar obediência, não trava**   | modelo recusa sem evento técnico                                 | Exigir prova no log e teste que force o mecanismo de bloqueio. |

## 4. Condição de aceite

Este artefato está pronto quando:

- as ações 2.5 e 2.6 estão decompostas em componentes e critérios verificáveis;
- a sequência respeita a dependência instrumentos → contratos → camadas → execução declarada;
- cada componente está classificado como construir, integrar ou fora do escopo;
- as evidências previstas para o relatório foram definidas antes da implementação;
- os riscos de implementação possuem tratamento explícito; e
- um engenheiro consegue iniciar a Sprint 2 lendo este plano em conjunto com ARQ-01 e ESP-01.

## 5. Referências

- EMCIA-ARQ-01 — Arquitetura do Estúdio interno.
- EMCIA-ESP-01 — Especificação executável do Estúdio.
- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-TRI-01 — Instrumento de triagem da Fase 0.
- EMCIA-VER-01 — Plano de verificação.
- Camadas da Solução (documento interno, setembro de 2026).
- Estúdio como Plugin — Conceito e Arquitetura (documento interno, setembro de 2026).
- Guia do Engenheiro de Campo — Estúdio (documento interno, setembro de 2026).

## 6. Histórico de revisões

| **Versão** | **Data**   | **Autor**     | **Descrição da alteração**                                                                                 | **Aprovação** |
|------------|------------|---------------|------------------------------------------------------------------------------------------------------------|---------------|
| **0.1**    | 17/09/2026 | Celso do Vale | Versão inicial: decomposição da Sprint 2, critérios de pronto, dependências e evidências de implementação. | —             |
