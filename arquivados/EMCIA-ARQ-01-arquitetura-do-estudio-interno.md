# Arquitetura do Estúdio interno

*Arquitetura executável do método e recorte da prova de conceito*

|                 |                         |               |            |
|-----------------|-------------------------|---------------|------------|
| **Código**      | EMCIA-ARQ-01            | **Versão**    | 0.1        |
| **Data**        | 17/09/2026              | **Estado**    | Em revisão |
| **Responsável** | Celso do Vale           | **Aprovação** | pendente   |
| **Fase**        | Sprint 1 — Planejamento | **Passo**     | Ação 1.9   |

## 1. Objetivo

Fixar a arquitetura do Estúdio interno utilizado pelo engenheiro de campo, definindo a separação entre método e infraestrutura, a organização em plugins, a estrutura de cada caso e o recorte das camadas que serão materializadas na Sprint 2. O documento sustenta a decisão de como o método será tornado executável sem transferir ao modelo de linguagem as restrições que precisam ser determinísticas.

## 2. Escopo e aplicação

Aplica-se ao ambiente interno de apoio à Engenharia de IA de Campo e orienta a implementação das ações 2.5 e 2.6. O usuário do Estúdio é o engenheiro de campo; a organização participante é usuária do serviço, não desta ferramenta.

Não descreve a solução do cliente, não substitui o EMCIA-MET-01 e não transforma o trabalho de campo em camada de software. Também não inclui a construção de uma plataforma completa de controle corporativo, implantação da solução especificada para o cliente, integrações com ERP, CRM, correio eletrônico ou portais operacionais.

## 3. Conteúdo

### 3.1 Princípios de desenho

A arquitetura parte de quatro princípios. O método precede a ferramenta; as restrições críticas são verificadas por código ou estrutura de dados; a infraestrutura genérica permanece substituível; e cada caso preserva as regras sob as quais foi aberto. O Estúdio deve instrumentar o método, não redefini-lo durante a execução.

| **Regra de arquitetura.** Constrói-se o que carrega a tese; integra-se o que carrega a função. Procedência, fronteira de execução, portões e estado do percurso não podem depender de interpretação livre do modelo. |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

### 3.2 Usuário e superfície prioritária

A primeira superfície operacional será o Claude Code, utilizado diretamente pelo engenheiro de campo. A escolha prioriza a validação do método e de suas travas antes da criação de uma interface própria. A superfície é substituível: uma futura interface visual deverá consumir os mesmos contratos, playbooks e registros, sem alterar as regras do domínio.

| **Decisão**               | **Definição**                                                             |
|---------------------------|---------------------------------------------------------------------------|
| **Usuário primário**      | Engenheiro de campo que conduz o método.                                  |
| **Superfície inicial**    | Claude Code.                                                              |
| **Forma de distribuição** | Marketplace com dois plugins: eiac-nucleo e eiac-campo.                   |
| **Unidade de trabalho**   | Um caso por organização/processo, em repositório próprio.                 |
| **Portabilidade**         | A lógica do método deve permanecer independente da interface e do modelo. |

### 3.3 Separação entre núcleo e campo

| **Componente**  | **Responsabilidade**                                                                                                  | **Conhece o método**                          |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| **eiac-nucleo** | Aplicar guardas, validar procedência, controlar estado/etapas, autorizar gravação e emissão e registrar eventos.      | Não. Lê o playbook do caso.                   |
| **eiac-campo**  | Disponibilizar habilidades, comandos, subagentes, referências e templates que materializam os instrumentos do método. | Sim. É a representação operacional do método. |

A separação impede que regras da EMCIA sejam codificadas de forma irreversível no motor. O núcleo conhece caso, etapa, nível, portão, asserção e procedência; o componente de campo conhece F0, P1 a P10, instrumentos e entregáveis. Trocar o método deve significar trocar o playbook e os componentes de campo, não reescrever o mecanismo de controle.

### 3.4 Playbook e isolamento do caso

Cada engajamento recebe uma cópia versionada do playbook no momento de abertura. Essa cópia registra as etapas válidas, a camada de execução por nível, a modalidade, os itens inegociáveis e os portões de entregáveis. Atualizações posteriores dos plugins não alteram automaticamente um caso em andamento.

