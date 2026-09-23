# Ferramentas em detalhe
### Fase F2 — Desenho

| Metadado | Valor | Metadado | Valor |
| :--- | :--- | :--- | :--- |
| **Código** | EMCIA-FER-F2-01 | **Versão** | 0.1 |
| **Data** | 14/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Fase F2 | **Passos** | 4 e 5 |

---

## 1. Objetivo
Detalhar cada instrumento selecionado para esta fase, de modo que um engenheiro que não participou da seleção saiba quando aplicá-lo, como aplicá-lo e quando parar. Este documento é auxiliar do quadro de ferramentas EMCIA-FER-01, que registra a seleção; aqui está a aplicação.

## 2. Escopo e aplicação
Aplica-se aos 12 instrumentos selecionados para a fase F2 — Desenho. A sigla é a mesma do quadro e permanece estável ainda que o instrumento seja reposicionado.

Fase em que a decisão precede a classificação. Priorizar depois de escolher a tecnologia produz caso de uso selecionado pela ferramenta disponível.

## 3. Fichas
O campo de erro comum registra a falha observada na aplicação do instrumento, e não a sua limitação teórica. É o campo de maior valor para quem aplica pela primeira vez.

---

### ADM-09 · Matriz de Priorização com zona de contenção ★

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Decidir o que atacar primeiro e com que grau de cautela, entre os candidatos levantados. |
| **Quando aplicar** | Passo 4, sobre a saída do Mapa de Valor. |
| **Como aplicar** | 1. Posicionar todos os candidatos, inclusive os que serão descartados.<br>2. Aplicar a zona de contenção antes de comparar impacto.<br>3. Registrar a decisão do patrocinador, inclusive quando for não seguir. |
| **Insumo e saída** | Pontos candidatos do Mapa de Valor → Matriz preenchida e decisão registrada |
| **Erro comum** | Registrar apenas o caso escolhido, o que impede a organização de reavaliar a decisão depois. |
| **Encerramento** | Todos os candidatos presentes e decisão do patrocinador registrada com data. |
| **Exigida em** | Todos |

---

### ADM-10 · Matriz de impacto e esforço

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer quais lacunas compensam o esforço de fechar, entre as identificadas no diagnóstico. |
| **Quando aplicar** | Passo 4, quando o diagnóstico revelar mais lacunas do que o engajamento alcança. |
| **Como aplicar** | 1. Estimar esforço com quem vai executar, e não com quem decide.<br>2. Separar esforço de construção de esforço de mudança organizacional.<br>3. Marcar as lacunas que bloqueiam outras. |
| **Insumo e saída** | Lacunas do diagnóstico → Lacunas posicionadas, com bloqueios marcados |
| **Erro comum** | Estimar esforço sem consultar quem executará, o que subestima sistematicamente a mudança. |
| **Encerramento** | Lacunas posicionadas, com dependências entre elas declaradas. |
| **Exigida em** | N2 e N3 |

---

### ADM-11 · Identificação de ganho rápido

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Selecionar o caso que gera adesão antes que o resultado maior apareça. |
| **Quando aplicar** | Passo 4, após a priorização. |
| **Como aplicar** | 1. Procurar o caso de menor esforço entre os priorizados.<br>2. Verificar se o ganho é perceptível a quem opera, e não apenas ao patrocinador.<br>3. Confirmar que não depende de acesso ainda pendente. |
| **Insumo e saída** | Casos priorizados → Caso de entrada identificado |
| **Erro comum** | Escolher o ganho rápido pelo menor esforço técnico, ignorando se alguém perceberá o efeito. |
| **Encerramento** | Caso identificado, com o efeito perceptível declarado. |
| **Exigida em** | Todos |

---

### IA-01 · Matriz Problema→Tecnologia ★

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer que tecnologia a natureza do problema exige, incluindo a conclusão de que nenhum agente é necessário. |
| **Quando aplicar** | Passo 5, após a decisão do passo 4. |
| **Como aplicar** | 1. Classificar a natureza do problema antes de considerar qualquer tecnologia.<br>2. Registrar a justificativa da classificação, e não apenas o resultado.<br>3. Separar caso agêntico, caso isolado e habilitador acoplado. |
| **Insumo e saída** | Casos priorizados e camada de contexto → Classificação por caso, com justificativa |
| **Erro comum** | Aplicar antes da priorização, o que faz a tecnologia escolher o caso. |
| **Encerramento** | Cada caso classificado, com justificativa e confirmação do engenheiro. |
| **Exigida em** | Todos |

---

### IA-02 · Distinção entre IA discriminativa e generativa

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Impedir que o caso peça criação quando precisa de previsão, ou o contrário. |
| **Quando aplicar** | Passo 5, junto com a classificação. |
| **Como aplicar** | 1. Perguntar se a saída esperada é uma escolha entre opções ou um texto novo.<br>2. Verificar se existe histórico rotulado disponível.<br>3. Registrar quando as duas se combinam no mesmo caso. |
| **Insumo e saída** | Caso classificado → Natureza da tecnologia declarada |
| **Erro comum** | Adotar modelo generativo para problema de classificação, por disponibilidade da ferramenta. |
| **Encerramento** | Natureza declarada, com justificativa ligada à saída esperada. |
| **Exigida em** | Todos |

---

