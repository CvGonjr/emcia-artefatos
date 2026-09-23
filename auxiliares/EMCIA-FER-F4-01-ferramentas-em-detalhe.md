# Ferramentas em detalhe
### Fase F4 — Piloto e calibragem

| Metadado | Valor | Metadado | Valor |
| :--- | :--- | :--- | :--- |
| **Código** | EMCIA-FER-F4-01 | **Versão** | 0.1 |
| **Data** | 14/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Fase F4 | **Passos** | 8, 9 e 10 |

---

## 1. Objetivo
Detalhar cada instrumento selecionado para esta fase, de modo que um engenheiro que não participou da seleção saiba quando aplicá-lo, como aplicá-lo e quando parar. Este documento é auxiliar do quadro de ferramentas EMCIA-FER-01, que registra a seleção; aqui está a aplicação.

## 2. Escopo e aplicação
Aplica-se aos 12 instrumentos selecionados para a fase F4 — Piloto e calibragem. A sigla é a mesma do quadro e permanece estável ainda que o instrumento seja reposicionado.

Fase em que o método se torna verificável. Os instrumentos existem para impedir que o critério de sucesso seja fixado depois de conhecido o resultado.

## 3. Fichas
O campo de erro comum registra a falha observada na aplicação do instrumento, e não a sua limitação teórica. É o campo de maior valor para quem aplica pela primeira vez.

---

### IA-07 · Conjunto de casos de teste com saída esperada ★

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer, antes do piloto, o que a solução precisa acertar. |
| **Quando aplicar** | Passo 8, antes de qualquer execução. |
| **Como aplicar** | 1. Cobrir quatro tipos: regra geral, exceção, caso fora de escopo que deve ser recusado e tentativa de violar limite que deve ser bloqueada.<br>2. Incluir casos raros de alta consequência, invisíveis ao histórico.<br>3. Submeter o conjunto à revisão de quem executa o processo. |
| **Insumo e saída** | Regras verificadas e camada de contexto → Casos com saída esperada, revisados |
| **Erro comum** | Derivar os casos apenas do histórico, o que omite justamente a exceção que decide o resultado. |
| **Encerramento** | Conjunto revisado por quem executa o processo, com saída esperada por caso. |
| **Exigida em** | Todos |

---

### IA-08 · Modo sombra e liberação gradual

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Limitar o alcance de uma falha durante o período em que ela é mais provável. |
| **Quando aplicar** | Passo 8, na entrada em operação. |
| **Como aplicar** | 1. Executar em paralelo sem efeito, comparando com a decisão humana.<br>2. Só avançar para assistido após o critério de acerto declarado.<br>3. Definir a fatia de casos liberada em cada etapa. |
| **Insumo e saída** | Solução construída e casos de teste → Sequência de liberação declarada |
| **Erro comum** | Passar direto para assistido por pressão de prazo, perdendo a única etapa sem risco. |
| **Encerramento** | Sequência declarada, com critério de avanço entre etapas. |
| **Exigida em** | N2 e N3 |

---

### ADM-19 · Plano de reversão

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer como voltar ao estado anterior, e em quanto tempo. |
| **Quando aplicar** | Passo 8, antes do início do piloto. |
| **Como aplicar** | 1. Declarar quem pode acionar a reversão.<br>2. Estimar o tempo até o processo voltar a operar sem a solução.<br>3. Verificar se o conhecimento do processo manual ainda existe na equipe. |
| **Insumo e saída** | Estado atual e estado futuro → Plano com acionador e tempo declarados |
| **Erro comum** | Presumir que a equipe retoma o processo manual, quando a rotina anterior já se perdeu. |
| **Encerramento** | Plano escrito, com acionador nomeado e tempo estimado. |
| **Exigida em** | Todos |

---

### IA-09 · Métricas de precisão, revocação e F1

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se o acerto é real ou efeito de base desbalanceada. |
| **Quando aplicar** | Passo 8, na apuração do piloto. |
| **Como aplicar** | 1. Verificar a distribuição das classes antes de ler o acerto.<br>2. Declarar qual erro é mais caro: o falso positivo ou o falso negativo.<br>3. Escolher a métrica conforme essa resposta. |
| **Insumo e saída** | Resultado dos casos de teste → Métricas apuradas, com a escolha justificada |
| **Erro comum** | Reportar acerto global em base desbalanceada, onde ele pode ser alto sem significado. |
| **Encerramento** | Métrica escolhida e justificada pela assimetria de custo do erro. |
| **Exigida em** | N2 e N3 |

---

### ADM-20 · Comparação contra a linha de base

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer se o processo melhorou em relação ao que era. |
| **Quando aplicar** | Passo 9, sobre a linha de base do passo 3. |
| **Como aplicar** | 1. Usar os mesmos indicadores e o mesmo método de apuração da linha de base.<br>2. Declarar fatores externos que possam ter influenciado o período.<br>3. Separar resultado do processo de uso da ferramenta. |
| **Insumo e saída** | Linha de base datada e medições do piloto → Comparativo, com fatores externos declarados |
| **Erro comum** | Medir adoção e apresentá-la como valor gerado. |
| **Encerramento** | Ao menos um indicador de resultado comparado contra a linha de base. |
| **Exigida em** | Todos |

---

### ADM-21 · Retorno financeiro com VPL e TIR

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se o investimento se pagou, nos termos em que a organização avalia investimento. |
| **Quando aplicar** | Passo 9, após a apuração dos indicadores. |
| **Como aplicar** | 1. Partir do valor realizado no período medido.<br>2. Separar valor realizado de valor projetado, em notações distintas.<br>3. Declarar a faixa de incerteza da projeção. |
| **Insumo e saída** | Resultado do piloto e custo de operação → Retorno apurado e projetado, separadamente |
| **Erro comum** | Projetar o resultado do piloto para o ano inteiro sem declarar a faixa de incerteza. |
| **Encerramento** | Valor realizado e projetado apresentados em notações distintas. |
| **Exigida em** | N3 |

