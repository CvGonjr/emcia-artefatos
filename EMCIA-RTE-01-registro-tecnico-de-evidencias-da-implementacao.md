# Registro Técnico de Evidências da Implementação

*Rastreabilidade entre baseline, requisito, teste, defeito, correção e reteste da Sprint 2*

> Atualizado em: 18/09/2026 — registro efetivo dos pacotes 2.5.0 a 2.5.6. Ação 2.5 (Camada de Contexto e Dados) encerrada CONFORME.

| | | | |
|---|---|---|---|
| **Código** | EMCIA-RTE-01 | **Versão** | 0.8 |
| **Data** | 18/09/2026 | **Estado** | Em revisão |
| **Responsável** | Celso do Vale | **Aprovação** | pendente |
| **Fase** | Sprint 2 | **Passo** | Ações 2.5–2.6 |

## 1. Objetivo

Definir o registro técnico consolidado das evidências produzidas durante a implementação de referência da Sprint 2 do Estúdio de Trabalho. O EMCIA-RTE-01 liga o estado inicial controlado da implementação aos requisitos executados em cada pacote e registra, de forma rastreável, o teste aplicado, o resultado obtido, o defeito eventualmente encontrado, a correção realizada, o reteste, o commit e o estado final do requisito.

O RTE-01 não substitui os logs brutos, a suíte de testes nem os eventos produzidos pelo Estúdio. Sua função é indexar essas evidências e preservar a cadeia **baseline → requisito → teste → resultado → defeito → correção → reteste → evidência → commit → estado final**, de modo que a implementação possa ser auditada sem reconstrução retrospectiva do que ocorreu.

## 2. Escopo e aplicação

Aplica-se à Sprint 2, composta pelas ações **2.5 — Camada de Contexto e Dados** e **2.6 — Camada de Agentes e Protocolos**, incluindo o baseline S2-BL realizado antes dos pacotes de implementação. O instrumento acompanha tanto funcionalidades novas quanto requisitos já presentes no repositório: quando um requisito já estiver implementado, o RTE-01 registra sua verificação e os testes correspondentes sem exigir reimplementação artificial.

O registro trata da implementação do Estúdio de Trabalho e não da validação operacional da solução empresarial do cliente. Resultados como implantação produtiva, ROI observado, ganho operacional real ou desempenho em produção não podem ser inferidos a partir do RTE-01. Esses limites permanecem os mesmos definidos na arquitetura e no plano de verificação do método.

| Instrumento / fonte | Função na evidência |
|---|---|
| **EMCIA-TST-01** | Define o plano, os casos e os critérios de teste da implementação. |
| **EMCIA-RTE-01** | Registra o que foi efetivamente executado e liga requisito, teste, defeito, correção e reteste. |
| **`.projectdocs/evidencias/sprint2/`** | Preserva a evidência técnica bruta por pacote. |
| **Git** | Preserva o estado executável da implementação por commit. |
| **`eventos.jsonl`** | Preserva recusas, autorizações e demais eventos auditáveis produzidos pelo Estúdio. |
| **EMCIA-VER-01** | Verifica o método; não substitui os testes de implementação do TST-01. |

## 3. Conteúdo

### 3.1 Cadeia de rastreabilidade

Cada requisito acompanhado pelo RTE-01 deve poder ser lido no seguinte percurso:

```text
S2-BL / estado anterior
        ↓
requisito documental
        ↓
teste ou controle
        ↓
resultado inicial
        ↓
defeito, se houver
        ↓
correção
        ↓
reteste
        ↓
evidência técnica
        ↓
commit da implementação
        ↓
estado final
```

Um resultado `PASS` comprova somente o comportamento coberto pelo teste executado. A aprovação de toda a suíte não deve ser interpretada como prova de ausência de defeitos fora de sua cobertura. O S2-BL demonstrou essa distinção: a suíte inicial apresentou 26 resultados `PASS`, enquanto controles adicionais identificaram lacunas fora da cobertura existente.

### 3.2 Hierarquia das evidências

Quando houver diferença entre resumo e evidência bruta, prevalece a evidência mais próxima da execução.

| Prioridade | Evidência | Papel |
|---:|---|---|
| 1 | Saída bruta do comando/teste | Mostra o comportamento realmente executado. |
| 2 | Evento auditável do Estúdio | Demonstra recusa, autorização ou transição registrada pelo sistema. |
| 3 | Diff e commit Git | Demonstra a mudança executável que produziu o comportamento. |
| 4 | `resultado.md` do pacote | Consolida o pacote e referencia as evidências brutas. |
| 5 | EMCIA-RTE-01 | Consolida a rastreabilidade entre os pacotes e o baseline. |
| 6 | Relatório do PFC | Usa apenas a síntese necessária para demonstrar o percurso de implementação. |

O RTE-01 não deve reproduzir integralmente stdout/stderr quando a evidência estiver preservada no diretório técnico. Deve apontar para a evidência e registrar apenas o resultado necessário à rastreabilidade.

### 3.3 Repositório de evidências

As evidências técnicas da Sprint 2 devem ser organizadas por pacote:

```text
.projectdocs/
└── evidencias/
    └── sprint2/
        ├── S2-BL/
        ├── 2.5.0/
        ├── 2.5.1/
        ├── 2.5.2/
        ├── 2.5.3/
        ├── 2.5.4/
        ├── 2.5.5/
        ├── 2.5.6/
        ├── 2.6.0/
        ├── 2.6.1/
        ├── 2.6.2/
        ├── 2.6.3/
        ├── 2.6.4/
        ├── 2.6.5/
        └── 2.6.6/
```

Cada diretório de pacote deve preservar, quando aplicável:

```text
resultado.md
teste-regressao-inicial.txt
teste-<id>.txt
teste-regressao-final.txt
eventos.jsonl
diff.patch
git-show.txt
```

`resultado.md` é a ficha consolidada do pacote. Os arquivos `teste-<id>.txt` preservam a execução de cada teste ou controle. `eventos.jsonl` deve conter somente os eventos relevantes ao pacote ou uma cópia claramente delimitada da trilha usada como evidência. `diff.patch` registra a mudança executável e `git-show.txt` registra o commit de implementação depois de criado.

A evidência não deve ser forçada para dentro do mesmo commit que referencia. O commit de implementação pode ser criado primeiro e, em seguida, suas evidências podem ser arquivadas em commit documental separado ou consolidadas ao fechamento da ação. Não se deve reescrever o histórico apenas para inserir em um arquivo o hash do próprio commit que o contém.

### 3.4 Registro mínimo de teste

Cada evidência de teste deve registrar, quando aplicável:

```text
PACOTE:
TESTE:
REQUISITO:
DATA/HORA:
COMMIT TESTADO:
COMANDO EXECUTADO:
EXIT CODE:

RESULTADO ESPERADO:

RESULTADO OBTIDO:

STDOUT/STDERR:

RESULTADO FINAL:
PASS | FAIL | SKIP | BLOQUEADO
```

Um teste negativo é considerado `PASS` quando a violação planejada é recusada pelo motivo esperado. Um controle positivo é considerado `PASS` quando o mesmo mecanismo permite o caminho válido correspondente. Uma trava que rejeita todas as entradas não satisfaz o critério de implementação apenas por fazer os testes negativos passarem.

### 3.5 Estado inicial dos requisitos

Antes da implementação ou revisão de cada pacote, o requisito deve receber uma das classificações abaixo:

| Estado inicial | Significado |
|---|---|
| **AUSENTE** | O requisito não possui implementação identificável. |
| **PARCIAL** | Parte do requisito existe, mas faltam comportamento, validação, cobertura ou caminho válido. |
| **JÁ IMPLEMENTADO E CONFORME** | O requisito já existe e corresponde ao contrato documental; requer verificação, não reescrita artificial. |
| **IMPLEMENTADO MAS DIVERGENTE** | Existe comportamento implementado, mas ele contradiz ou não representa adequadamente o contrato atual. |

### 3.6 Estado final dos pacotes e requisitos

| Estado final | Significado |
|---|---|
| **CONFORME** | Requisito implementado ou validado, com teste e evidência suficientes para o escopo. |
| **PARCIAL** | Parte do requisito foi atendida, mas permanece lacuna explicitamente registrada. |
| **BLOQUEADO** | A execução depende de decisão, artefato ou condição não disponível. |

`PASS`, `FAIL` e `SKIP` descrevem resultados de testes; `CONFORME`, `PARCIAL` e `BLOQUEADO` descrevem o estado do requisito ou pacote. As duas classificações não devem ser confundidas.

### 3.7 Modelo de registro por pacote

Cada pacote deve produzir uma ficha consolidada com a seguinte estrutura:

| Campo | Registro esperado |
|---|---|
| Pacote | Identificador, por exemplo `2.5.0`. |
| Documentos consultados | Arquivos e versões usados para definir o requisito. |
| Requisitos | IDs documentais e/ou IDs do baseline tratados. |
| Estado inicial | AUSENTE, PARCIAL, JÁ IMPLEMENTADO E CONFORME ou IMPLEMENTADO MAS DIVERGENTE. |
| Arquivos inspecionados | Arquivos de código, configuração, templates e testes relevantes. |
| Alterações | Mudanças efetivamente realizadas; vazio quando o requisito já estava conforme. |
| Testes planejados | Casos previstos antes da execução. |
| Testes executados | Casos realmente executados e seus IDs. |
| Controles positivos | Caminhos válidos usados para provar que a trava não rejeita tudo. |
| Resultado | Síntese de PASS/FAIL/SKIP/BLOQUEADO. |
| Defeitos | Desvios identificados durante a execução. |
| Correções | Mudanças realizadas para tratar os defeitos. |
| Reteste | Resultado após a correção. |
| Eventos | Eventos auditáveis usados como evidência. |
| Commit | Hash do commit de implementação testado. |
| Evidência | Caminho para o diretório bruto do pacote. |
| Estado final | CONFORME, PARCIAL ou BLOQUEADO. |

### 3.8 Modelo de rastreabilidade de requisito

O RTE-01 consolida os pacotes por requisito, sem substituir `resultado.md`.

| Campo | Descrição |
|---|---|
| ID do requisito | Código do baseline, TST, CTX, HB/AG, portão ou outro requisito controlado. |
| Pacote | Pacote responsável pela implementação/verificação. |
| Baseline | Estado observado antes do pacote. |
| Teste | ID do teste ou controle executado. |
| Resultado inicial | PASS, FAIL, SKIP ou BLOQUEADO. |
| Defeito | ID do defeito quando o teste revelar desvio. |
| Correção | Resumo da mudança aplicada. |
| Reteste | Resultado obtido depois da correção. |
| Evidência | Caminho do log/evento/diff correspondente. |
| Commit | Commit executável associado ao estado final. |
| Estado final | CONFORME, PARCIAL ou BLOQUEADO. |

### 3.9 Baseline técnico S2-BL

O baseline oficial da Sprint 2 foi registrado em 18/09/2026 antes do início dos pacotes de implementação.

| Campo | Valor |
|---|---|
| Repositório | `/home/netiv-ai/Projetos/AI/PLUGINS/emcia-marketplace` |
| Branch | `master` |
| HEAD | `9a54017411c20cf54ab3a28fa488678c945a34b1` |
| `eiac-nucleo` | 0.2.5 |
| `eiac-campo` | 0.3.2 |
| Playbook | 0.3.0 |
| Working tree | limpa antes e depois do baseline |
| Testes | 26 |
| PASS / FAIL / SKIP | 26 / 0 / 0 |

#### 3.9.1 Indicadores iniciais

