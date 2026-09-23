# Ferramentas em detalhe
### Fase F3 — Operacionalização

| Metadado | Valor | Metadado | Valor |
| :--- | :--- | :--- | :--- |
| **Código** | EMCIA-FER-F3-01 | **Versão** | 0.1 |
| **Data** | 14/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Fase F3 | **Passos** | 6 e 7 |

---

## 1. Objetivo
Detalhar cada instrumento selecionado para esta fase, de modo que um engenheiro que não participou da seleção saiba quando aplicá-lo, como aplicá-lo e quando parar. Este documento é auxiliar do quadro de ferramentas EMCIA-FER-01, que registra a seleção; aqui está a aplicação.

## 2. Escopo e aplicação
Aplica-se aos 11 instrumentos selecionados para a fase F3 — Operacionalização. A sigla é a mesma do quadro e permanece estável ainda que o instrumento seja reposicionado.

Fase em que o método deixa de tratar da solução e passa a tratar de quem convive com ela. Os instrumentos são majoritariamente administrativos porque o que está em jogo é decisão e responsabilidade, não técnica.

## 3. Fichas
O campo de erro comum registra a falha observada na aplicação do instrumento, e não a sua limitação teórica. É o campo de maior valor para quem aplica pela primeira vez.

---

### NEG-10 · Redesenho de processo com visão sistêmica

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer se a solução entra no fluxo de trabalho ou fica ao lado dele. |
| **Quando aplicar** | Passo 6, com as áreas envolvidas. |
| **Como aplicar** | 1. Partir do fluxo atual levantado no passo 3.<br>2. Marcar o ponto exato de entrada: quem, em que momento, em que sistema.<br>3. Identificar quem perde atribuição com a mudança. |
| **Insumo e saída** | Fluxo atual e blueprint da solução → Estado futuro do processo |
| **Erro comum** | Desenhar o estado futuro sem identificar quem perde atribuição, que é quem determina se a mudança pega. |
| **Encerramento** | Estado futuro descrito, com ponto de entrada nominal. |
| **Exigida em** | Todos |

---

### BD-10 · Integração com sistema de gestão

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Definir onde a solução lê e onde escreve, e sob que permissão. |
| **Quando aplicar** | Passo 6, sobre o estado futuro desenhado. |
| **Como aplicar** | 1. Inventariar os pontos de leitura e escrita separadamente.<br>2. Verificar se já existe conector em uso na organização.<br>3. Nomear o responsável por cada conexão. |
| **Insumo e saída** | Estado futuro e inventário de sistemas → Pontos de integração, com donos nomeados |
| **Erro comum** | Especificar conector novo onde já existe um em uso, ampliando a superfície de manutenção. |
| **Encerramento** | Cada ponto com protocolo, operação e responsável declarados. |
| **Exigida em** | N2 e N3 |

---

### IA-04 · Automação determinística complementar

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Resolver com regra fixa o que não precisa de modelo, reduzindo custo e superfície de erro. |
| **Quando aplicar** | Passo 6, ao especificar o fluxo. |
| **Como aplicar** | 1. Identificar as etapas de regra estável dentro do fluxo.<br>2. Separá-las das etapas que exigem julgamento.<br>3. Especificar a automação determinística antes de considerar o modelo. |
| **Insumo e saída** | Estado futuro do processo → Etapas automatizáveis sem modelo |
| **Erro comum** | Delegar ao modelo etapas que uma regra resolve, por uniformidade de implementação. |
| **Encerramento** | Etapas de regra estável identificadas e especificadas separadamente. |
| **Exigida em** | N2 e N3 |

---

### IA-05 · Biblioteca de padrões de instrução

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Especificar o comportamento esperado da solução de forma reutilizável e versionada. |
| **Quando aplicar** | Passo 6, após o desenho do fluxo. |
| **Como aplicar** | 1. Partir das regras verificadas, e não de exemplos genéricos.<br>2. Versionar cada padrão com a regra que o origina.<br>3. Declarar o que o padrão não cobre. |
| **Insumo e saída** | Regras verificadas e estado futuro → Padrões versionados, ligados às regras |
| **Erro comum** | Escrever instrução onde o caso exige política de bloqueio, tornando probabilístico o que deveria ser determinístico. |
| **Encerramento** | Cada padrão ligado à regra de origem e versionado. |
| **Exigida em** | Todos |

---

### ADM-14 · Gestão de mudança

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer quem muda de rotina e quem conduz essa mudança. |
| **Quando aplicar** | Passo 6, em paralelo ao redesenho. |
| **Como aplicar** | 1. Identificar nominalmente quem é afetado.<br>2. Definir o responsável pela condução, que não deve ser o engenheiro.<br>3. Prever período de acompanhamento próximo após a entrada em operação. |
| **Insumo e saída** | Estado futuro do processo → Plano de mudança com responsável nomeado |
| **Erro comum** | Atribuir a condução ao engenheiro de campo, que sai ao final do engajamento. |
| **Encerramento** | Responsável interno nomeado e ciente da atribuição. |
| **Exigida em** | Todos |

---