---

### BD-12 · Painel de acompanhamento

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Permitir que o patrocinador acompanhe o resultado sem precisar solicitá-lo. |
| **Quando aplicar** | Passo 9, após a definição dos indicadores. |
| **Como aplicar** | 1. Limitar aos indicadores que sustentam decisão.<br>2. Declarar a origem e a periodicidade de cada número.<br>3. Verificar se o painel se mantém sem intervenção manual. |
| **Insumo e saída** | Indicadores definidos → Painel com origem e periodicidade declaradas |
| **Erro comum** | Incluir indicador que ninguém usa para decidir, o que dilui a atenção sobre os que importam. |
| **Encerramento** | Cada indicador do painel ligado a uma decisão específica. |
| **Exigida em** | N2 e N3 |

---

### IA-10 · Detecção de desvio de dado e de conceito

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Identificar quando o mundo mudou desde a última calibragem da solução. |
| **Quando aplicar** | Passo 10, na entrada em operação. |
| **Como aplicar** | 1. Definir o limiar antes do piloto, e não após conhecer a variação normal.<br>2. Distinguir mudança na distribuição do dado de mudança na relação que a solução aprendeu.<br>3. Declarar quem recebe o alerta. |
| **Insumo e saída** | Dados do período de piloto → Limiar e destinatário do alerta declarados |
| **Erro comum** | Ajustar o limiar depois de observar o comportamento, o que o torna incapaz de alertar. |
| **Encerramento** | Limiar declarado antes do piloto, com destinatário nomeado. |
| **Exigida em** | N2 e N3 |

---

### BD-13 · Observabilidade de dados

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se frescor, volume e distribuição das fontes continuam dentro do esperado. |
| **Quando aplicar** | Passo 10, sobre as fontes críticas. |
| **Como aplicar** | 1. Definir o esperado por fonte a partir do período de piloto.<br>2. Alertar sobre ausência de dado, e não apenas sobre dado anômalo.<br>3. Ligar o alerta ao responsável pela fonte. |
| **Insumo e saída** | Fontes críticas e comportamento no piloto → Monitoramento definido por fonte |
| **Erro comum** | Monitorar apenas anomalia de valor, deixando passar a interrupção silenciosa da carga. |
| **Encerramento** | Cada fonte crítica com esperado declarado e responsável ligado. |
| **Exigida em** | N3 |

---

### ADM-22 · Roteiro de resposta a incidente

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer o que fazer quando a solução erra, antes que ela erre. |
| **Quando aplicar** | Passo 10, antes da entrada em operação. |
| **Como aplicar** | 1. Classificar os incidentes por severidade.<br>2. Declarar o destinatário nominal de cada severidade.<br>3. Definir o prazo de resposta por classe. |
| **Insumo e saída** | Riscos identificados e papéis nomeados → Roteiro com severidades e destinatários |
| **Erro comum** | Encaminhar para uma área em vez de uma pessoa, o que equivale a não encaminhar. |
| **Encerramento** | Cada severidade com destinatário nominal e prazo declarado. |
| **Exigida em** | N2 e N3 |

---

### ADM-23 · Análise pós-incidente focada em processo

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Estabelecer por que o erro foi possível, e não quem o cometeu. |
| **Quando aplicar** | Passo 10, após cada incidente relevante. |
| **Como aplicar** | 1. Reconstituir a sequência a partir da trilha de auditoria.<br>2. Perguntar o que permitiu o erro, e não quem o cometeu.<br>3. Registrar a correção e o prazo, com responsável. |
| **Insumo e saída** | Trilha de auditoria e relato dos envolvidos → Registro de causa e correção, com responsável |
| **Erro comum** | Conduzir a análise com foco em responsabilidade individual, o que faz o próximo incidente não ser relatado. |
| **Encerramento** | Causa registrada no processo, com correção e prazo atribuídos. |
| **Exigida em** | Todos |

---

### ADM-24 · Reavaliação de maturidade em 12 a 18 meses

| Campo | Especificação |
| :--- | :--- |
| **Para que serve** | Verificar se a organização evoluiu de nível, e se o método aplicável mudou. |
| **Quando aplicar** | Passo 10, com data marcada em calendário. |
| **Como aplicar** | 1. Reaplicar o mesmo instrumento de maturidade do passo 1.<br>2. Comparar com a posição inicial registrada.<br>3. Reavaliar se o nível do próximo engajamento mudou. |
| **Insumo e saída** | Posição de maturidade do passo 1 → Nova posição, comparada à inicial |
| **Erro comum** | Reavaliar com instrumento diferente do usado na primeira medição, o que impede a comparação. |
| **Encerramento** | Reavaliação agendada com data e responsável nomeados. |
| **Exigida em** | N2 e N3 |

---

## 4. Condição de aceite
Este artefato está pronto quando todo instrumento selecionado para a fase tem os sete campos preenchidos; quando o campo de encerramento permite verificar, sem consulta a terceiros, se a aplicação terminou; e quando o erro comum descreve falha de aplicação, e não limitação do instrumento.

## 5. Referências
* **Artefatos relacionados:** EMCIA-FER-01, EMCIA-MET-01, EMCIA-GLO-01.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
| :---: | :---: | :--- | :--- | :---: |
| **0.1** | 14/09/2026 | Celso do Vale | Versão inicial: fichas dos 12 instrumentos da fase | — |