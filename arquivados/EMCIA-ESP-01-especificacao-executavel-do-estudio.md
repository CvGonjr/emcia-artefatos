# Especificação executável do Estúdio

*Playbook, estado, procedência, portões e invariantes para implementação*

|                 |                         |               |            |
|-----------------|-------------------------|---------------|------------|
| **Código**      | EMCIA-ESP-01            | **Versão**    | 0.1        |
| **Data**        | 17/09/2026              | **Estado**    | Em revisão |
| **Responsável** | Celso do Vale           | **Aprovação** | pendente   |
| **Fase**        | Sprint 1 — Planejamento | **Passo**     | Ação 1.9   |

## 1. Objetivo

Definir os contratos executáveis que a implementação do Estúdio deve respeitar, traduzindo decisões do método em estruturas verificáveis de playbook, estado, procedência, camadas de execução, transições, escrita, portões de entregáveis e eventos. O documento especifica o comportamento esperado; não prescreve uma linguagem de programação nem uma biblioteca de orquestração.

## 2. Escopo e aplicação

Aplica-se ao eiac-nucleo, ao eiac-campo e ao repositório de cada caso. Serve de contrato entre os artefatos metodológicos da Sprint 1 e o código da Sprint 2. As regras aqui descritas devem produzir o mesmo resultado independentemente do modelo de linguagem utilizado.

Não define mérito de uma decisão, não decide pelo cliente e não autoriza agentes a operar nas camadas humanas. Também não resolve, por si, conflitos documentais ainda abertos; quando houver divergência entre fontes controladas, a implementação deve registrá-la e operar de forma conservadora até decisão explícita.

## 3. Conteúdo

### 3.1 Objetos mínimos do domínio executável

| **Objeto**     | **Função**                                  | **Campos mínimos**                                                                           |
|----------------|---------------------------------------------|----------------------------------------------------------------------------------------------|
| **Caso**       | Unidade isolada de um engajamento.          | id, organização/processo, versão do playbook, nível, etapa atual, estado do selo.            |
| **Playbook**   | Declara como o percurso deve ser executado. | versão, etapas, camada por nível, modalidade, portões, inegociáveis, rótulos de procedência. |
| **Etapa**      | Unidade de avanço do percurso.              | id, pré-requisitos, camada por nível, modalidade, critério de encerramento, dependências.    |
| **Asserção**   | Informação aceita no caso.                  | texto/valor, autor pessoa, contexto, origem, fonte e, quando numérica, apuração.             |
| **Sessão**     | Registro de atividade humana exigida.       | etapa, modalidade, data, participantes, responsável pelo registro.                           |
| **Entregável** | Saída autorizada por portão.                | id, etapas exigidas, inegociáveis, condição específica.                                      |
| **Evento**     | Rastro de mudança ou negativa.              | tipo, data/hora, caso, etapa, ator, resultado e motivo.                                      |

### 3.2 Invariantes de carga do playbook

Um playbook que omita qualquer uma das condições abaixo é inválido e o caso não deve operar:

| **ID**   | **Invariante**                                                                  |
|----------|---------------------------------------------------------------------------------|
| **P-01** | Toda etapa declara camada de execução por nível N1, N2 e N3.                    |
| **P-02** | Toda etapa declara modalidade de execução.                                      |
| **P-03** | Todo entregável declara exatamente um portão com etapas exigidas.               |
| **P-04** | Existe uma lista de itens inegociáveis e ela não é vazia.                       |
| **P-05** | Existem rótulos de procedência reconhecidos pelo validador.                     |
| **P-06** | O playbook possui versão e essa versão é copiada para o caso na abertura.       |
| **P-07** | Etapas dependentes de presença ou sessão declaram a dependência explicitamente. |

### 3.3 Camadas de execução