### ADM-15 · Termo de autonomia ★

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Fixar por escrito o que a solução faz sozinha, o que exige aprovação e o que nunca faz. |
| **Quando aplicar** | Passo 7, com o patrocinador. |
| **Como aplicar** | 1. Partir da matriz de autonomia proposta no blueprint.<br>2. Nomear o aprovador de cada item da segunda lista.<br>3. Obter assinatura de quem tem competência para assiná-la. |
| **Insumo e saída** | Matriz de autonomia do blueprint → Termo assinado, com as três listas |
| **Erro comum** | Redigir as listas em termos gerais. Cada item precisa nomear uma ação concreta, ou não é conversível em política. |
| **Encerramento** | As três listas preenchidas, com aprovadores nomeados e assinatura registrada. |
| **Exigida em** | Todos |

---

### ADM-16 · Política de uso e papéis formais

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer quem responde por quê ao longo da operação. |
| **Quando aplicar** | Passo 7, após o termo de autonomia. |
| **Como aplicar** | 1. Verificar a política existente antes de propor uma nova.<br>2. Nomear papéis, e não áreas.<br>3. Declarar o que acontece quando o responsável deixa a função. |
| **Insumo e saída** | Termo de autonomia e estrutura da organização → Papéis nomeados, com sucessão prevista |
| **Erro comum** | Atribuir responsabilidade a uma área, o que equivale a não atribuir a ninguém. |
| **Encerramento** | Cada papel com nome próprio e regra de sucessão. |
| **Exigida em** | N2 e N3 |

---

### ADM-17 · Avaliação de impacto sobre proteção de dados

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se o tratamento de dado pessoal é lícito e proporcional ao fim declarado. |
| **Quando aplicar** | Passo 7, quando houver dado pessoal no processo-alvo. |
| **Como aplicar** | 1. Identificar o dado pessoal tratado e a base legal invocada.<br>2. Avaliar se a finalidade justifica o volume tratado.<br>3. Registrar as medidas de mitigação adotadas. |
| **Insumo e saída** | Fontes classificadas e desenho da solução → Avaliação registrada, com medidas |
| **Erro comum** | Tratar a avaliação como formalidade posterior, quando ela pode inviabilizar o desenho. |
| **Encerramento** | Avaliação concluída antes do início do piloto. |
| **Exigida em** | N3 |

---

### BD-11 · Trilha de auditoria das ações da solução

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Permitir reconstruir o que a solução fez, quando e sob qual decisão humana. |
| **Quando aplicar** | Passo 7, junto com a governança. |
| **Como aplicar** | 1. Declarar o que se registra: entrada, ferramenta acionada, saída e aprovação.<br>2. Definir retenção e quem acessa a trilha.<br>3. Verificar se a trilha permite reconstituir um caso específico. |
| **Insumo e saída** | Especificação da solução → Registro definido, com retenção e acesso |
| **Erro comum** | Registrar apenas a saída, o que impede reconstituir por que a decisão foi tomada. |
| **Encerramento** | Registro definido e testado contra a reconstituição de um caso. |
| **Exigida em** | Todos |

---

### ADM-18 · Segregação de funções

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Garantir que quem administra a solução não seja quem audita seu comportamento. |
| **Quando aplicar** | Passo 7, em contextos regulados. |
| **Como aplicar** | 1. Identificar os papéis de administração e de auditoria.<br>2. Verificar acúmulo de funções na estrutura atual.<br>3. Registrar quando a segregação não for possível, com a mitigação adotada. |
| **Insumo e saída** | Papéis nomeados → Segregação declarada ou mitigação registrada |
| **Erro comum** | Declarar segregação no papel quando a mesma pessoa acumula as duas funções na prática. |
| **Encerramento** | Segregação verificada na estrutura real, não na declarada. |
| **Exigida em** | N3 |

---

### IA-06 · Auditoria de desempenho por subgrupo

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se a solução trata grupos distintos de forma equivalente. |
| **Quando aplicar** | Passo 7, quando a decisão afetar pessoas. |
| **Como aplicar** | 1. Definir os subgrupos relevantes antes de medir.<br>2. Comparar o desempenho entre eles, e não apenas o agregado.<br>3. Registrar a diferença aceitável e sua justificativa. |
| **Insumo e saída** | Casos de teste e classificação de subgrupos → Desempenho por subgrupo, com limiar declarado |
| **Erro comum** | Avaliar apenas o desempenho agregado, que oculta desempenho desigual entre subgrupos. |
| **Encerramento** | Subgrupos definidos e desempenho comparado, com limiar declarado. |
| **Exigida em** | N3 |

---

## 4. Condição de aceite
Este artefato está pronto quando todo instrumento selecionado para a fase tem os sete campos preenchidos; quando o campo de encerramento permite verificar, sem consulta a terceiros, se a aplicação terminou; e quando o erro comum descreve falha de aplicação, e não limitação do instrumento.

## 5. Referências
* **Artefatos relacionados:** EMCIA-FER-01, EMCIA-MET-01, EMCIA-GLO-01.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
| :---: | :---: | :--- | :--- | :---: |
| **0.1** | 14/09/2026 | Celso do Vale | Versão inicial: fichas dos 11 instrumentos da fase | — |