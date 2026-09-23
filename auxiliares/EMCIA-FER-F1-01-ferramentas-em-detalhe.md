# Ferramentas em detalhe
### Fase F1 — Diagnóstico

| Metadado | Valor | Metadado | Valor |
| :--- | :--- | :--- | :--- |
| **Código** | EMCIA-FER-F1-01 | **Versão** | 0.1 |
| **Data** | 14/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Fase F1 | **Passos** | 1, 2 e 3 |

---

## 1. Objetivo
Detalhar cada instrumento selecionado para esta fase, de modo que um engenheiro que não participou da seleção saiba quando aplicá-lo, como aplicá-lo e quando parar. Este documento é auxiliar do quadro de ferramentas EMCIA-FER-01, que registra a seleção; aqui está a aplicação.

## 2. Escopo e aplicação
Aplica-se aos 15 instrumentos selecionados para a fase F1 — Diagnóstico. A sigla é a mesma do quadro e permanece estável ainda que o instrumento seja reposicionado.

Fase que concentra o limite arquitetural do método. Os instrumentos dos passos 1 e 2 operam sobre o declarado; os do passo 3 existem para produzir o que a organização não consegue declarar.

## 3. Fichas
O campo de erro comum registra a falha observada na aplicação do instrumento, e não a sua limitação teórica. É o campo de maior valor para quem aplica pela primeira vez.

---

### ADM-05 · Maturidade de IA em cinco níveis, Gartner

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Posicionar a organização sem exigir instrumentação prévia, o que importa justamente onde a maturidade é o que falta medir. |
| **Quando aplicar** | Passo 1, na sessão com o patrocinador. |
| **Como aplicar** | 1. Aplicar às quatro frentes separadamente.<br>2. Registrar nível atual e nível pretendido.<br>3. Anotar a evidência que sustenta cada posição. |
| **Insumo e saída** | Declarações sobre uso atual de IA → Nível por frente, com lacuna e alvo |
| **Erro comum** | Atribuir um nível único à organização, dissolvendo a assimetria entre frentes. |
| **Encerramento** | Nível por frente, cada um com evidência registrada. |
| **Exigida em** | Todos |

---

### ADM-06 · Maturidade de IA, IBM

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Oferecer leitura alternativa para triangular o diagnóstico do instrumento anterior. |
| **Quando aplicar** | Passo 1, depois da aplicação da Gartner. |
| **Como aplicar** | 1. Aplicar sobre o mesmo material.<br>2. Comparar as duas leituras.<br>3. Registrar as divergências, sem conciliá-las. |
| **Insumo e saída** | Resultado do instrumento anterior → Divergências entre as duas leituras |
| **Erro comum** | Somar ou promediar os dois resultados, como se fossem escalas comparáveis. |
| **Encerramento** | Divergências registradas e comentadas. |
| **Exigida em** | N3 |

---

### NEG-04 · Quatro frentes de incorporação

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Medir amplitude — em quantas superfícies do negócio a IA já entrou — e não profundidade. |
| **Quando aplicar** | Passo 1, junto com o modelo de maturidade. |
| **Como aplicar** | 1. Verificar em quais frentes há uso real.<br>2. Distinguir uso experimental de uso incorporado ao processo.<br>3. Registrar também a frente sem uso algum. |
| **Insumo e saída** | Declarações sobre iniciativas em curso → Quatro frentes classificadas |
| **Erro comum** | Tratar as frentes como etapas sequenciais, quando são superfícies independentes. |
| **Encerramento** | As quatro frentes classificadas, com exemplo por frente. |
| **Exigida em** | Todos |

---

### NEG-05 · Pirâmide DIKW

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Identificar se a organização decide a partir de dado, de informação ou de conhecimento acumulado. |
| **Quando aplicar** | Passo 1. |
| **Como aplicar** | 1. Perguntar o que sustenta as decisões correntes do processo-alvo.<br>2. Pedir um exemplo concreto da última decisão relevante.<br>3. Posicionar com base no exemplo, e não na declaração. |
| **Insumo e saída** | Relato sobre decisões recentes → Posição registrada, com exemplo |
| **Erro comum** | Usar como diagnóstico de maturidade em vez de posicionamento. |
| **Encerramento** | Posição registrada com ao menos um exemplo verificável. |
| **Exigida em** | N2 e N3 |

---