| **Área do caso** | **Conteúdo**                              | **Regra**                                                   |
|------------------|-------------------------------------------|-------------------------------------------------------------|
| **registro/**    | playbook, estado e trilha de eventos      | Escrita somente pelos caminhos autorizados do núcleo.       |
| **metodo/**      | documentos controlados aplicáveis ao caso | Leitura; versão congelada conforme o engajamento.           |
| **contexto/**    | termos, entidades, regras e fontes        | Conteúdo curado, versionado e com procedência.              |
| **rascunho/**    | material proposto por pessoa ou agente    | Não é evidência aceita enquanto não for validado e gravado. |
| **caso/**        | asserções e artefatos aceitos             | Não admite escrita direta pelo agente.                      |

### 3.5 Arquitetura de referência em cinco camadas

O Estúdio é descrito por cinco camadas de referência. A camada de controle permanece no modelo para explicitar onde residiria a governança de plataforma, mas o recorte da prova de conceito constrói somente as quatro camadas diretamente ligadas à operação interna do engenheiro de campo. O eiac-nucleo aplica controles do método, porém isso não equivale à construção de uma camada corporativa de controle com identidade, cofre, gateway e sandbox.

| **Camada**     | **Função no Estúdio**                                                           | **Tratamento na PoC**                                                   | **Ação**                  |
|----------------|---------------------------------------------------------------------------------|-------------------------------------------------------------------------|---------------------------|
| **Controle**   | Governança transversal da plataforma e supervisão de execução.                  | Referência arquitetural; não construída como camada da PoC.             | Fora do escopo de 2.5/2.6 |
| **Agente**     | Modelo, orquestração e contexto operacional: skills, ferramentas e base curada. | Camada construída, integrando modelo/harness de mercado.                | 2.5                       |
| **Protocolos** | Como os agentes alcançam arquivos, documentos e capacidades.                    | Camada construída com sistema de arquivos e MCP restrito ao necessário. | 2.5                       |
| **Contexto**   | Termos, entidades, regras, fontes e memória estruturada do caso.                | Camada construída; nenhuma regra crítica entra sem validação humana.    | 2.6                       |
| **Dados**      | Documentos, amostras e demais fontes utilizadas no caso.                        | Camada construída como repositório versionado com procedência.          | 2.6                       |

### 3.6 Fronteira entre construir e integrar

| **Objeto**                     | **Decisão**                                             | **Justificativa**                                                                           |
|--------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Modelo de linguagem**        | Integrar                                                | É motor substituível; não carrega a tese do projeto.                                        |
| **Harness/orquestração**       | Integrar                                                | Memória, loop e execução são infraestrutura de mercado.                                     |
| **Skills do método**           | Construir                                               | Convertem instrumentos e critérios de saída em procedimentos versionados.                   |
| **Playbook e validadores**     | Construir                                               | Representam regras e portões que precisam ser determinísticos.                              |
| **MCP / sistema de arquivos**  | Construir configuração e contratos; integrar tecnologia | Acesso é capacidade, não conhecimento do método.                                            |
| **Base de referência curada**  | Construir conteúdo e governança                         | A consulta deve ter fonte identificada e escopo controlado.                                 |
| **Repositório de contexto**    | Construir                                               | É onde o conhecimento verificado passa a existir como ativo versionado.                     |
| **Integrações ERP/CRM/e-mail** | Não construir nesta PoC                                 | Não testam a fronteira HITL e adicionam credencial, LGPD e esforço sem evidência adicional. |

### 3.7 Origem externa do conteúdo das camadas

O trabalho de Engenharia de IA de Campo permanece externo à arquitetura. Seus produtos, porém, alimentam o Estúdio: P2 fornece documentos e fontes; P3 produz medição, divergências e regras verificadas; P4 e P5 definem priorização, contenção e classificação tecnológica; P6 em diante acrescentam capacidades operacionais, testes e calibragem. A arquitetura organiza o estado desses ativos; o método define o percurso que os produz.

| **Limite.** O Estúdio é incompleto por desenho. Regras de baixa frequência e alta consequência podem não existir em documento nem em histórico; por isso a camada de contexto não é preenchida automaticamente e depende do levantamento humano. |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

### 3.8 Restrições determinísticas

A arquitetura reserva ao núcleo as verificações que não podem ser delegadas ao modelo. No mínimo, devem ser determinísticas: apuração do nível quando baseada em pontuação, validação de procedência, autorização de escrita no caso, aplicação da camada de execução, registro de sessão exigida, avanço de etapa e emissão de entregável. Uma recusa deve sempre produzir registro auditável.

### 3.9 Encadeamento com a Sprint 2

| **Origem**                              | **Transformação na Sprint 2**                                                       | **Destino**                           |
|-----------------------------------------|-------------------------------------------------------------------------------------|---------------------------------------|
| **2.1–2.4: instrumentos do engenheiro** | Converter procedimentos em skills, comandos, schemas e critérios executáveis.       | eiac-campo e contratos do caso        |
| **2.5: agente + protocolos**            | Configurar agentes internos, contexto operacional, MCP e base de referência curada. | Camadas Agente e Protocolos           |
| **2.6: contexto + dados**               | Estruturar repositórios, procedência, versionamento e regras verificadas.           | Camadas Contexto e Dados              |
| **2.7–2.9: braço declarado**            | Usar o Estúdio para produzir, executar e selar a representação declarada.           | Primeiro uso integrado da arquitetura |

## 4. Condição de aceite

Este artefato está pronto quando:

- o usuário, a superfície inicial e a separação eiac-nucleo × eiac-campo estão definidos;
- a estrutura do caso e o papel do playbook estão descritos sem depender de tecnologia de interface;
- as cinco camadas de referência estão delimitadas e o recorte da PoC identifica explicitamente que somente Agente, Protocolos, Contexto e Dados serão construídas nas ações 2.5 e 2.6;
- a camada de Controle está distinguida dos controles internos do núcleo e permanece fora do escopo de construção;
- as decisões construir × integrar × fora de escopo estão registradas; e
- a Sprint 2 consegue iniciar 2.5 e 2.6 sem nova decisão arquitetural de princípio.

## 5. Referências

- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-GLO-01 — Glossário do método.
- EMCIA-VER-01 — Plano de verificação.
- Concepção da Solução — Registro de Decisão (documento interno, setembro de 2026).
- Camadas da Solução (documento interno, setembro de 2026).
- Estúdio como Plugin — Conceito e Arquitetura (documento interno, setembro de 2026).
- Guia do Engenheiro de Campo — Estúdio (documento interno, setembro de 2026).

## 6. Histórico de revisões

| **Versão** | **Data**   | **Autor**     | **Descrição da alteração**                                                                                            | **Aprovação** |
|------------|------------|---------------|-----------------------------------------------------------------------------------------------------------------------|---------------|
| **0.1**    | 17/09/2026 | Celso do Vale | Versão inicial: arquitetura do Estúdio, superfície prioritária, recorte das camadas e ligação com as ações 2.5 e 2.6. | —             |