| Indicador | Baseline | Alvo da Sprint 2 |
|---|---:|---:|
| Etapas operacionais | 8 / 13 | 13 / 13 |
| HB oficiais referenciadas | 9 / 18 | 18 / 18 |
| HB com código estável no próprio arquivo | 0 / 18 | 18 / 18 |
| AG oficialmente mapeados | 0 / 4 | 4 / 4 |
| Portões estritamente conformes | 2 / 6 | 6 / 6 |
| Inegociáveis efetivamente verificáveis | 0 / 5 | 5 / 5 |
| Validações CTX | 0 / 11 | 11 / 11 |
| Testes existentes | 26 | crescimento orientado à cobertura; sem meta numérica artificial |

O baseline identificou dois arquivos de agente funcionalmente existentes, mas nenhum estava formalmente mapeado aos códigos AG-01–AG-04. Da mesma forma, treze arquivos de skill existiam, porém somente nove códigos HB eram referenciados no playbook e nenhum estava declarado de forma estável no próprio arquivo.

### 3.10 Pacotes da Sprint 2

| Pacote | Camada | Escopo | Estado inicial do pacote |
|---|---|---|---|
| **S2-BL** | Transversal | Registrar o estado inicial sem alteração de código. | Concluído |
| **2.5.0** | Contexto e Dados | Normalizar o contrato documental D/I/V. | IMPLEMENTADO MAS DIVERGENTE |
| **2.5.1** | Contexto e Dados | Migrar Termo, Entidade, Regra e Fonte para CTX-01. | IMPLEMENTADO MAS DIVERGENTE |
| **2.5.2** | Contexto e Dados | Curadoria, autoria, versionamento I→V e proteção de `contexto/`. | Concluído |
| **2.5.3** | Contexto e Dados | Classificação de confronto e `referencia_p3d`. | Concluído |
| **2.5.4** | Contexto e Dados | Implementar CTX-V01–V11 e referências. | Concluído |
| **2.5.5** | Contexto e Dados | Integrar P2/P3 → CTX → P4/P5 e eventos. | Concluído |
| **2.5.6** | Contexto e Dados | Verificação consolidada da camada. | Concluído |
| **2.6.0** | Agentes e Protocolos | Congelar contrato executável F0–P10. | Concluído |
| **2.6.1** | Agentes e Protocolos | Fortalecer núcleo, máquina de estados, guardas e eventos. | Concluído |
| **2.6.2** | Agentes e Protocolos | Implementar P6/P7 e decisão humana de autonomia. | Concluído |
| **2.6.3** | Agentes e Protocolos | Implementar P8/P9/P10 e recorrência. | Concluído |
| **2.6.4** | Agentes e Protocolos | Completar 18 HB, 4 AG e critérios de verificação. | Concluído |
| **2.6.5** | Agentes e Protocolos | Ativar seis autorizações, inegociáveis e geração dos entregáveis. | Concluído |
| **2.6.6** | Agentes e Protocolos | Executar caso de controle F0–P10 e suíte end-to-end. | Concluído |