### ADM-07 · Caso de negócio com VPL e TIR

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Sustentar financeiramente a decisão de investimento, quando a organização a exige nesses termos. |
| **Quando aplicar** | Passo 1, após o custo do problema. |
| **Como aplicar** | 1. Partir do custo anual já estimado na Fase F0.<br>2. Projetar o horizonte com faixa de incerteza declarada.<br>3. Separar custo evitado de receita adicional. |
| **Insumo e saída** | Custo do problema e estimativa de esforço → Retorno projetado, com premissas |
| **Erro comum** | Apresentar projeção com a mesma ênfase de valor medido. |
| **Encerramento** | Cálculo reproduzível a partir das premissas registradas. |
| **Exigida em** | N3 |

---

### BD-01 · Modelo de maturidade de dados, CMMI

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se a gestão de dados sustenta o caso pretendido, antes de projetá-lo. |
| **Quando aplicar** | Passo 2, no início. |
| **Como aplicar** | 1. Avaliar apenas os domínios que o processo-alvo consome.<br>2. Registrar evidência por domínio avaliado.<br>3. Marcar como declarado o que não pôde ser verificado. |
| **Insumo e saída** | Documentação e declarações sobre gestão de dados → Nível por domínio crítico |
| **Erro comum** | Avaliar a organização inteira, quando só interessam os domínios do processo-alvo. |
| **Encerramento** | Domínios críticos avaliados, com evidência ou marca de declarado. |
| **Exigida em** | N2 e N3 |

---

### BD-02 · Taxonomia de dados por estrutura

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Classificar as fontes em estruturadas, semiestruturadas e não estruturadas, o que condiciona a arquitetura do passo 5. |
| **Quando aplicar** | Passo 2, junto com o inventário. |
| **Como aplicar** | 1. Classificar cada fonte do processo-alvo.<br>2. Registrar o volume aproximado por categoria.<br>3. Sinalizar fonte não estruturada de uso decisório. |
| **Insumo e saída** | Lista de fontes → Fontes classificadas por estrutura |
| **Erro comum** | Classificar pelo sistema de origem, e não pela forma do dado que o processo consome. |
| **Encerramento** | Toda fonte do processo-alvo classificada. |
| **Exigida em** | Todos |

---

### BD-03 · Inventário de fontes internas e externas

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer de onde vem cada dado que o processo consome. |
| **Quando aplicar** | Passo 2, primeira atividade. |
| **Como aplicar** | 1. Partir do fluxo do processo, e não do mapa de sistemas.<br>2. Registrar criticidade por fonte.<br>3. Marcar como declarada toda fonte ainda sem acesso verificado. |
| **Insumo e saída** | Descrição do processo e documentação disponível → Lista de fontes com criticidade e procedência |
| **Erro comum** | Inventariar sistemas em vez de fontes, o que omite planilhas e registros informais. |
| **Encerramento** | Toda fonte com criticidade atribuída e procedência marcada. |
| **Exigida em** | Todos |

---

### NEG-06 · Glossário de negócio

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer se as áreas usam os mesmos termos com o mesmo sentido — insumo primário da camada de contexto. |
| **Quando aplicar** | Passo 2, em paralelo ao inventário. |
| **Como aplicar** | 1. Coletar de dez a vinte termos do processo-alvo.<br>2. Pedir a definição a mais de uma área.<br>3. Registrar a divergência, sem conciliá-la. |
| **Insumo e saída** | Documentos e entrevistas → Termos com definição e divergências marcadas |
| **Erro comum** | Conciliar definições divergentes no diagnóstico, apagando o achado mais valioso do passo. |
| **Encerramento** | Termos registrados, com as divergências explícitas. |
| **Exigida em** | Todos |

---

### BD-04 · Catálogo de dados

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se os ativos críticos estão documentados e têm dono declarado. |
| **Quando aplicar** | Passo 2, em organizações com estrutura formal de dados. |
| **Como aplicar** | 1. Verificar existência de catálogo antes de propor um.<br>2. Conferir se o processo-alvo está coberto.<br>3. Registrar quem responde por cada ativo crítico. |
| **Insumo e saída** | Estrutura existente de metadados → Cobertura do processo-alvo no catálogo |
| **Erro comum** | Propor a construção de catálogo quando o escopo é especificar, e não implantar. |
| **Encerramento** | Cobertura verificada, com donos nomeados. |
| **Exigida em** | N3 |

---

