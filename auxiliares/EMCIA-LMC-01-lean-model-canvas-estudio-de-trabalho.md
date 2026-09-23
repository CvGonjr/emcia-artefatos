# Lean Model Canvas do Estúdio de Trabalho

*Hipóteses de valor e recorte da PoC do Code Plugin*

| | | | |
|---|---|---|---|
| **Código** | EMCIA-LMC-01 | **Versão** | 0.1 |
| **Data** | 17/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 1 — Planejamento | **Passo** | Ação 1.9 |

## 1. Objetivo

Resumir em um único quadro as hipóteses de problema, usuário, proposta de valor, solução, métricas e estrutura de custo do Estúdio de Trabalho. O canvas orienta a implementação da PoC; não define um modelo comercial validado.

## 2. Escopo

O canvas trata do **Estúdio de Trabalho em formato Code Plugin**, utilizado pelo engenheiro de campo para executar o método EMCIA. Não trata da solução que será especificada para o cliente.

## 3. Lean Model Canvas

| Bloco | Conteúdo |
|---|---|
| Problemas | 1) Método documentado pode ser aplicado de forma inconsistente. 2) Procedência e fronteira podem virar apenas instrução ao modelo. 3) Cobertura parcial F0–P5 impede demonstrar o percurso completo. |
| Usuário / segmento | Engenheiro de campo da EMCIA ou terceiro habilitado a aplicar o método. Beneficiário indireto: organização cliente, que recebe entregáveis verificáveis. |
| Proposta única de valor | **Executar o método inteiro, F0–P10, com travas verificáveis sem transformar julgamento humano em prompt.** |
| Solução | Code Plugin no Claude Code com `eiac-nucleo`, `eiac-campo`, playbook por caso, D/I/V, 18 HB, 4 AG, cinco inegociáveis, geração de entregáveis e trilha de eventos. |
| Alternativas existentes | Documentos e checklists manuais; chat genérico; agentes sem camada de controle do método; scripts isolados sem playbook do caso. |
| Canais / acesso | Marketplace/plugin do Claude Code; repositório próprio de cada caso; documentos controlados da EMCIA. |
| Métricas-chave | 13 etapas carregáveis; 5 fases fecháveis; 18 HB com código; 4 AG com código; 5 inegociáveis operantes; 20 testes acumulados; 6 autorizações internas de emissão; 0% de I incorporada como V sem confirmação. |
| Vantagem difícil de copiar | Integração entre método, catálogo de fronteira, instrumentos de campo, playbook versionado e evidência de recusa. O diferencial não é o modelo de linguagem. |
| Estrutura de custos | Redação dos instrumentos; implementação e testes; curadoria da base de referência; manutenção de plugins; consumo de modelos/serviços de mercado. |
| Valor capturado / receita | Nesta PoC não há modelo de receita validado. O valor esperado é reutilização do método, redução de preparação manual e capacidade de aplicação por terceiros com maior consistência. |

## 4. Hipóteses a verificar

- O engenheiro consegue percorrer F0–P10 sem contornar as travas do método.
- O ganho do Code Plugin está em padronizar preparação, registro e verificação, não em automatizar P3b, P7 ou decisões finais.
- A separação `eiac-nucleo` / `eiac-campo` permite trocar método, modelo ou superfície sem perder o contrato do caso.
- A cobertura completa é demonstrável sem implantar a solução do cliente em produção.

## 5. Condição de aceite

O canvas está pronto quando identifica um usuário primário, três problemas concretos, uma proposta única de valor, a solução mínima da PoC, métricas de cobertura e qualidade, custos principais e uma declaração explícita de que receita não é objeto de validação desta etapa.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 17/09/2026 | Celso do Vale | Versão inicial do Lean Model Canvas do Estúdio de Trabalho. | — |