#### 3.10.1 Pacote 2.5.0 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.0` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Requisitos** | `D-01`, `2.5-BL01`, `2.5-BL02` |
| **Baseline** | `IMPLEMENTADO MAS DIVERGENTE` no HEAD `9a54017411c20cf54ab3a28fa488678c945a34b1` |
| **Resultado inicial** | O playbook mantinha procedência multidimensional e taxonomias concorrentes a D/I/V. |
| **Implementação** | Normalização da procedência para `D`, `I` e `V`; separação de `apuracao` e `tipo_fonte`; I passou a exigir premissa; V passou a exigir evidência; valores externos ao contrato passaram a ser recusados. O diff também atualizou consumidores ativos, modelos mínimos, documentação diretamente afetada, versões e cobertura de testes. |
| **Testes** | `2.5.0-T01` a `2.5.0-T07`; `2.5.0-T08` como regressão dos 26 cenários anteriores. Os testes constam no commit, mas o stdout/stderr bruto da execução original não foi preservado. |
| **Defeito** | `D-01` — taxonomia documental concorrente: `campo`, `antitese`, `conversa`, `livre`, `externo` e `apuracao` apareciam misturados ou concorrendo com declarado/inferido/verificado. |
| **Correção** | Contrato canônico `D = Declarada`, `I = Inferida`, `V = Verificada`; dimensões ainda válidas representadas separadamente. |
| **Reteste** | Evidência reconstruída em 18/09/2026 15:41:28 -0300 no commit final: 33 verificações aprovadas, 0 falhas, exit code 0. Não substitui o log original, que não foi preservado. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.0/resultado.md` |
| **Commit** | `acf35f963bff718cfaa25981c4c84753f661c367` — `refactor(context): normalize documentary provenance to DIV` |
| **Estado final** | **CONFORME** |

**Proveniência da evidência.** O commit, seu conteúdo e os testes versionados
são evidências contemporâneas da implementação. `resultado.md`,
`git-show.txt`, `diff.patch` e `teste-regressao-final.txt` foram reconstruídos
posteriormente a partir do Git preservado e de uma reexecução no commit final.
Não foram encontrados logs brutos nem eventos preservados da execução original.

#### 3.10.2 Pacote 2.5.1 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.1` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Objetivo** | Materializar Termo, Entidade, Regra e Fonte conforme o EMCIA-CTX-01 v0.4. |
| **Requisitos / baseline** | `D-02`, `2.5-BL03`, `2.5-BL04`, `2.5-BL05`, `2.5-BL06` |
| **Estado inicial** | `IMPLEMENTADO MAS DIVERGENTE` no HEAD `5421c78edaeb074c3d14e61e6686be42431a2c56`: os quatro modelos existiam, mas ainda representavam o schema anterior. |
| **Resultado inicial** | Regressão anterior com 33/33 verificações aprovadas; Termo e Entidade usavam `autor/fonte`; Regra usava `R-*`, `estatuto` e divergência embutida, sem todos os metadados do CTX-01 v0.4; Fonte não possuía `registrado_por` nem contrato estrutural executável. Não foram localizadas instâncias reais para migração. |
| **Implementação** | Os quatro modelos foram alinhados ao CTX-01 v0.4; Regra passou a `RN-*`, preservou os sete campos centrais e recebeu gatilho, autoria, registro, origem, confronto e histórico estruturais; Fonte recebeu contrato mínimo verificável; todos os objetos adotaram D/I/V e metadados de rastreabilidade. O `eiac-campo` passou a declarar `registro/contexto.schema.json`, enquanto o `eiac-nucleo` recebeu um validador genérico orientado pelo schema, sem regras específicas do EMCIA. |
| **Testes** | `2.5.1-T01` a `2.5.1-T11`: quatro controles positivos, quatro negativas por campo obrigatório, D/I/V nos quatro objetos, recusa de oito taxonomias obsoletas e presença dos sete campos centrais da Regra; regressão acumulada `2.5.1-T12`. |
| **Defeitos** | Nenhum defeito novo demonstrável. O pacote tratou os desvios já registrados em `D-02` e `2.5-BL03` a `2.5-BL06`. |
| **Correções** | Migração estrutural dos templates, schema declarativo, validador genérico, documentação compatível, versões `eiac-nucleo` 0.2.7 e `eiac-campo` 0.3.4 e cobertura estrutural positiva/negativa. |
| **Reteste** | 44/44 verificações aprovadas, 0 falhas e 0 skips: 33 da suíte anterior e 11 testes estruturais novos. |
| **Eventos** | Não aplicáveis: o pacote valida estrutura em modo somente leitura; não executa curadoria nem transição de estado. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.1/resultado.md` |
| **Commit** | `92179256f078880f92fbfe5d395ee4a61dccfbf7` — `feat(context): materialize CTX core objects` |
| **Estado final** | **CONFORME** |

Os comportamentos de curadoria, restrição de autoria, versionamento I→V,
semântica obrigatória de P3d, CTX-V01–V11 e integração P2/P3 → P4/P5 não
foram antecipados; permanecem atribuídos aos pacotes 2.5.2 a 2.5.5.

#### 3.10.3 Pacote 2.5.2 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.2` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Objetivo** | Implementar curadoria, autoria (`autoria_conteudo` × `registrado_por`), premissa/evidência, histórico e transição I→V sem sobrescrita. |
| **Requisitos / baseline** | `D-03`, `2.5-BL07`, `2.5-BL08`, `2.5-BL09`, `2.5-BL10`, `2.5-BL11`, `2.5-BL12`, `2.5-BL13` |
| **Estado inicial** | `HEAD_INICIAL_2.5.2 = 61af78ce2886757be2c110ddca8a6a714a272421`, working tree limpa. Evidência/evidência obrigatória e premissa obrigatória já `JÁ IMPLEMENTADO E CONFORME` desde o 2.5.1 (`conditional_nonempty` do schema); autoria dupla, histórico/versionamento, rascunho×contexto e agente-como-autor estavam `PARCIAL` ou `AUSENTE` — os campos existiam no schema, mas nenhum código verificava conteúdo humano, comparava versão anterior ou protegia `contexto/` contra escrita direta. |
| **Implementação** | Novo `eiac-nucleo/scripts/curar.py`: único caminho de escrita em `contexto/`, reaproveitando `estrutura.validar()` para a checagem estrutural e acrescentando checagem de autoria e de versionamento. Nova regra G2b em `guarda.py` bloqueia escrita direta em `contexto/`, espelhando a proteção já existente para `caso/`. Convenção lexical de autor-agente centralizada em `estado.autor_e_agente()` e reutilizada por `selar.py`, `avancar.py`, `validar.py` e `curar.py`. |
| **Testes** | `2.5.2-T01` a `2.5.2-T16` (mínimo obrigatório da instrução do pacote) + um teste adicional do achado específico do baseline (`--registrado-por AG-01`) + `2.5.2-T17` como regressão acumulada. |
| **Defeitos** | (1) Reprodução confirmada do achado do baseline: `validar.py --autor` nunca era verificado contra a convenção de nome de agente. (2) Defeito adicional descoberto durante a correção: a convenção lexical `startswith(("ag0","agente","sistema"))`, já usada desde pacotes anteriores, não cobria `"AG-01"` com hífen, porque `"ag-01"` não começa por `"ag0"`. Os testes anteriores só exercitavam `AG05` (sem hífen), por isso o ponto cego nunca havia aparecido. |
| **Correções** | `autor_e_agente()` normaliza hífen/espaço/underscore antes de comparar; `validar.py --autor` passa a ser verificado; `curar.py` verifica `--registrado-por` e os campos `autoria_conteudo`/`declarado_por`/`registrado_por` do YAML candidato; `selar.py`/`avancar.py`/`validar.py` passaram a usar a função centralizada em vez de três cópias da mesma regra. |
| **Reteste** | 61/61 verificações aprovadas, 0 falhas, 0 skips: 33 de `negativos.sh` + 11 de `contexto.py` (sem regressão) + 17 novas de `curadoria.py`. |
| **Eventos** | `ObjetoContextoCurado` (criação e cada nova versão curada) e `CuradoriaRecusada` (qualquer recusa), emitidos por `curar.py`; `TentativaNegada`, emitido por `guarda.py` G2b, para bypass de escrita direta em `contexto/`. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.2/resultado.md` |
| **Commit** | `c9df31f` — `feat(context): enforce curation and immutable provenance history` |
| **Estado final** | **CONFORME** |

Este pacote não implementou `classificacao_confronto`/`referencia_p3d`
(2.5.3), CTX-V01–V11 como bateria formal completa ou validação referencial
entre objetos (2.5.4), integração executável P2/P3 → CTX → P4/P5 (2.5.5),
nem qualquer item da ação 2.6.

#### 3.10.4 Pacote 2.5.3 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.3` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Objetivo** | Integrar a Regra CTX ao confronto P3d por classificação e referência rastreável, sem duplicar a evidência detalhada. |
| **Requisitos / baseline** | `D-04`, `2.5-BL14`, `2.5-BL15` |
| **Estado inicial** | `HEAD_INICIAL_2.5.3 = c67ea6219c6c78232850e66641ec05349cd83abe`, working tree limpa. `classificacao_confronto` já existia desde o 2.5.1 (`estatuto`/`divergencia` já haviam sido removidos naquele pacote), mas sem taxonomia verificada nem resolução de `referencia_p3d` — 2.5-BL14 `PARCIAL`, 2.5-BL15 `AUSENTE`. |
| **Achado documental** | Nenhum documento oficial nem código definia um instrumento estruturado de P3d com registros endereçáveis por ID; a saída real de P3d era (e continua sendo, como preparação da sessão) `caso/P3d-divergencias.md` em texto livre. Decisão de implementação, aprovada antes de codificar: introduzir `contexto/divergencias/DIV-*.yaml`, registro estruturado mínimo curado pelo mesmo caminho de curadoria do 2.5.2, sem alterar `hb-confrontar` nem a fronteira EX3 do P3d. |
| **Implementação** | Taxonomia oficial extraída de EMCIA-ROT-01 §3.9 (`alinhada`, `divergente`, `nao_documentada`, `orfa`, `escrita_inacessivel`) adicionada como enum de `classificacao_confronto.classe` no schema da Regra. Novo `registro/p3d.schema.json` para o objeto `divergencia`. `curar.py` ganhou `checar_confronto()`: quando `classe: divergente`, exige `referencia_p3d` resolvível contra um registro `divergencia` curado e existente (comportamento mínimo de CTX-V11, não a bateria formal). `checar_versao()` generalizada para tratar mudança de `classificacao_confronto` como mudança relevante, exigindo versão nova com histórico, do mesmo modo que mudança de `procedencia` desde o 2.5.2. |
| **Testes** | `2.5.3-T01` a `2.5.3-T12` (mínimo obrigatório) + `2.5.3-T13` como regressão acumulada. Nenhum teste ficou `NÃO APLICÁVEL`. |
| **Defeitos** | Nenhum defeito de código nos pacotes anteriores; o achado foi documental (lacuna do instrumento de P3d, tratada como decisão de implementação, não como defeito). |
| **Correções** | Não houve correção de defeito pré-existente — o pacote implementou requisitos ausentes/parciais do baseline. |
| **Reteste** | 73/73 verificações aprovadas, 0 falhas, 0 skips: 61 da suíte anterior (sem regressão) + 12 novas de `p3d.py`. |
| **Eventos** | `ObjetoContextoCurado` e `CuradoriaRecusada`, emitidos por `curar.py`, agora também para o tipo `divergencia` e para a checagem de `classificacao_confronto`/`referencia_p3d`. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.3/resultado.md` |
| **Commit** | `323d153` — `feat(context): link CTX rules to P3d confrontation records` |
| **Estado final** | **CONFORME** |

Este pacote não implementou a bateria formal CTX-V01–V11 completa, o
resolvedor genérico de referências entre demais objetos CTX (2.5.4), a
integração executável P2/P3 → CTX → P4/P5 (2.5.5), nem qualquer item da
ação 2.6.

#### 3.10.5 Pacote 2.5.4 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.4` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Objetivo** | Formalizar as onze validações determinísticas do contrato CTX (CTX-V01–CTX-V11), extraídas literalmente de EMCIA-CTX-01 §3.13. |
| **Requisitos / baseline** | `D-05`, `2.5-BL16`, `2.5-BL17`, `2.5-BL18`, `2.5-BL19` |
| **Estado inicial** | `HEAD_INICIAL_2.5.4 = 004b42813c63ab7ba7bb3c2c86c7e74df99a9d53`, working tree limpa. Oito das onze CTX-V (`V01`–`V04`, `V08`–`V11`) já estavam corretamente implementadas pelos pacotes 2.5.0–2.5.3, mas sem o código formal `CTX-Vxx` associado — origem do "0/11" registrado no S2-BL. As três genuinamente ausentes eram `V05`, `V06` e `V07`: `entradas` (Regra) e `onde_vive` (Entidade) eram validados só como tipo `list`, sem resolução contra objetos curados existentes. |
| **Implementação** | Oito CTX-V formalizadas: mensagens de erro e eventos de `curar.py` passaram a citar o código (`CTX-V04`, `CTX-V09`, `CTX-V10`, `CTX-V11`), sem reescrever a lógica já correta. As três ausentes (`V05`–`V07`) implementadas por um resolvedor genérico e declarativo: `catalogo_referencias` (prefixo do id → tipo/diretório) e `references` (campo → prefixos aceitos), ambos lidos do schema do caso por `checar_referencias()`, sem hard-code de vocabulário EMCIA no núcleo. Fonte referenciada também passa pela própria validação estrutural (contrato mínimo); um arquivo físico em `fontes/` nunca satisfaz sozinho uma referência a Fonte CTX. |
| **Testes** | 22 pares negativo/positivo (`2.5.4-V01-N/P` a `2.5.4-V11-N/P`) + 1 teste de violações múltiplas (`2.5.4-multi`, confirmando política de validação acumulativa) = 23 verificações. |
| **Defeitos** | Nenhum defeito de código nos pacotes anteriores. Um erro de fixture nos próprios testes novos (valores de `premissa`/`evidencia` auto-preenchidos mascarando cenários negativos) foi corrigido antes da execução registrada como evidência. |
| **Correções** | Não houve correção de defeito pré-existente — implementação das três validações ausentes e formalização das oito existentes. |
| **Reteste** | 96/96 verificações aprovadas, 0 falhas, 0 skips: 73 da suíte anterior (sem regressão) + 23 novas de `ctx_v.py`. |
| **Eventos** | `CuradoriaRecusada`/`ObjetoContextoCurado` de `curar.py` agora incluem o código `CTX-Vxx` na lista de motivos, quando aplicável. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.4/resultado.md`; matriz completa em `.projectdocs/evidencias/sprint2/2.5.4/matriz-ctx-validacoes.md` |
| **Commit** | `e3d0bea` — `feat(context): enforce CTX validation contract` |
| **Estado final** | **CONFORME** |

**Indicador CTX-V:** baseline `0/11` → final `11/11`. Nenhuma validação foi
contabilizada apenas por constar no documento — todas as onze têm teste
negativo e controle positivo executados e persistidos.

Este pacote não implementou a integração executável P2/P3 → CTX → P4/P5
(2.5.5), a verificação consolidada da camada (2.5.6), nem qualquer item da
ação 2.6.

#### 3.10.6 Pacote 2.5.5 — execução efetiva

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.5` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Objetivo** | Integrar a produção de informação de P2/P3 à camada CTX e fazer P4/P5 consumirem o contexto validado. |
| **Requisitos / baseline** | `D-06`, `2.5-BL20`, `2.5-BL21`, `2.5-BL22` (parte de fluxo) |
| **Estado inicial** | `HEAD_INICIAL_2.5.5 = 2216feef1bece5cee01e3409631945ab1dd1fb93`, working tree limpa. Confirmado por inspeção direta (busca textual em todas as skills/comandos/agentes): nenhuma etapa P2–P5 referenciava `curar.py` ou `contexto/`; todas liam/escreviam só `caso/*.md`. `quadro.py` já existia e já lia CTX estruturado, mas nenhuma skill de P4 instruía usá-lo; `classificador-tecnologico` (P5) só tinha `Read, Grep`, sem consulta estruturada. |
| **Implementação** | P2 ganhou caminho real de propor Termo/Entidade/Regra/Fonte candidata em `rascunho/`, curada só por decisão humana. P3a manteve-se fora dos quatro objetos CTX (decisão de método: CTX-01 não define objeto de medição), com vínculo rastreável via `evidencia.referencia` quando aplicável. P3b/P3d tiveram o caminho já existente (2.5.2/2.5.3) formalizado nas skills. P4 passou a rodar `quadro.py` (já estrutural) antes de priorizar. P5 ganhou `eiac-nucleo/scripts/consultar.py`, leitura genérica e somente-leitura por id, reaproveitando `catalogo_referencias`; a skill/agente de P5 preservam D/I/V sem exigir V globalmente. |
| **Testes** | `2.5.5-T01` a `2.5.5-T16` (mínimo obrigatório) + `2.5.5-T05b` (controle positivo adicional) + `2.5.5-T17` como regressão acumulada. |
| **Defeitos** | Defeito real e pré-existente encontrado em `quadro.py`: `entradas: []`/`excecoes_conhecidas: []` eram tratados como "campo ausente" mesmo sendo válidos pelo schema (`required` sem `nonempty`), inconsistente com o tratamento que `decisor_quando_nao_cobre` já recebia no mesmo script. Descoberto ao montar o fluxo mínimo P2→CTX→P4. |
| **Correções** | `quadro.py`: checagem de ausência migrada de `r.get(c) in (None, "", [])` para `c not in r`, exceto para os três campos que o CTX-01 3.6 não exige terem conteúdo não-trivial. |
| **Reteste** | 113/113 verificações aprovadas, 0 falhas, 0 skips: 96 da suíte anterior (sem regressão) + 17 novas de `integracao.py`. |
| **Eventos** | `ObjetoContextoCurado`/`CuradoriaRecusada` de `curar.py` cobrem também os candidatos originados em P2 e as Regras de P3b/P3d — mesmo mecanismo, sem formato paralelo. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.5/resultado.md`; matriz em `.projectdocs/evidencias/sprint2/2.5.5/matriz-integracao.md` |
| **Commit** | `8420451` — `feat(context): integrate CTX with P2-P5 workflow` |
| **Estado final** | **CONFORME** |

**Indicadores da camada:** P2/P3 → CTX: **IMPLEMENTADO**. CTX → P4:
**IMPLEMENTADO**. CTX → P5: **IMPLEMENTADO**. Recusas de contexto
auditáveis: **SIM**.

Este pacote não implementou a verificação consolidada da camada (2.5.6),
nem qualquer item da ação 2.6 (contrato F0–P10, P6–P10, 18 HB, 4 AG,
portões E4/E5, geração de entregáveis).

#### 3.10.7 Pacote 2.5.6 — verificação consolidada (encerramento da Ação 2.5)

| Campo | Registro |
|---|---|
| **Pacote** | `2.5.6` |
| **Ação** | `2.5 — Camada de Contexto e Dados` |
| **Tipo** | Verificação consolidada — não introduz capacidade metodológica nova |
| **Objetivo** | Verificar de forma integrada e regressiva a camada implementada em 2.5.0–2.5.5. |
| **Baseline** | S2-BL |
| **Estado inicial** | `HEAD_INICIAL_2.5.6 = 96d1886580b6a638ed3deff24d5328ca5ad964d1`, working tree limpa. Todos os seis commits registrados nos pacotes anteriores (`acf35f9`, `9217925`, `c9df31f`, `323d153`, `e3d0bea`, `8420451`) confirmados presentes em `git log`, na ordem correta. Suíte geral no início: 113/113 PASS. |
| **Caso de controle** | `CTX-TEST-2.5.6-001` — ver `.projectdocs/evidencias/sprint2/2.5.6/caso-controle.md`. Construído do zero, sem reaproveitar estado residual; uma Regra central atravessa `D` → tentativa de sobrescrita recusada → `V` (v2) → `V` (v3, divergente, referenciando P3d), junto com reexecução de 8 das 11 CTX-V, referências a Termo/Entidade/Fonte, e o percurso P2→CTX→P3→P4→P5 completo. |
| **Testes** | `2.5.6-C01` a `2.5.6-C16`, todos PASS. |
| **Defeitos** | Nenhum em código de produção. Dois problemas identificados e corrigidos nas próprias fixtures do teste novo (`testes/consolidado.py`) antes da execução registrada como evidência — não afetam `eiac-nucleo/` nem `eiac-campo/`. |
| **Correções** | Nenhuma correção funcional necessária. |
| **Reteste** | 129/129 verificações aprovadas, 0 falhas, 0 skips: 113 da suíte anterior (sem regressão) + 16 novas de `consolidado.py`. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.5.6/resultado.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.5.6/matriz-consolidada.md` |
| **Caso** | `.projectdocs/evidencias/sprint2/2.5.6/caso-controle.md` |
| **Commit** | `fc5fd2f` — `test(context): verify Sprint 2 context and data layer` |
| **Estado final da Ação 2.5** | **CONFORME** |