### BD-06 · Arquitetura em zonas bruta, curada e analítica

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Definir como o dado é organizado antes de ser consumido pela solução. |
| **Quando aplicar** | Passo 5, sobre as fontes críticas. |
| **Como aplicar** | 1. Verificar o que já existe antes de propor zonas novas.<br>2. Declarar em que zona a solução lê.<br>3. Registrar a transformação exigida entre zonas. |
| **Insumo e saída** | Inventário e classificação das fontes → Arquitetura de acesso declarada |
| **Erro comum** | Especificar zonas que a organização não tem condição de manter. |
| **Encerramento** | Zona de leitura declarada por fonte crítica. |
| **Exigida em** | N2 e N3 |

---

### BD-07 · Fluxo de ingestão e tipos de carga

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer com que frescor o dado chega, e a que custo. |
| **Quando aplicar** | Passo 5, após a arquitetura de zonas. |
| **Como aplicar** | 1. Partir da criticidade da decisão, e não da capacidade técnica disponível.<br>2. Declarar a defasagem aceitável por fonte.<br>3. Estimar o custo da carga na frequência exigida. |
| **Insumo e saída** | Requisitos da decisão automatizada → Frequência e custo por fonte |
| **Erro comum** | Especificar carga contínua onde a decisão tolera defasagem diária. |
| **Encerramento** | Frequência declarada por fonte, com a defasagem aceitável justificada. |
| **Exigida em** | N2 e N3 |

---

### BD-08 · Metadados de negócio e contratos de dados

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Formalizar o significado do dado entre as áreas que o produzem e o consomem. |
| **Quando aplicar** | Passo 5, sobre as fontes do processo-alvo. |
| **Como aplicar** | 1. Partir do glossário do passo 2.<br>2. Declarar estrutura, significado e qualidade esperada por fonte.<br>3. Nomear quem responde pelo contrato de cada lado. |
| **Insumo e saída** | Glossário e inventário de fontes → Contratos com responsáveis nomeados |
| **Erro comum** | Tratar o contrato como documentação técnica, sem responsável de negócio do lado produtor. |
| **Encerramento** | Cada fonte crítica com contrato e dois responsáveis nomeados. |
| **Exigida em** | N2 e N3 |

---

### IA-03 · Regras de negócio como testes automáticos

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Tornar a regra verificável em execução, e não apenas escrita. |
| **Quando aplicar** | Passo 5, sobre as regras verificadas no passo 3. |
| **Como aplicar** | 1. Escolher as regras que decidem o resultado.<br>2. Escrever entrada e saída esperada para cada uma.<br>3. Vincular o teste à regra, para que a mudança de uma exija a revisão do outro. |
| **Insumo e saída** | Regras verificadas do passo 3 → Casos de teste vinculados às regras |
| **Erro comum** | Escrever testes sobre a regra documentada, e não sobre a regra praticada. |
| **Encerramento** | Toda regra crítica com ao menos um caso de teste vinculado. |
| **Exigida em** | N3 |

---

### BD-09 · Menor privilégio, controle de acesso e criptografia

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Definir quem e o que acessa cada dado, e sob que condição. |
| **Quando aplicar** | Passo 5, junto com a especificação da solução. |
| **Como aplicar** | 1. Partir da permissão mínima e acrescentar apenas o necessário.<br>2. Distinguir identidade da solução da identidade do usuário.<br>3. Declarar o tratamento do dado sensível em trânsito e em repouso. |
| **Insumo e saída** | Fontes classificadas por sensibilidade → Permissões declaradas por ferramenta |
| **Erro comum** | Conceder à solução as permissões do usuário que a opera, por conveniência de implantação. |
| **Encerramento** | Permissão declarada por ferramenta, no menor privilégio. |
| **Exigida em** | Todos |

---

### ADM-12 · Classificação da informação

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Tornar o controle proporcional à sensibilidade do dado tratado. |
| **Quando aplicar** | Passo 5, antes da definição de acessos. |
| **Como aplicar** | 1. Classificar as fontes que a solução consome.<br>2. Verificar a existência de política interna antes de propor classificação própria.<br>3. Registrar o dado pessoal separadamente. |
| **Insumo e saída** | Inventário de fontes → Fontes classificadas por sensibilidade |
| **Erro comum** | Classificar sistemas em vez de dados, o que mascara o dado sensível em sistema comum. |
| **Encerramento** | Toda fonte consumida pela solução classificada. |
| **Exigida em** | N2 e N3 |

---

### ADM-13 · Estimativa de custo por tarefa e latência

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se a solução cabe no orçamento e no tempo de resposta que o processo admite. |
| **Quando aplicar** | Passo 5, ao final. |
| **Como aplicar** | 1. Estimar por unidade de trabalho do processo, e não por mês.<br>2. Declarar as premissas de volume.<br>3. Fixar o teto mensal e o que acontece ao atingi-lo. |
| **Insumo e saída** | Desenho da solução e volume do processo → Custo por tarefa, teto e latência declarados |
| **Erro comum** | Estimar custo mensal sem declarar o volume que o sustenta, o que impede reavaliar quando o volume muda. |
| **Encerramento** | Custo por tarefa com premissas expostas e teto declarado. |
| **Exigida em** | Todos |

---

## 4. Condição de aceite
Este artefato está pronto quando todo instrumento selecionado para a fase tem os sete campos preenchidos; quando o campo de encerramento permite verificar, sem consulta a terceiros, se a aplicação terminou; e quando o erro comum descreve falha de aplicação, e não limitação do instrumento.

## 5. Referências
* **Artefatos relacionados:** EMCIA-FER-01, EMCIA-MET-01, EMCIA-GLO-01.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
| :---: | :---: | :--- | :--- | :---: |
| **0.1** | 14/09/2026 | Celso do Vale | Versão inicial: fichas dos 12 instrumentos da fase | — |