### BD-05 · Linhagem de dados

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer se é possível rastrear o dado da origem ao uso, o que condiciona a confiabilidade da decisão automatizada. |
| **Quando aplicar** | Passo 2, sobre as fontes críticas. |
| **Como aplicar** | 1. Escolher a fonte de maior criticidade.<br>2. Reconstituir o caminho até o ponto de decisão.<br>3. Registrar cada transformação sem responsável identificado. |
| **Insumo e saída** | Fontes críticas inventariadas → Caminho do dado, com pontos cegos marcados |
| **Erro comum** | Aceitar a linhagem documentada sem conferir uma amostra real. |
| **Encerramento** | Caminho reconstituído para ao menos a fonte mais crítica. |
| **Exigida em** | N2 e N3 |

---

### NEG-07 · Mapa de Valor ★

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Localizar onde na organização há concentração de oportunidade, antes de escolher o que atacar. |
| **Quando aplicar** | Passo 3, primeira atividade. |
| **Como aplicar** | 1. Percorrer a cadeia de valor do processo-alvo.<br>2. Marcar os pontos de espera, retrabalho e decisão manual.<br>3. Registrar a etapa que origina cada ponto. |
| **Insumo e saída** | Fluxo do processo → Pontos candidatos a intervenção, rastreáveis à etapa |
| **Erro comum** | Aplicar após a priorização, invertendo a ordem de descoberta e decisão. |
| **Encerramento** | Pontos candidatos registrados, cada um ligado à etapa que o originou. |
| **Exigida em** | Todos |

---

### NEG-08 · Mapeamento do fluxo atual

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Descrever como o processo funciona hoje, etapa a etapa, distinguindo o documentado do praticado. |
| **Quando aplicar** | Passo 3, com quem executa. |
| **Como aplicar** | 1. Desenhar a partir do relato de quem executa, não da documentação.<br>2. Confrontar depois com o fluxo documentado.<br>3. Marcar visualmente onde os dois divergem. |
| **Insumo e saída** | Relato do executor e documentação existente → Fluxo do estado atual, com divergências marcadas |
| **Erro comum** | Desenhar a partir da documentação e validar por confirmação, o que produz concordância nominal. |
| **Encerramento** | Fluxo desenhado e confirmado por leitura de volta com o executor. |
| **Exigida em** | Todos |

---

### NEG-09 · Levantamento de regras não documentadas

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Tornar explícita a regra que decide o resultado e que ninguém escreveu — o que a execução declarada não alcança. |
| **Quando aplicar** | Passo 3, em sessão presencial. |
| **Como aplicar** | 1. Perguntar pela exceção, e não pela regra: o caso em que não se faz o de sempre.<br>2. Repetir a pergunta sob outro ângulo, a intervalos, para expor a omissão.<br>3. Escrever a regra na forma se-então e devolvê-la ao autor para correção. |
| **Insumo e saída** | Presença junto a quem executa o processo → Regras escritas, com autoria nominal e leitura de volta |
| **Erro comum** | Aceitar a primeira formulação. A regra decisiva costuma aparecer na terceira tentativa, quando o executor corrige o que se escreveu. |
| **Encerramento** | Cada regra com autor identificado e leitura de volta registrada. |
| **Exigida em** | Todos |

---

### ADM-08 · Linha de base de tempo, custo, erro e retrabalho

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer o estado do processo antes de qualquer intervenção, contra o qual o resultado será medido. |
| **Quando aplicar** | Passo 3, antes de qualquer piloto. |
| **Como aplicar** | 1. Escolher no máximo quatro indicadores.<br>2. Declarar se cada valor é medido ou estimado.<br>3. Datar o registro. |
| **Insumo e saída** | Processo mapeado e acesso a registros → Linha de base datada, com origem por indicador |
| **Erro comum** | Registrar após o início do piloto, o que torna a comparação impossível. |
| **Encerramento** | Indicadores registrados, datados e com origem declarada. |
| **Exigida em** | Todos |

---

## 4. Condição de aceite
Este artefato está pronto quando todo instrumento selecionado para a fase tem os sete campos preenchidos; quando o campo de encerramento permite verificar, sem consulta a terceiros, se a aplicação terminou; e quando o erro comum descreve falha de aplicação, e não limitação do instrumento.

## 5. Referências
* **Artefatos relacionados:** EMCIA-FER-01, EMCIA-MET-01, EMCIA-GLO-01.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
| :---: | :---: | :--- | :--- | :---: |
| **0.1** | 14/09/2026 | Celso do Vale | Versão inicial: fichas dos 15 instrumentos da fase | — |