**Indicadores finais da Ação 2.5:** Procedência D/I/V **CONFORME** ·
Objetos CTX **4/4** · CTX-V **11/11** · Curadoria protegida **SIM** ·
I→V versionado **SIM** · P3d rastreável **SIM** · P2/P3→CTX
**IMPLEMENTADO** · CTX→P4 **IMPLEMENTADO** · CTX→P5 **IMPLEMENTADO** ·
Eventos de recusa **CONFORME**.

**Comparação S2-BL → final da Ação 2.5:**

| Indicador | S2-BL | Final Ação 2.5 |
|---|---|---|
| D/I/V | divergente | conforme, contrato único |
| Objetos CTX conformes | 0/4 plenamente alinhados | 4/4 |
| `autoria_conteudo` × `registrado_por` | ausente | conforme (CTX-V09) |
| Histórico I→V imposto | parcial | conforme (CTX-V04/V10) |
| `referencia_p3d` | ausente | conforme, resolvível (CTX-V11) |
| CTX-V | 0/11 | 11/11 |
| P2/P3 → CTX | parcial | implementado |
| CTX → P4/P5 | parcial | implementado |
| Eventos CTX | ausente | conforme |

**Situação dos defeitos do baseline relativos à Ação 2.5:**

| ID | Síntese | Pacote | Estado |
|---|---|---|---|
| D-01 | Procedência multidimensional antiga | 2.5.0 | RESOLVIDO |
| D-02 | Quatro objetos CTX no schema anterior | 2.5.1 | RESOLVIDO |
| D-03 | Curadoria e versionamento não impostos | 2.5.2 | RESOLVIDO |
| D-04 | P3d sem `referencia_p3d` | 2.5.3 | RESOLVIDO |
| D-05 | CTX-V01–V11 ausentes | 2.5.4 | RESOLVIDO |
| D-06 | P2/P3 não alimentam e P4/P5 não consomem CTX | 2.5.5 | RESOLVIDO |

Nenhum defeito foi apagado do histórico — cada um mantém sua entrada em
§3.11, com a resolução registrada aqui como evidência adicional.

**Este pacote não iniciou nenhum item da ação 2.6** (contrato executável
F0–P10, P6–P10, 18 HB, 4 AG, portões restantes, E4/E5). Aguarda revisão
humana e aprovação formal antes de 2.6.0.

#### 3.10.8 Pacote 2.6.0 — contrato executável F0–P10 (início da Ação 2.6)

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.0` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Representar declarativamente o percurso integral F0–P10, suas fronteiras, inegociáveis e autorizações de emissão, sem implementar comportamento de P6–P10. |
| **Baseline** | `2.6-BL01`–`BL05`, `2.6-BL18`–`BL20`, `D-07` |
| **Estado inicial** | `HEAD_INICIAL_2.6.0 = 667c0212e81721b67b3dcf866b3eb3333a7d60d4`, working tree limpa. Playbook v0.3.1 com 8/13 etapas (F0, P1, P2, P3a, P3b, P3d, P4, P5); `E4`/`E5` com `portao_pendente: true`; `E5` sem `P8` e sem inegociável 3; `E3-E` com condição em string livre; inegociável 1 com texto mais restritivo que MET-01 §3.4.3. Suíte geral no início: 129/129 PASS. |
| **Fontes documentais** | EMCIA-MET-01, EMCIA-CAT-01, EMCIA-ESP-01 v0.2, EMCIA-CAM-01 v0.1 (leitura obrigatória); EMCIA-E1–E5, EMCIA-ROT-01 (consulta). |
| **Achado documental** | A pendência de correspondência entregável×passo registrada em `decisoes/012` (E4=P6/P7 vs. E4=P6/P7/P8, conforme a fonte) está resolvida por EMCIA-CAM-01 e EMCIA-ESP-01 v0.2 (17/09/2026): E4=P6/P7, E5=P8/P9/P10, coincidindo com o relatório do PFC. Registrado como `decisoes/013`. |
| **Implementação** | Playbook (`eiac-campo/template-caso/registro/playbook.json`) v0.3.1→v0.4.0: adicionadas as etapas P6, P7, P8, P9 e P10 com fase, camada por nível, `depende_de`, e para P10 `recorrente`/`cadencia_obrigatoria`/`responsavel_obrigatorio`; `E4`/`E5` corrigidos (`portao_pendente` removido, `E5` passa a incluir `P8` e o inegociável 3); `E3-E.condicao` convertida de string livre para estrutura declarativa `{campo, etapa, operador, valor}`; texto do inegociável 1 corrigido para admitir estimativa em N1 (MET-01 §3.4.3). `eiac-nucleo/scripts/playbook.py` ganhou checagens estruturais genéricas (sem vocabulário do método): ID de etapa duplicado, camada fora de EX1–EX4, `depende_de`/portão/inegociável órfão, e recorrência exigindo cadência e responsável. Nenhum outro script do núcleo foi alterado — `estado.py`, `avancar.py`, `guarda.py` e `fronteira.py` já liam os campos genéricos necessários. |
| **Testes** | `2.6.0-T01` a `2.6.0-T24` (estruturais/positivos) + `2.6.0-N01` a `2.6.0-N05` (fixtures negativas temporárias, playbook oficial nunca sobrescrito). |
| **Defeitos** | Nenhum defeito de produção novo. `D-07` (baseline) tratado por este pacote. |
| **Correções** | Ver `resultado.md` §9–14. |
| **Reteste** | 158/158 verificações aprovadas, 0 falhas, 0 skips: 129 da suíte anterior (sem regressão) + 29 novas de `playbook_2_6_0.py`. |
| **Capacidades pendentes do núcleo** | Interpretação semântica da condição de E3-E; mecanismo de cadência/scheduler de P10; verificação semântica dos cinco inegociáveis; validação de composição semântica de portão (ex.: conjunto exato de um portão, não apenas existência das etapas referenciadas); proteção de `registro/` (D-08); eventos de recusa de `avancar.py` (D-09). Todas atribuídas a 2.6.1 em diante. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.0/resultado.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.6.0/matriz-contrato-f0-p10.md` |
| **Commit** | `f3ae15e` — `refactor(playbook): freeze full F0-P10 execution contract` |
| **Estado final** | **CONFORME** |

**Indicadores após o pacote 2.6.0:** Etapas declaradas **13/13** ·
Inegociáveis declarados **5/5** · Autorizações declaradas **6/6** · P3b
não delegável **SIM** · P7 não delegável **SIM** · P10 recorrente **SIM**.
Etapas operacionalmente implementadas permanecem **8/13** (F0–P5) — a
declaração do contrato não antecipa a execução de P6–P10.

Este pacote não implementou: máquina de protocolos genérica além do que
`avancar.py`/`guarda.py` já faziam; proteção de `registro/`; eventos para
toda recusa de `avancar.py`; verificação semântica dos cinco
inegociáveis; P6–P10 operacionais; 18 HB completas; 4 AG mapeados;
geração material de E4/E5; percurso end-to-end F0–P10. Esses itens
pertencem a 2.6.1–2.6.6. Aguarda revisão humana antes de iniciar 2.6.1.

#### 3.10.9 Pacote 2.6.1 — núcleo genérico de protocolos

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.1` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Fortalecer o núcleo genérico para aplicar o contrato F0–P10 declarado em 2.6.0 sem hard-code da semântica EMCIA. |
| **Baseline** | `2.6-BL12`–`BL17`, `2.6-BL26`, `D-08`, `D-09` |
| **Estado inicial** | `HEAD_INICIAL_2.6.1 = 70d1d9bf793ab53b0218b1a5663915c4baa1c9ae`, working tree limpa. Defeito de `2.6-BL12` reproduzido: com o caso em `P1`, `avancar.py --encerrar P5` retornava `exit 0` e movia `etapa_atual` direto para `P6`, sem checar dependências/sessões das etapas puladas. `guarda.py` sem regra sobre `registro/` (`2.6-BL17`/`D-08`). `avancar.py` só emitia evento em dois pontos; todo `return` de erro em `encerrar()`/`emitir()` saía sem evento (`2.6-BL15`/`D-09`). `st["inegociaveis"][n]` era booleano gravável só por edição direta (`2.6-BL26`). Suíte geral no início: 158/158 PASS. |
| **Implementação** | `avancar.encerrar()` passou a recusar `etapa_id != st["etapa_atual"]` antes de qualquer outra checagem (corrige `2.6-BL12`). Novo comando `--registrar-recorrencia` (cadência/responsável, com `_ator_valido()` recusando nome vazio, agente ou coletivo genérico) grava `estado_recorrente` com ciclo/`ultima_verificacao`/histórico. Novo comando `--satisfazer-inegociavel` como único caminho autorizado, gravando registro estruturado `{satisfeito, evidencia, autor, data}`; `emitir()` valida essa estrutura, não um booleano solto (corrige `2.6-BL26`). Nova regra G5 em `guarda.py` bloqueia escrita direta em `registro/` via `Write`/`Edit`/redirecionamento de shell, preservando a invocação autorizada dos scripts do núcleo via `Bash` (corrige `2.6-BL17`/`D-08`). `avancar.main()` emite `RecusaMaquina`/`RecusaEmissao` em todo caminho de erro (corrige `2.6-BL15`/`D-09`). `playbook.carregar()` ganhou validação estrutural de `condicao` declarativa (campos, etapa referenciada, operador reconhecido). Novo `playbook.capacidade_valida()` — mecanismo isolado de critério de verificação, testado com fixtures sintéticas, sem integração ao playbook oficial (decisão explícita: integração com HB/AG reais pertence a 2.6.4). |
| **Testes** | `2.6.1-T01` a `2.6.1-T32` (com sub-itens T01b, T03b, T10b, T12b, T20b, T20c, T27b) — 39 verificações. |
| **Defeitos** | Um defeito de produção confirmado e corrigido: `2.6-BL12` (etapa corrente não verificada). Seis bugs de fixture no próprio `testes/nucleo_2_6_1.py`, corrigidos antes da evidência registrada — não afetam `eiac-nucleo/`. |
| **Correções** | Ver `resultado.md` §6–15. |
| **Reteste** | 197/197 verificações aprovadas, 0 falhas, 0 skips: 158 da suíte anterior (sem regressão) + 39 novas de `nucleo_2_6_1.py`. |
| **Hard-code EMCIA** | Busca por P6–P10/E4/E5/autonomia/recalibragem/piloto/métrica de resultado em `eiac-nucleo/`: 2 ocorrências, ambas não comportamentais (exemplo de CLI em docstring, comentário). `HARD-CODE EMCIA NO NÚCLEO: 0` comportamental. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.1/resultado.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.6.1/matriz-regras-nucleo.md` |
| **Commit** | `2105f6c` — `feat(nucleo): enforce generic F0-P10 protocol contracts` |
| **Estado final** | **CONFORME** |