| **Camada**               | **Natureza**           | **Regra executável**                                                                                                                             |
|--------------------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **EX1 — Conversacional** | Automatizado e híbrido | Pode estruturar coleta declarativa, triagem e cálculos determinísticos previstos; o que for híbrido exige confirmação antes de gravar conclusão. |
| **EX2 — Analítica**      | Automatizado e híbrido | Pode consultar referências, estruturar análises e produzir hipóteses/minutas; inferência permanece marcada como inferência até validação.        |
| **EX3 — Verificação**    | Humano                 | Agente pode preparar insumo, mas não produz a saída verificada nem encerra a atividade em nome da pessoa.                                        |
| **EX4 — Julgamento**     | Humano                 | Agente não decide priorização, autonomia, curadoria final ou aceite. A atividade exige pessoa nomeada.                                           |

Nenhum agente opera em EX3 ou EX4. A camada de uma etapa pode mudar conforme o nível do caso; sem nível apurado, aplica-se a interpretação mais restritiva declarada e nenhuma etapa posterior a F0 deve operar.

### 3.4 Matriz inicial de etapas e modalidade

| **Etapa**  | **N1**            | **N2**            | **N3**            | **Modalidade**  | **Regra especial**                                                                       |
|------------|-------------------|-------------------|-------------------|-----------------|------------------------------------------------------------------------------------------|
| **F0**     | EX1               | EX1               | EX1               | assíncrona      | Deve concluir com nível apurado.                                                         |
| **P1**     | EX2               | EX2               | EX3               | vídeo           | Em N3, verificação humana obrigatória.                                                   |
| **P2**     | EX2               | EX2               | EX3               | assíncrona      | Fontes críticas não podem permanecer apenas declaradas ao encerrar.                      |
| **P3a**    | EX2               | EX3               | EX3               | remota          | Linha de base segue regra de apuração do método.                                         |
| **P3b**    | EX4               | EX4               | EX4               | presencial      | Não possui comando de execução por agente.                                               |
| **P3d**    | EX3               | EX3               | EX3               | remota          | Exige sessão P3b registrada.                                                             |
| **P4**     | EX2               | EX3               | EX3               | vídeo           | Decisão do patrocinador precisa ser registrada.                                          |
| **P5**     | EX3               | EX3               | EX3               | vídeo           | Classificação tecnológica validada por pessoa; E3-E só abre se houver caso agêntico.     |
| **P6–P10** | conforme playbook | conforme playbook | conforme playbook | conforme método | As habilidades só podem existir após os instrumentos correspondentes serem formalizados. |

### 3.5 Procedência e apuração

A especificação de implementação usa três dimensões independentes para impedir que contexto de coleta, origem da informação e natureza de um número sejam confundidos. O contexto é atribuído pelo sistema; origem e apuração devem ser compatíveis com a evidência registrada.

| **Dimensão** | **Valores previstos**                       | **Regra**                                                                                                                                          |
|--------------|---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **Contexto** | campo · antitese · conversa · livre         | Atribuído pelo sistema conforme a origem da sessão; o operador não escolhe livremente.                                                             |
| **Origem**   | verificado · declarado · inferido · externo | Toda asserção possui um valor. Inferido e externo não se tornam verificados por edição do rótulo; uma nova evidência gera nova asserção/histórico. |
| **Apuração** | medido · calculado · estimado               | Obrigatória para asserção numérica. Medido exige amostra/período; calculado exige fórmula/entradas; estimado exige base e margem.                  |

| **Pendência documental.** EMCIA-MET-01, EMCIA-CAT-01 e EMCIA-GLO-01 ainda utilizam as marcas declarado/inferido/verificado como taxonomia principal. A implementação não deve tratar essa divergência como resolvida por conveniência. Até revisão controlada, a compatibilidade deve ser explícita e a decisão registrada. |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

### 3.6 Regras de escrita

A escrita em áreas aceitas do caso deve possuir um único caminho autorizado. Saídas de agente ou humano podem existir em rascunho, mas somente o validador registra em caso/ ou altera registro/.