**Indicadores após o pacote 2.6.1:** Máquina de estados genérica
**CONFORME** · Dependências **CONFORME** · Guardas de camada
**CONFORME** · Proteção `registro/` **SIM** · Eventos de recusa
**CONFORME** · Recorrência **SUPORTADA** · Cadência obrigatória
**SUPORTADA** · Responsável nominal **SUPORTADO** · Inegociável genérico
**SUPORTADO** (caminho autorizado; verificação semântica do conteúdo
ainda pendente para 2.6.2/2.6.3/2.6.5) · Condições de portão
**SUPORTADAS** (avaliação genérica; integridade estrutural também
validada no carregamento) · Hard-code EMCIA no núcleo **0**.

Este pacote não implementou: conteúdo metodológico de P6; decisão de
P7; termo de autonomia; conteúdo de P8; definição semântica de outcome
em P9; decisão de recalibragem em P10; 18 HB; 4 AG; materialização de
E4/E5; percurso integral F0–P10; scheduler real de recorrência (o
mecanismo representa estado, não agenda automaticamente). Esses itens
pertencem a 2.6.2–2.6.6. Aguarda revisão humana antes de iniciar 2.6.2.

#### 3.10.10 Pacote 2.6.2 — P6 e P7 (implementação operacional)

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.2` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Implementar operacionalmente P6 (especificação operacional) e P7 (termo de autonomia), preservando a decisão humana sobre a fronteira de autonomia. |
| **Baseline** | P6 ausente, P7 ausente, P7 não delegável ausente operacionalmente, `D-10` (parte P7) |
| **Estado inicial** | `HEAD_INICIAL_2.6.2 = 3f7fb2a1926619a27ba009e0fc07637ecaf18b74`, working tree limpa. Playbook já declarava P6/P7 corretamente (2.6.0), mas nenhuma skill, script ou objeto de domínio existia para eles. `reference/gates.md` e `hb-emitir-e4` ainda citavam a pendência de correspondência entregável×passo já resolvida em 2.6.0 (`decisoes/013`). Suíte geral no início: 197/197 PASS. |
| **Achado durante a implementação** | `guarda.py` G1 bloqueava o carregamento de qualquer `SKILL.md` de etapa EX3/EX4 independentemente de sessão humana registrada — defeito pré-existente (já afetava `hb-confrontar`, `hb-priorizar`, `hb-classificar`), fora do escopo original do pacote, corrigido por decisão explícita em commit separado. |
| **Implementação** | Dois novos domínios de `registro/`, distintos de `contexto/` (CTX-01, intocado): `registro/operacional/` (P6, schema `operacional.schema.json`, script `eiac-campo/scripts/operacional.py`, estados `proposta`→`validado`) e `registro/governanca/autonomia/` (P7, schema `autonomia.schema.json`, script `eiac-campo/scripts/governanca.py`, estados `rascunho`→`proposto`→`decidido`). Ambos os scripts vivem em `eiac-campo/` e reaproveitam as primitivas genéricas do núcleo (`estrutura.validar`, `estado.evento`, `estado.autor_e_agente`) sem alterá-las com semântica de método. `governanca.py` exige `operacional_ref` resolvendo para um `OP-*` já `validado` (relação P7→P6, aplicada por checagem de campo, não por hard-code no núcleo). Ambos os scripts bloqueiam estruturalmente a transição só-humana (`validado`/`decidido`) para atores agente e para nomes genéricos de coletivo. `guarda.py` G1 corrigida: passa a considerar sessão humana válida (`cumprimentos[etapa]["sessao"]`) antes de bloquear carregamento de skill EX3/EX4 — não delega decisão, que continua bloqueada por outras regras. Novas skills `hb-operacionalizar` (P6) e `hb-governar` (P7), comandos `operacionalizar.md`/`governar.md`. `reference/gates.md` e `hb-emitir-e4` atualizados para refletir E4=P6/P7, E5=P8/P9/P10 sem pendência. |
| **Testes** | `2.6.2-T01` a `2.6.2-T33` + `G1a`/`G1b`/`G1c` (achado da correção de G1) — 38 verificações. |
| **Defeitos** | Um defeito de produção real, pré-existente, corrigido (G1/sessão humana). Nenhum defeito novo introduzido pelos scripts de campo. |
| **Correções** | Ver `resultado.md` §17–18. |
| **Reteste** | 235/235 verificações aprovadas, 0 falhas, 0 skips: 197 da suíte anterior (sem regressão) + 38 novas de `campo_2_6_2.py`. |
| **Hard-code EMCIA** | Busca por P6/P7/autonomia/governança/E4 em `eiac-nucleo/` após as edições: 1 ocorrência, não comportamental (comentário pré-existente desde 2.6.1). `HARD-CODE EMCIA NO NÚCLEO: 0` comportamental. |
| **Caso de controle** | `PP-TEST-2.6.2-001` — percurso F0→P7 completo; agente prepara ambos os artefatos, tentativa de decisão por agente recusada com evento, decisão final por humano nomeado com evento e evidência rastreável para o inegociável 2. Nota honesta: `avancar.py --emitir E4` retornou `exit 0` no caso de controle (portão estrutural satisfeito pelo mecanismo de 2.6.1) — isso não substitui a validação semântica do inegociável 2 nem a materialização do documento, ambas do pacote 2.6.5. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.2/resultado.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.6.2/matriz-p6-p7.md` |
| **Caso** | `.projectdocs/evidencias/sprint2/2.6.2/caso-controle.md` |
| **Commits** | `f1f1a4c` — `fix(nucleo): allow human-layer skills with valid session`; `25905ac` — `feat(field): implement P6-P7 operational governance flow`; `144b7c6` — `docs(evidence): register package 2.6.2 execution` |
| **Estado final** | **CONFORME** |

**Indicadores após o pacote 2.6.2:** P6 operacional **SIM** · P7
operacional **SIM** · P7 não delegável **CONFORME** · Minuta por agente
**SUPORTADA** · Decisão por agente **BLOQUEADA** · Decisão humana
**SUPORTADA** · Responsável nominal **EXIGIDO** · Termo de autonomia
**PRODUZÍVEL** · Evidência para E4 **SIM** (insumos rastreáveis; E4 não
declarado emitido em definitivo).

**Situação de D-10:** `PARCIALMENTE RESOLVIDO`. A parte referente a P7
está tratada (não delegável operacionalmente conforme, decisão humana
obrigatória, evidência rastreável). P10 permanece ausente e será tratado
em 2.6.3 — `D-10` só fecha por completo então.

Este pacote não implementou: P8, P9, P10; recorrência operacional
completa de P10; catálogo formal das 18 HB e 4 AG; validação semântica
completa dos cinco inegociáveis; emissão final de E4/E5; materialização
completa E1–E5; percurso F0–P10 completo. Esses itens pertencem a
2.6.3–2.6.6. Aguarda revisão humana antes de iniciar 2.6.3.

#### 3.10.11 Pacote 2.6.3 — P8, P9 e P10 (implementação operacional)

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.3` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Implementar operacionalmente P8 (casos de teste com saída esperada), P9 (mensuração do valor contra a linha de base) e P10 (calibragem recorrente, detecção de desvio e decisão humana sobre evolução). |
| **Baseline** | P8 ausente, P9 ausente, P10 ausente, P10 recorrente ausente operacionalmente, E5 implementado mas divergente, `D-10` (parte P10) |
| **Estado inicial** | `HEAD_INICIAL_2.6.3 = 3431e6fd6dbcbaa24112e2d99c033fcd4d672ac8`, working tree limpa. Playbook já declarava P8/P9/P10 corretamente (2.6.0), incluindo `recorrente`/`cadencia_obrigatoria`/`responsavel_obrigatorio`/`delegavel: false` em P10 e a camada textual "EX4 na decisão, EX2 no monitoramento" (confirmada em EMCIA-CAM-01 §3.6). O núcleo já suportava genericamente recorrência, cadência, responsável nominal e satisfação de inegociáveis por caminho autorizado desde 2.6.1 — nenhuma dessas primitivas exigiu alteração. Suíte geral no início: 235/235 PASS. |
| **Implementação** | Três novos domínios de `registro/`, distintos de `contexto/`, `registro/operacional/` e `registro/governanca/` (2.6.2, intocados): `registro/piloto/` (P8, schema `piloto.schema.json`, script `eiac-campo/scripts/piloto.py`, estados `rascunho`→`revisado`), `registro/metricas/` (P9, schema `metricas.schema.json`, script `eiac-campo/scripts/metrica.py`, estados `planejada`→`apurada`) e `registro/calibragem/` (P10, schema `calibragem.schema.json` com dois objetos — `rotina_calibragem`, sem estado, e `ciclo_calibragem`, com `drift_detectado`/`decisao` opcional —, script `eiac-campo/scripts/calibragem.py`). Todos os três scripts vivem em `eiac-campo/` e reaproveitam as primitivas genéricas do núcleo (`estrutura.validar`, `estado.evento`, `estado.autor_e_agente` e, para recorrência/inegociáveis, `avancar.registrar_recorrencia`/`avancar.satisfazer_inegociavel`, já genéricas desde 2.6.1) sem alterar `eiac-nucleo/` — nenhum arquivo do núcleo foi tocado neste pacote. `metrica.py` exige `piloto_ref` resolvendo para um `CT-*` `revisado` (relação P8→P9); `calibragem.py` resolve `metricas_ref` contra `registro/metricas/` (relação P9→P10). A decisão de recalibragem (`recalibrar`/`expandir`/`descontinuar` — únicas três opções nomeadas em CAT-01/CAM-01/ESP-01) é bloqueada estruturalmente para agentes em `calibragem.py::checar_decisao`. Novas skills `hb-pilotar` (P8), `hb-medir-valor` (P9) e `hb-recalibrar` (P10, `delegavel: false`, mesma marcação de `hb-governar`), comandos `/pilotar`, `/medir-valor`, `/recalibrar`. |
| **Achado durante a implementação** | `calibragem.py::gravar_ciclo` recusava incondicionalmente qualquer segunda gravação do mesmo identificador de ciclo, mesmo para complementar um ciclo pendente (drift detectado, sem decisão) com a decisão humana — bloqueando o fluxo de duas fases que o caso de controle integrado exigiu ao reproduzir "agente detecta e recomenda; humano decide depois, sobre o mesmo ciclo". Corrigido dentro deste mesmo pacote, antes do commit (não é defeito pré-existente de outro pacote). |
| **Testes** | `2.6.3-T01` a `2.6.3-T48` + sub-verificações (`T05a`, `T10b`/`T11b`, `T29b`/`T29c`, `G5a`-`G5c`) — 57 verificações. |
| **Defeitos** | Um defeito introduzido e corrigido dentro do próprio pacote (`calibragem.py`, ciclo em duas fases). Nenhum defeito de outro pacote encontrado. |
| **Correções** | Ver `resultado.md` §25–26. |
| **Reteste** | 292/292 verificações aprovadas, 0 falhas, 0 skips: 235 da suíte anterior (sem regressão) + 57 novas de `campo_2_6_3.py`. |
| **Hard-code EMCIA** | Busca por P8/P9/P10/piloto/baseline/métrica/drift/calibragem/recalibragem/E5 em `eiac-nucleo/` após as edições: 3 ocorrências, todas não comportamentais (uma linha de docstring de exemplo, duas de comentário explicativo pré-existente sobre `2.6-BL26`). `eiac-nucleo/` não foi alterado neste pacote. `HARD-CODE EMCIA NO NÚCLEO: 0` comportamental. |
| **Caso de controle** | `caso-controle-2-6-3` — percurso F0→P10 completo; P8 com dois casos (um célula crítica), P9 com métrica de resultado (45min→31min) e métrica de uso, P10 com responsável nomeado e cadência mensal, ciclo 1 sem drift, ciclo 2 com drift — tentativa de decisão por agente recusada duas vezes com evento, decisão humana válida registrada. Evidências rastreáveis para os inegociáveis 3, 4 e 5. E5 não emitido. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.3/resultado.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.6.3/matriz-p8-p10.md` |
| **Caso** | `.projectdocs/evidencias/sprint2/2.6.3/caso-controle.md` |
| **Commit** | `e210266` — `feat(field): implement P8-P10 pilot measurement calibration flow` |
| **Estado final** | **CONFORME** |

**Indicadores após o pacote 2.6.3:** P8 operacional **SIM** · P9
operacional **SIM** · P10 operacional **SIM** · P10 recorrente
**CONFORME** · Casos com saída esperada **CONFORME** · Métrica de
outcome **DISPONÍVEL** · Responsável nominal P10 **CONFORME** ·
Cadência **CONFORME** · Drift detectável **SIM** · Decisão de
recalibragem humana **CONFORME** · Evidência para E5 **SIM** (insumos
rastreáveis; E5 não declarado emitido).

**Situação de D-10:** `RESOLVIDO`. P7 (2.6.2) e P10 (2.6.3) estão
ambos operacionalmente conformes: não delegáveis onde exigido, decisão
humana obrigatória e registrada, responsável nominal e cadência
exigidos por P10, evidência rastreável para os inegociáveis 2 e 5.

Este pacote não implementou: catálogo formal das 18 HB e 4 AG;
validação semântica completa dos cinco inegociáveis; emissão final de
E4/E5; materialização completa E1–E5; percurso F0–P10 completo. Esses
itens pertencem a 2.6.4–2.6.6. Aguarda revisão humana antes de iniciar
2.6.4.

#### 3.10.12 Pacote 2.6.4 — formalização das 18 HB e 4 AG

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.4` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Formalizar as 18 capacidades HB e os 4 papéis AG, conectando cada capacidade ao playbook, implementação física e critério de verificação. |
| **Baseline** | 13 skills físicas, 9/18 HB referenciadas (cresceu para 14/18 após 2.6.2/2.6.3), 0/18 códigos estáveis, 2 agentes físicos, 0/4 AG formalmente mapeados, `D-11` aberto |
| **Estado inicial** | `HEAD_INICIAL_2.6.4 = 418a91635b96742a443e36ad4976146c4b04894a`, working tree limpa. Playbook já referenciava 14/18 HB (não 9/18 — o número cresceu com 2.6.2/2.6.3); nenhum catálogo declarativo existia. Suíte geral no início: 292/292 PASS. |
| **Implementação** | Catálogo declarativo em `eiac-campo/reference/habilidades.json` (18 HB, id/nome/camada/automatizada/insumo/saída/critério de verificação/AG autorizado/skill_ref/etapas — todos extraídos literalmente de EMCIA-CAT-01 Anexo A) e `agentes.json` (4 AG, id/nome/camada/hb_autorizadas/implementação física). Resolução genérica em novo `eiac-nucleo/scripts/catalogo.py` — não conhece HB, AG nem qualquer nome EMCIA, só dois objetos genéricos (`capacidade`, `papel`) com `id`, reaproveitando `playbook.capacidade_valida()` (2.6.1/ESP-01 G6). A relação HB↔etapa vem exclusivamente de `playbook.json` (nunca de inferência textual entre CAT-01 e MET-01/CAM-01, preservando a pendência já registrada sobre correspondência entregável×passo, `decisoes/002`). 5 skills ganharam `hb:` no frontmatter (`hb-enquadrar`, `hb-extrair-regras`, `hb-mapear-contexto`, `hb-priorizar`, `hb-classificar`), somando-se às 4 já herdadas de 2.6.2/2.6.3. Nenhum arquivo físico de agente novo foi criado — os 4 AG lógicos resolvem sobre a infraestrutura existente (2 subagents + skills de etapa). |
| **Achado** | Nenhum defeito de produção pré-existente encontrado. Confirmado que 4/18 HB (HB-04, HB-05, HB-06, HB-13) não têm implementação física nem referência no playbook — registrado explicitamente no catálogo (`estado_relacao_etapa: "nao_referenciada_no_playbook"`), não é defeito, é o estado real do contrato. |
| **Testes** | `2.6.4-T01` a `2.6.4-T50` — 50 verificações. |
| **Defeitos** | Nenhum. |
| **Correções** | Não aplicável. |
| **Reteste** | 342/342 verificações aprovadas, 0 falhas, 0 skips: 292 da suíte anterior (sem regressão) + 50 novas de `campo_2_6_4.py`. |
| **Hard-code EMCIA** | Busca por HB-01/HB-18/AG-01/AG-04/Enquadramento/Análise documental/Especificação/Avaliação em `eiac-nucleo/` após as edições: 7 ocorrências, todas não comportamentais (docstrings de exemplo, um comentário pré-existente). `HARD-CODE EMCIA NO NÚCLEO: 0` comportamental. |
| **Caso de controle** | Cadeia completa etapa→HB→catálogo→AG→skill→critério→execução, demonstrada para HB-10/P4 (dentro de P1–P5) e HB-17/P9 (dentro de P6–P10): AG autorizado aceito, AG não autorizado recusado, para ambos. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.4/resultado.md` |
| **Inventário** | `.projectdocs/evidencias/sprint2/2.6.4/inventario-hb-ag.md` |
| **Matriz** | `.projectdocs/evidencias/sprint2/2.6.4/matriz-hb-ag.md` |
| **Caso** | `.projectdocs/evidencias/sprint2/2.6.4/caso-controle.md` |
| **Commit** | `dff5a08` — `feat(field): formalize HB and AG capability catalogs` |
| **Estado final** | **CONFORME** (escopo executável do pacote); **PARCIAL** quanto a D-11 |

**Indicadores após o pacote 2.6.4:** HB declaradas **18/18** · HB com
código estável **9/18** · HB com critério de verificação **18/18** · HB
com implementação resolvível **14/18** · AG declarados **4/4** · AG com
mapeamento HB **4/4** · referências HB do playbook resolvíveis
**14/14** · AG com capacidade EX3/EX4 indevida **0** (confirmado).

**Situação de D-11:** `PARCIAL`. O catálogo está completo e correto
(18/18 HB, 4/4 AG, relações resolvem, critérios existem onde
documentados, playbook resolve HB, fronteira humana preservada), mas
nem toda skill possui identidade HB rastreável (9/18 com `hb:`, as
demais são infraestrutura ou capacidade não catalogada por CAT-01, não
faltantes) e 4/18 HB não têm implementação física ainda. Registrado
como PARCIAL, não RESOLVIDO, por critério estrito da seção 55 do
pacote.

Este pacote não implementou: validação semântica completa dos cinco
inegociáveis; emissão final de E1–E5; fechamento final dos seis
portões; percurso F0–P10 completo. Esses itens pertencem a 2.6.5–2.6.6.
Aguarda revisão humana antes de iniciar 2.6.5.