| **Regra** | **Comportamento esperado**                                                              |
|-----------|-----------------------------------------------------------------------------------------|
| **E-01**  | Escrita direta em caso/ e registro/ é recusada.                                         |
| **E-02**  | Toda asserção gravada possui autor pessoa nomeada; identificador de agente não é autor. |
| **E-03**  | Toda asserção possui contexto e origem válidos; número possui também apuração.          |
| **E-04**  | Asserção inferida exige premissa explícita.                                             |
| **E-05**  | Asserção externa exige fonte, data de captura e limite da fonte.                        |
| **E-06**  | Linha de base não aceita valor estimado quando o critério do método exigir medição.     |
| **E-07**  | Recusa sempre gera evento; falha silenciosa é defeito.                                  |

### 3.7 Estado e transições

O estado do caso deve ser pequeno, legível e reproduzível. No mínimo registra etapa corrente, nível, sessões obrigatórias, itens cumpridos, entregáveis autorizados e selo. As transições seguem regras determinísticas:

| **Transição**             | **Pré-condição**                                  | **Resultado**                                                                                               |
|---------------------------|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Abrir caso**            | playbook válido                                   | Caso em F0, nível não apurado, versão do playbook congelada.                                                |
| **Encerrar F0**           | nove respostas válidas e nível apurado            | Nível passa a governar a resolução das camadas.                                                             |
| **Registrar sessão**      | atividade humana realizada e responsável nomeado  | Dependências de campo podem ser satisfeitas.                                                                |
| **Encerrar etapa**        | critério de encerramento + dependências atendidas | Estado avança para a próxima etapa prevista.                                                                |
| **Autorizar entregável**  | portão atendido + inegociáveis satisfeitos        | Entregável pode ser emitido; autorização não implica geração automática do documento.                       |
| **Selar braço declarado** | execução declarada encerrada antes do campo       | Conteúdo fica imutável para fins de comparação; correções posteriores viram novo registro, não sobrescrita. |

### 3.8 Portões de entregáveis

| **Entregável**                      | **Portão mínimo**                        | **Regra especial**                                                          |
|-------------------------------------|------------------------------------------|-----------------------------------------------------------------------------|
| **E1 — Ficha de enquadramento**     | F0 encerrada                             | Nível deve estar registrado como resultado da triagem.                      |
| **E2 — Diagnóstico e oportunidade** | P1, P2, P3a, P3b e P3d encerrados        | Linha de base atende ao inegociável e as regras levantadas possuem autoria. |
| **E3-D — Decisão**                  | P4 e P5 encerrados                       | Existe sempre, inclusive quando a decisão é não usar agente.                |
| **E3-E — Especificação**            | P5 concluiu ao menos um caso como agente | Não pode ser emitido quando nenhum caso é agêntico.                         |
| **E4 — Guia operacional**           | portão a detalhar com P6–P7              | Termo de autonomia é inegociável.                                           |
| **E5 — Relatório de piloto**        | portão a detalhar com P8–P10             | Exige métrica de resultado e responsável de calibragem.                     |

### 3.9 Regras mínimas de guarda

| **ID** | **Regra**                                            | **O que impede**                                               |
|--------|------------------------------------------------------|----------------------------------------------------------------|
| **G1** | Habilidade de camada humana não carrega para agente. | Agente executar atividade que exige verificação ou julgamento. |
| **G2** | Escrita direta em caso/ e registro/ é negada.        | Asserção sem procedência e avanço fora do validador.           |
| **G3** | Etapa dependente de sessão exige sessão registrada.  | Produzir confronto “de campo” sem campo.                       |
| **G4** | Nenhuma etapa após F0 opera sem nível apurado.       | Caso usar a fronteira mais permissiva por ausência de triagem. |

### 3.10 Eventos mínimos

A trilha deve permitir reconstruir decisões de estado e provar que uma negativa foi técnica, não apenas uma resposta do modelo. O conjunto mínimo de eventos previsto é:

| **Evento**               | **Quando ocorre**                                                                    |
|--------------------------|--------------------------------------------------------------------------------------|
| **CasoAberto**           | criação de um caso com playbook e versão registrados.                                |
| **AssercaoGravada**      | validador aceita conteúdo e grava no caso.                                           |
| **AssercaoRecusada**     | conteúdo falha em schema, procedência ou regra de escrita.                           |
| **TentativaNegada**      | guarda impede habilidade, comando, leitura ou escrita por violação de camada/estado. |
| **SessaoRegistrada**     | atividade humana exigida é registrada.                                               |
| **EtapaEncerrada**       | critério de encerramento e dependências são satisfeitos.                             |
| **EntregavelAutorizado** | portão do entregável é satisfeito.                                                   |
| **CasoSelado**           | braço declarado ou outro recorte é congelado para comparação.                        |

### 3.11 Comportamento conservador

Quando uma condição necessária estiver ausente ou ambígua, o sistema não deve escolher a interpretação mais permissiva. Sem nível, utiliza-se a camada mais restritiva declarada; sem procedência suficiente, não se grava; sem sessão exigida, não se encerra; sem portão satisfeito, não se autoriza entregável. O núcleo não avalia mérito do conteúdo: recusa omissão estrutural e violação de contrato.

### 3.12 Critério de verificação técnica

Cada regra executável relevante precisa de ao menos um teste positivo ou negativo. Os testes devem distinguir obediência do modelo de bloqueio técnico: uma recusa só prova a guarda quando o evento correspondente existe e o estado não foi alterado.

| **Caso de teste**                                                 | **Esperado**                                                     |
|-------------------------------------------------------------------|------------------------------------------------------------------|
| **Gravar asserção válida com procedência completa**               | grava e emite AssercaoGravada.                                   |
| **Gravar diretamente em caso/**                                   | recusa e emite TentativaNegada.                                  |
| **Carregar habilidade EX4 por agente**                            | recusa e emite TentativaNegada.                                  |
| **Executar P1 em N3 por agente**                                  | recusa; a mesma ação em N1 pode ser permitida conforme playbook. |
| **Encerrar P3d sem sessão P3b**                                   | recusa sem alterar estado.                                       |
| **Emitir E3-E sem caso agêntico**                                 | recusa por portão.                                               |
| **Usar estimativa como linha de base onde medição é obrigatória** | recusa ou mantém item inegociável pendente.                      |

## 4. Condição de aceite

Este artefato está pronto quando:

- o playbook possui contrato mínimo suficiente para ser validado antes da abertura do caso;
- camada, modalidade, estado, procedência, escrita e portões possuem regras determinísticas e não dependem de julgamento do LLM;
- P3b está explicitamente preservado como atividade humana presencial sem comando de agente;
- o comportamento conservador para ausência de nível, procedência, sessão ou portão está definido;
- a divergência documental de procedência está registrada como pendência, e não ocultada;
- cada guarda e transição crítica possui critério de teste; e
- um implementador consegue derivar schemas, validadores e testes sem tomar nova decisão metodológica.

## 5. Referências

- EMCIA-ARQ-01 — Arquitetura do Estúdio interno.
- EMCIA-IMP-01 — Plano de implementação do Estúdio.
- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-TRI-01 — Instrumento de triagem da Fase 0.
- EMCIA-VER-01 — Plano de verificação.
- EMCIA-GLO-01 — Glossário do método.
- Estúdio como Plugin — Conceito e Arquitetura (documento interno, setembro de 2026).
- Guia do Engenheiro de Campo — Estúdio (documento interno, setembro de 2026).

## 6. Histórico de revisões

| **Versão** | **Data**   | **Autor**     | **Descrição da alteração**                                                                                | **Aprovação** |
|------------|------------|---------------|-----------------------------------------------------------------------------------------------------------|---------------|
| **0.1**    | 17/09/2026 | Celso do Vale | Versão inicial: contratos de playbook, camadas, procedência, escrita, estado, portões, guardas e eventos. | —             |