#### 3.10.13 Pacote 2.6.5 — portões, inegociáveis e materialização de E1–E5

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.5` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Objetivo** | Tornar semanticamente verificáveis os cinco inegociáveis, operacionalizar os seis portões de emissão e materializar E1–E5 a partir das evidências reais do caso. |
| **Baseline** | Portões estritamente conformes 2/6, inegociáveis semanticamente verificáveis 0/5, emissão só registrava evento `EntregavelEmitido` sem materialização, `D-12` aberto. |
| **Estado inicial** | `HEAD_INICIAL_2.6.5 = 57700a0d2c421f891de2d48a0ab0f090c45eda63`, working tree limpa. `avancar.py` já possuía `satisfazer_inegociavel`/`emitir` genéricos desde 2.6.1, mas `satisfazer_inegociavel` aceitava evidência em texto livre (nunca verificada contra artefato real) e `emitir` só checava etapas/condição/registro de inegociável, sem exigir nem produzir documento material. Suíte geral no início: 342/342 PASS. |
| **Implementação** | Novo `eiac-campo/scripts/inegociaveis.py`: cinco verificadores puros (`verificar_i1`–`verificar_i5`), cada um lendo exatamente um artefato real (`registro/baseline/`, `registro/governanca/autonomia/`, `registro/piloto/`, `registro/metricas/`, `registro/calibragem/`) e só então chamando `avancar.py --satisfazer-inegociavel` com a evidência referenciando o verificador e o artefato — nunca um booleano solto. Novo domínio `registro/baseline/` (linha de base, inegociável 1) — sem schema/ID dedicado em nenhuma fonte oficial (MET-01 §3.4.3 só exige "registrada e datada"; o formato concreto vem de EMCIA-E2 Parte A.3); `BL-nnn` é convenção técnica do Estúdio, não terminologia do método, decisão tomada explicitamente com o usuário. `baseline.py` recusa `apuracao: estimado` fora de N1 (MET-01 §3.4.3). `metrica.py` ganhou `baseline_ref` opcional para P9 referenciar a mesma linha de base de I1, sem duplicar o valor (checagem cruzada `valor_atual`/`data`). `eiac-nucleo/scripts/avancar.py::emitir()` passou a devolver `(None, motivo)` distinto de `(erro, None)` quando a condição declarativa de um entregável não se aplica ao caso (E3-E sobre caso não agêntico) — `NAO_APLICAVEL`, exit 0, evento `EntregavelNaoAplicavel`, nunca `RecusaEmissao`. Ganhou `--materializar <arquivo>`: só registra `EntregavelEmitido` se o arquivo existir e não estiver vazio, gravando `arquivo`/`versao` no evento e em `estado.entregaveis_emitidos[ID]` (versão incrementada a cada reemissão, nunca sobrescrita silenciosa). Novo `eiac-campo/scripts/entregaveis.py` renderiza `caso/entregaveis/<ID>.md` a partir dos artefatos reais do caso, recusando materializar (`NaoMaterializavel`) quando falta evidência rastreável para um campo obrigatório do modelo oficial — nunca preenche com texto genérico. `E3` permanece um único entregável ao cliente: `render_e3` sempre escreve a Parte A (decisão) e só acrescenta a Parte B quando `classificacao_tecnologica` de P5 contém `"agente"`; `emitir()` avalia `E3-D` (sempre) e `E3-E` (condicional, pode ser `NAO_APLICAVEL`) internamente antes de materializar o arquivo único. |
| **Achado** | Nenhum artefato/schema dedicado de "linha de base" existe em nenhuma fonte oficial — decisão tomada com o usuário (não inferir do playbook, não fabricar `criterio_de_habilitacao`-like concept) de criar `registro/baseline/` como domínio técnico do Estúdio. `calibragem.py::_ator_pessoa_nomeada` (mecanismo herdado de 2.6.2/2.6.3) recusa apenas palavras genéricas exatas, deixando passar frases compostas como `"equipe de TI"`; `inegociaveis.verificar_i5` fecha essa lacuna com checagem por token. Nenhum defeito de produção pré-existente encontrado; um erro de nome de campo introduzido neste próprio pacote (`criterio_aprovacao` vs. `criterio_aprovacao_escala` em `entregaveis.py::render_e5`) foi encontrado e corrigido durante a construção do caso de controle, antes do commit. |
| **Testes** | `2.6.5-T01` a `2.6.5-T60` (mais `T02b`/`T09b`) — 62 verificações. |
| **Defeitos** | Nenhum de produção pré-existente. |
| **Correções** | Nome de campo corrigido em `entregaveis.py::render_e5` (`criterio_aprovacao_escala`), encontrado durante a construção do caso de controle. |
| **Reteste** | 404/404 verificações aprovadas, 0 falhas, 0 skips: 342 da suíte anterior (sem regressão) + 62 novas de `campo_2_6_5.py`. |
| **Hard-code EMCIA** | Busca por `E1`/`E2`/`E3-D`/`E3-E`/`E4`/`E5`/`baseline`/`autonomia`/`saida_esperada`/`metrica de resultado`/`recalibragem` em `eiac-nucleo/` após as edições: todas as ocorrências em docstring de uso (`--emitir E2`) ou comentário explicando o que o mecanismo genérico NÃO conhece. `HARD-CODE EMCIA NO NÚCLEO: 0` comportamental (T54). |
| **Caso de controle** | Percurso F0→E5 completo, cenário agêntico (P5 classifica como agente, exercitando `E3-E` como AUTORIZADO), P6/P7/P8/P9/P10 válidos, os cinco inegociáveis satisfeitos a partir de artefato real, os seis portões avaliados, os cinco entregáveis materializados, tentativa de agente regravar termo já decidido recusada com evento. |
| **Evidência** | `.projectdocs/evidencias/sprint2/2.6.5/resultado.md` |
| **Matrizes** | `.projectdocs/evidencias/sprint2/2.6.5/matriz-portoes.md`, `matriz-inegociaveis.md`, `matriz-entregaveis.md` |
| **Caso** | `.projectdocs/evidencias/sprint2/2.6.5/caso-controle.md` |
| **Commit** | `639a8d6` — `feat(field+nucleo): enforce deliverable gates and materialize E1-E5` |
| **Estado final** | **CONFORME** quanto ao escopo executável do pacote; **RESOLVIDO** quanto a D-12 |

**Indicadores após o pacote 2.6.5:** inegociáveis semanticamente
verificáveis **5/5** · autorizações operacionalmente avaliáveis **6/6**
· portões com par negativo+positivo **6/6** · entregáveis
materializáveis **5/5** · emissão sem arquivo **0** (confirmado por
`--materializar` recusando artefato inexistente, T40).

**Situação de D-12:** `RESOLVIDO`. E1–E5 geram artefatos reais
(`caso/entregaveis/<ID>.md`), o evento `EntregavelEmitido` aponta para
o arquivo e a versão, a versão é identificável e incrementada a cada
reemissão sem sobrescrita silenciosa, e emissão negada nunca produz
documento (materialização recusada com `NaoMaterializavel` antes de
qualquer tentativa de emissão).

Este pacote não fechou ainda a Ação 2.6 nem a Sprint 2: falta o caso de
controle integral F0–P10 com verificação de todas as camadas juntas e
demonstração de ausência de regressão em conjunto — isso pertence a
2.6.6. Aguarda revisão humana antes do fechamento final da Ação 2.6.

#### 3.10.14 Pacote 2.6.6 — verificação integral F0–P10 e fechamento da Ação 2.6

| Campo | Registro |
|---|---|
| **Pacote** | `2.6.6` |
| **Ação** | `2.6 — Camada de Agentes e Protocolos` |
| **Tipo** | Verificação integral e fechamento |
| **Objetivo** | Demonstrar em caso novo o percurso integral F0–P10 e consolidar o resultado da Ação 2.6. |
| **Estado inicial** | `HEAD_INICIAL_2.6.6 = bcc85a62fc2b8c72b4704ecd43e5e901cce39d63`, working tree limpa. 2.6.0–2.6.5 todos `Concluído`. Suíte geral no início: 404/404 PASS. |
| **Caso** | Caso de controle novo (não reaproveita estado de 2.5.6/2.6.2/2.6.3/2.6.5), nível N2, cenário agêntico, percurso F0→P10 completo com dois ciclos de P10 (sem drift / com drift e decisão humana) e um caso de teste em P8 que diverge funcionalmente sem falhar o Estúdio (resultado calculado honestamente por `piloto.py`). Ver `.projectdocs/evidencias/sprint2/2.6.6/caso-controle.md`. |
| **Testes** | `2.6.6-C01` a `2.6.6-C43` — 43 verificações. |
| **Resultado F0–P10** | **PASS** — 13/13 etapas atingidas em ordem, sem bypass. |
| **Etapas** | 13/13 declaradas, 13/13 operacionalmente executáveis. |
| **HB** | 18/18 declaradas, 18/18 estruturalmente resolvíveis, 14/18 usadas neste caso concreto (HB-04/05/06/13 não referenciadas pelo contrato — situação inalterada de D-11/2.6.4). |
| **AG** | 4/4 declarados, 4/4 mapeados, 3/4 (AG-02, AG-03, AG-04) participantes ativos; 0 com autoridade EX3/EX4 indevida. |
| **Inegociáveis** | 5/5 semanticamente satisfeitos a partir de artefato real. |
| **Portões** | 6/6 aplicáveis conformes (caso agêntico: E1, E2, E3-D, E3-E AUTORIZADO, E4, E5). |
| **Entregáveis** | 5/5 materializados e rastreáveis a arquivo real com evento e versão. |
| **Defeito encontrado** | `D-2.6.6-01` — `calibragem.py::checar_autoria()` bloqueava indevidamente `declarado_por`/`registrado_por` de agente também para `ciclo_calibragem`, contrariando o próprio contrato documentado do módulo ("o agente pode preparar um ciclo inteiro"). Detectado ao exercitar, pela primeira vez, um ciclo de calibragem com autoria de agente ponta a ponta (2.6.3 sempre usara autoria humana em suas fixtures, mesmo passando agente como `--ator`). |
| **Correção** | Nova função `checar_autoria_ciclo()`, restrita a `ciclo_calibragem`, permitindo agente em `declarado_por`/`registrado_por`; `checar_autoria()` original preservada, inalterada, para `rotina_calibragem`. A vedação de `decisao` a agente permanece garantida por `checar_decisao()`, não tocada. |
| **Reteste** | 447/447 verificações aprovadas, 0 falhas: 404 da suíte anterior (sem regressão) + 43 novas de `campo_2_6_6.py`. |
| **Achado documental (reafirmação de 2.6.5)** | Não existe script executável para gravar `classificacao_tecnologica` de P5 de forma estruturada (`hb-classificar` produz apenas texto livre). O caso de controle registra o campo diretamente, com evidência preservada; não corrigido neste pacote por não ser capacidade já especificada a implementar (pacote de verificação, não de feature nova). |
| **D-07–D-13** | D-07/D-08/D-09/D-10/D-12 permanecem `RESOLVIDO`. D-11 permanece `PARCIAL` (inalterado). **D-13 RESOLVIDO neste pacote** — percurso positivo integral F0–P10 demonstrado. |
| **Evidências** | `.projectdocs/evidencias/sprint2/2.6.6/resultado.md`, `caso-controle.md`, `matriz-f0-p10.md`, `matriz-fronteira.md`, `matriz-inegociaveis-final.md`, `matriz-portoes-final.md`, `matriz-entregaveis-final.md`, `matriz-hb-ag-final.md` |
| **Commits** | `31ffff2260f40c06a323087791cf8e17062a4ee5` — `fix(field): allow agent authorship of calibration cycle records`; `1599e51` — `test(workflow): verify full F0-P10 execution path` |
| **Estado final da Ação 2.6** | **CONFORME** quanto ao escopo executável verificável, com a ressalva já registrada e inalterada de D-11 PARCIAL (não bloqueia o fechamento — nenhuma das 4 HB sem implementação física é exigida pelo percurso executável demonstrado). |

**Indicadores após o pacote 2.6.6 (final da Ação 2.6):** etapas
operacionalmente executáveis **13/13** · HB resolvíveis **18/18** · AG
mapeados **4/4** · inegociáveis **5/5** · portões **6/6** · entregáveis
**5/5** · P10 recorrente **SIM** · proteção `registro/`/`contexto/`
**SIM/SIM** · eventos de recusa **CONFORME** · decisão de autonomia
humana **CONFORME** · decisão de recalibragem humana **CONFORME**.

**Comparação S2-BL → final da Ação 2.6:**

| Indicador | S2-BL | Final Ação 2.6 |
|-----------|-------|----------------|
| Etapas | 8/13 | 13/13 |
| P7 | ausente | operacional, decisão humana protegida |
| P10 | ausente | operacional, recorrente, dois ciclos demonstrados |
| HB referenciadas/formalizadas | 9/18, 0/18 códigos | 18/18 declaradas e resolvíveis, 14/18 com implementação física |
| AG mapeados | 0/4 | 4/4 |
| Portões | 2/6 | 6/6 |
| Inegociáveis | 0/5 | 5/5 |
| registro/ protegido | não | sim |
| eventos da máquina | parcial | completo |
| entregáveis materiais | ausentes | 5/5 |
| percurso F0–P10 | ausente | demonstrado integralmente em caso novo |

Este pacote fecha a Ação 2.6 como **CONFORME** quanto ao escopo
executável de referência descrito nesta seção. Como Ação 2.5 já estava
registrada como CONFORME, a Sprint 2 conclui a implementação de
referência do Estúdio de Trabalho para a Camada de Contexto e Dados e a
Camada de Agentes e Protocolos, dentro do escopo acadêmico definido —
não uma solução empresarial implantada, não ROI comprovado, não operação
autônoma em produção. Aguarda revisão humana antes do registro formal de
fechamento da Sprint 2 no relatório do PFC.

### 3.11 Dívidas registradas no baseline

| ID | Tipo | Síntese | Pacote previsto |
|---|---|---|---|
| D-01 | Contrato | Procedência multidimensional antiga. | 2.5.0 |
| D-02 | Implementação | Quatro objetos CTX ainda no schema anterior. | 2.5.1 |
| D-03 | Implementação | Curadoria e versionamento não são impostos pelo código. | 2.5.2 |
| D-04 | Implementação | P3d não possui `referencia_p3d`. | 2.5.3 |
| D-05 | Teste | CTX-V01–V11 ausentes. | 2.5.4 |
| D-06 | Arquitetura | P2/P3 não alimentam e P4/P5 não consomem CTX de forma executável. | 2.5.5 |
| D-07 | Contrato | Somente 8 das 13 etapas estão declaradas. | 2.6.0 |
| D-08 | Implementação | `registro/` permite escrita direta. | 2.6.1 |
| D-09 | Implementação | Recusas da máquina não produzem evento. | 2.6.1 |
| D-10 | Implementação | P7 e P10 estão ausentes. **RESOLVIDO em 2.6.3.** | 2.6.2 / 2.6.3 |
| D-11 | Rastreabilidade | HB/AG sem códigos e relações estáveis. **PARCIAL em 2.6.4** (catálogo completo; 4/18 HB sem implementação física). | 2.6.4 |
| D-12 | Implementação | Emissão autoriza, mas não materializa documentos. **RESOLVIDO em 2.6.5.** | 2.6.5 |
| D-13 | Teste | Não há percurso positivo completo F0–P10. | 2.6.6 |
| D-14 | Documentação | Referências internas preservam decisões já superadas. | Revisão documental controlada |
| D-15 | Teste / documentação | TST-01, README e script divergem na classificação interna dos 26 testes. | Revisão TST/README |

Essas dívidas representam o estado inicial e não devem ser apagadas do RTE-01 quando corrigidas. O tratamento é registrado como nova evidência, preservando a relação entre defeito, pacote, correção e reteste.

### 3.12 Registro de defeito, correção e reteste

| Campo | Regra |
|---|---|
| ID do defeito | Usar ID do baseline quando já existir; criar novo ID somente para defeito novo. |
| Detecção | Indicar pacote, teste e evidência que revelaram o defeito. |
| Causa | Registrar somente quando demonstrada; não inferir causa sem evidência. |
| Correção | Descrever a mudança executável e os arquivos afetados. |
| Commit | Registrar o commit que contém a correção. |
| Reteste | Reexecutar o teste que falhou e o controle positivo correspondente quando aplicável. |
| Regressão | Executar a suíte definida para o pacote e registrar novos desvios. |
| Estado | Fechado, parcial ou bloqueado, mantendo a evidência anterior. |

### 3.13 Integração com o relatório do PFC

O relatório do PFC utiliza o RTE-01 como fonte de síntese da implementação. Não é necessário reproduzir os logs completos no corpo do trabalho. A narrativa deve demonstrar a evolução entre baseline e estado final e selecionar evidências representativas, como crescimento de cobertura, defeitos encontrados fora da suíte inicial, recusas determinísticas, controles positivos e percurso final F0–P10.

A comparação quantitativa final deve manter o baseline original e adicionar o estado final sem reescrever os valores iniciais. A quantidade total de testes não é meta em si; o aumento deve decorrer dos requisitos e lacunas cobertos.

## 4. Condição de aceite

O EMCIA-RTE-01 está pronto para uso quando: (1) preserva o baseline S2-BL e seu commit; (2) estabelece uma convenção única de evidência por pacote; (3) diferencia evidência bruta, registro consolidado e síntese do relatório; (4) permite rastrear cada requisito até teste, defeito, correção, reteste e commit; (5) preserva resultados anteriores em vez de sobrescrevê-los; (6) diferencia teste negativo de controle positivo; (7) distingue resultado de teste de estado final do requisito; e (8) mantém separadas a verificação da implementação e a verificação do método.

Para o fechamento da Sprint 2, cada pacote executado deve possuir `resultado.md` e referência às evidências correspondentes. Defeitos do baseline e defeitos novos devem ter tratamento rastreável até o estado final ou permanecer explicitamente abertos/bloqueados.

## 5. Referências

- EMCIA-MET-01 — Documento do método.
- EMCIA-CAT-01 — Fronteira de delegação e catálogo de agentes e habilidades.
- EMCIA-CTX-01 v0.4 — Instrumento de Registro da Camada de Contexto.
- EMCIA-ROT-01 — Roteiro de Levantamento de Regras Não Documentadas.
- EMCIA-ARQ-01 — Arquitetura do Estúdio de Trabalho.
- EMCIA-IMP-01 — Plano de Implementação do Estúdio de Trabalho.
- EMCIA-ESP-01 — Especificação Executável do Estúdio de Trabalho.
- EMCIA-CAM-01 — Protocolo de Campo por Passo, P6 a P10.
- EMCIA-TST-01 — Plano de Testes da Implementação do Estúdio de Trabalho.
- EMCIA-VER-01 — Plano de Verificação do Método.
- EMCIA-TRA-01 — Procedimentos Transversais do Método.
- S2-BL — Baseline controlado da Sprint 2, execução de 18/09/2026.
- Repositório local `emcia-marketplace`, HEAD `9a54017411c20cf54ab3a28fa488678c945a34b1` no baseline.

## 6. Histórico de revisões

| Versão | Data | Autor | Descrição da alteração | Aprovação |
|---|---|---|---|---|
| 0.1 | 18/09/2026 | Celso do Vale | Versão inicial: cadeia de evidência, convenção de armazenamento, modelo de registro por pacote, baseline S2-BL, dívidas iniciais e integração com as ações 2.5 e 2.6. | — |
| 0.2 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.0, commit de implementação, testes cobertos e proveniência das evidências reconstruídas. | — |
| 0.3 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.1: quatro objetos CTX, cobertura T01–T11, regressão acumulada, commit e evidências contemporâneas. | — |
| 0.4 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.2: curadoria de `contexto/`, autoria dupla, versionamento I→V sem sobrescrita, correção do achado do baseline em `validar.py --autor` e de um defeito adicional na convenção lexical de autor-agente, cobertura T01–T17, regressão acumulada 44→61. | — |
| 0.5 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.3: taxonomia oficial de confronto (EMCIA-ROT-01 3.9), registro estruturado `contexto/divergencias/` para P3d, resolução mínima de `referencia_p3d` (CTX-V11 mínimo), versionamento estendido a mudança de `classificacao_confronto`, cobertura T01–T13, regressão acumulada 61→73. | — |
| 0.6 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.4: formalização das onze CTX-V01–CTX-V11 (oito já implementadas, três novas — resolução de referência a Termo/Entidade/Fonte), indicador CTX-V 0/11→11/11, cobertura de 23 verificações, regressão acumulada 73→96. | — |
| 0.7 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.5: P2/P3 alimentando contexto real (não só prosa), P4 instruído a consumir `quadro.py`, novo `consultar.py` para P5 com distinção D/I/V preservada, correção de defeito real em `quadro.py` (campos legitimamente vazios tratados como ausentes), indicadores P2/P3→CTX e CTX→P4/P5 todos IMPLEMENTADO, cobertura de 17 verificações, regressão acumulada 96→113. | — |
| 0.8 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.5.6: verificação consolidada da Ação 2.5 com caso de controle único (`CTX-TEST-2.5.6-001`), reexecução de 8/11 CTX-V sobre objetos novos, percurso integrado P2→CTX→P3→P4→P5 com objeto rastreável do início ao fim, nenhum defeito de produção encontrado, cobertura de 16 verificações, regressão acumulada 113→129. **Ação 2.5 encerrada CONFORME**; D-01 a D-06 todos RESOLVIDOS. | — |
| 0.9 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.0: contrato executável F0–P10 congelado no playbook (8/13→13/13 etapas), E4/E5 corrigidos e `portao_pendente` removido, condição de E3-E convertida em estrutura declarativa, inegociável 1 corrigido contra MET-01 3.4.3, pendência de correspondência entregável×passo resolvida por EMCIA-CAM-01/ESP-01 (`decisoes/013`), checagens estruturais genéricas novas em `playbook.py`, cobertura de 29 verificações (24 positivas + 5 negativas), regressão acumulada 129→158. Nenhum comportamento de P6–P10 implementado. **D-07 tratado**; início da Ação 2.6, aguardando 2.6.1. | — |
| 0.10 | 18/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.1: núcleo genérico de protocolos fortalecido sem hard-code EMCIA (0 ocorrências comportamentais). Corrige defeito real do baseline `2.6-BL12` (`avancar.py --encerrar` não verificava etapa corrente — reproduzido e corrigido). Adiciona `--registrar-recorrencia` (cadência/responsável nominal), `--satisfazer-inegociavel` (caminho autorizado, substitui booleano mágico de `2.6-BL26`), G5 em `guarda.py` (protege `registro/`, `2.6-BL17`/`D-08`), eventos `RecusaMaquina`/`RecusaEmissao` em todo caminho de recusa (`2.6-BL15`/`D-09`), validação estrutural de condição declarativa e mecanismo isolado de `criterio_de_verificacao` (integração com HB/AG real adiada para 2.6.4, por decisão explícita). Cobertura de 39 verificações, regressão acumulada 158→197. **D-08 e D-09 tratados**; aguardando 2.6.2. | — |
| 0.11 | 19/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.2: P6 (`registro/operacional/`, estados proposta→validado) e P7 (`registro/governanca/autonomia/`, estados rascunho→proposto→decidido) implementados inteiramente em `eiac-campo/scripts/`, reaproveitando primitivas genéricas do núcleo sem introduzir semântica de método nele (hard-code EMCIA no núcleo: 0 comportamental). Fronteira agente×humano aplicada estruturalmente: agente prepara, só humano nomeado decide/valida, decisão de agente sempre recusada com evento. Corrige defeito pré-existente descoberto durante a implementação — `guarda.py` G1 bloqueava skill EX3/EX4 mesmo com sessão humana registrada. Caso de controle `PP-TEST-2.6.2-001` demonstra o percurso completo P5→P6→P7→evidência para o inegociável 2, sem declarar E4 emitido em definitivo. Cobertura de 38 verificações, regressão acumulada 197→235. **D-10 parcialmente resolvido** (parte P7; P10 pendente para 2.6.3). | — |
| 0.12 | 19/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.3: P8 (`registro/piloto/`, estados rascunho→revisado), P9 (`registro/metricas/`, estados planejada→apurada) e P10 (`registro/calibragem/`, rotina + ciclos) implementados inteiramente em `eiac-campo/scripts/`, reaproveitando primitivas genéricas do núcleo — incluindo `avancar.registrar_recorrencia`/`avancar.satisfazer_inegociavel`, já genéricas desde 2.6.1 — sem alterar `eiac-nucleo/` (hard-code EMCIA no núcleo: 0 comportamental; núcleo intocado neste pacote). Fronteira agente×humano aplicada estruturalmente em P10: agente detecta drift e recomenda, só humano nomeado decide recalibrar/expandir/descontinuar, decisão de agente sempre recusada com evento. Corrige defeito introduzido e resolvido dentro do próprio pacote — `calibragem.py` inicialmente recusava complementar um ciclo pendente (drift sem decisão) com a decisão humana no mesmo identificador. Caso de controle `caso-controle-2-6-3` demonstra o percurso completo P7→P8→P9→P10→dois ciclos (sem e com drift)→decisão humana→evidências para os inegociáveis 3, 4 e 5, sem declarar E5 emitido. Cobertura de 57 verificações, regressão acumulada 235→292. **D-10 resolvido** (P7 e P10 ambos conformes). | — |
| 0.13 | 19/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.4: as 18 HB e os 4 AG formalizados como catálogo declarativo (`eiac-campo/reference/habilidades.json`, `agentes.json`), extraídos literalmente de EMCIA-CAT-01 Anexo A, com resolução genérica em novo `eiac-nucleo/scripts/catalogo.py` — não conhece nomes/semântica EMCIA, só objetos `capacidade`/`papel` com `id`, reaproveitando `playbook.capacidade_valida()` (2.6.1/ESP-01 G6). Relação HB↔etapa extraída exclusivamente de `playbook.json`, nunca por inferência textual entre documentos (preserva a pendência aberta sobre correspondência entregável×passo). 5 skills ganharam `hb:` no frontmatter, somando 9/18 com identidade rastreável. Nenhum arquivo físico de agente novo criado — os 4 AG lógicos resolvem sobre os 2 subagents e as skills de etapa já existentes. Nenhum defeito de produção encontrado. Cobertura de 50 verificações, regressão acumulada 292→342. **D-11 parcial** (catálogo completo; 4/18 HB sem implementação física, 9/18 skills sem `hb:` — infraestrutura/não catalogada, não faltante). | — |
| 0.14 | 19/09/2026 | Celso do Vale | Registro efetivo do pacote 2.6.5: os cinco inegociáveis passam a ser verificados semanticamente a partir de artefato real (`eiac-campo/scripts/inegociaveis.py`, cinco verificadores puros), nunca de flag solta — `avancar.py --satisfazer-inegociavel` só é chamado após verificação. Novo domínio `registro/baseline/` para o inegociável 1 (sem schema/ID dedicado em nenhuma fonte oficial; `BL-nnn` é convenção técnica do Estúdio, decisão tomada explicitamente com o usuário), `metrica.py` ganha `baseline_ref` para P9 reutilizar a mesma linha de base de I1. `eiac-nucleo/scripts/avancar.py::emitir()` passa a distinguir `NAO_APLICAVEL` (E3-E sobre caso não agêntico, exit 0, evento `EntregavelNaoAplicavel`) de `NEGADO`, e ganha `--materializar <arquivo>`: só registra `EntregavelEmitido` se o artefato existir e não estiver vazio, com versão rastreável em `estado.entregaveis_emitidos`. Novo `eiac-campo/scripts/entregaveis.py` renderiza `caso/entregaveis/E1-E5.md` a partir dos artefatos reais do caso, recusando materializar campo obrigatório sem evidência (nunca inventa). `E3` permanece um único entregável ao cliente, consolidando `E3-D` (sempre) e `E3-E` (condicional) no mesmo arquivo. Caso de controle F0→E5 completo, cenário agêntico, cinco inegociáveis e seis portões demonstrados com evidência real. Um erro de nome de campo introduzido no próprio pacote (`entregaveis.py::render_e5`) foi encontrado e corrigido antes do commit. Cobertura de 62 verificações, regressão acumulada 342→404. **D-12 resolvido.** Aguarda revisão humana antes de iniciar 2.6.6. | — |
