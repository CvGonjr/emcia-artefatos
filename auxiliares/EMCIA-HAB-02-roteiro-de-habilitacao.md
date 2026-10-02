# Roteiro de habilitação — perguntas e ações do engenheiro de campo

**Documento de apoio · EMCIA-HAB-02 (identificador provisório) · setembro de 2026**
**Base:** EMCIA-HAB-01, Protocolo de habilitação
**Quando usar:** antes de qualquer etapa do método, a partir do primeiro contato com a organização

A habilitação decide se o percurso começa. Ela não é calibrada por nível e se aplica igual a toda organização. O plugin oferece `/eiac-campo:habilitacao <expediente>` para o registro administrativo anterior ao caso. O engenheiro inicializa o expediente fora de repositórios e da sessão do agente; o material é importado para o caso na etapa 0d. Consulte a referência técnica `eiac-campo/reference/habilitacao.md` para os formatos de entrada.

---

## Operação com formulário e assinatura

Use o fluxo de `EMCIA-HAB-fluxo-operacional-proposta.md`: coleta administrativa → revisão humana → rodadas de esclarecimentos → consolidação → revisão das minutas → PDFs → assinatura pelo painel escolhido pelo cliente → conferência → 0c → 0d.

A exceção administrativa aprovada está em EMCIA-HAB-01, seção 3.7. Antes de consultar respostas pelo MCP, registre as condições de tratamento e sua evidência. Não processe dados operacionais antes de 0d. Reserve o identificador do futuro caso, sem apresentá-lo como aberto.

O plugin preserva a origem dos campos e versões dos três documentos. O engenheiro confere a carta atual e o conteúdo dos PDFs antes de liberá-los. Cliente e engenheiro combinam quem opera o painel e recolhe arquivos assinados e comprovantes. Não há integração com o serviço de assinatura. Registre a conferência humana das assinaturas antes de concluir 0b.

## Os quatro pré-requisitos

A falta de qualquer um impede o início do percurso.

| # | Pré-requisito | Pergunta de verificação |
|:-:|---|---|
| 1 | Patrocinador com autoridade sobre o processo | Quem decide sobre este processo e pode assinar as decisões dos passos 4, 7 e 9? |
| 2 | Executor liberado para sessão presencial | Quem executa o processo no dia a dia, e essa pessoa pode passar algumas horas conosco, presencialmente? |
| 3 | Autorização escrita de acesso a dado e documento | Quem autoriza por escrito o acesso aos dados e documentos do processo? |
| 4 | Processo delimitado | Qual processo, com início e fim claros, será tratado? |

---

## Etapa 0a — Qualificação do contato

**Objetivo:** saber se existe um engajamento possível antes de formalizar qualquer coisa.

**Perguntas ao interlocutor**

1. Qual processo vocês querem tratar? Onde ele começa e onde termina?
2. Qual é o problema concreto nesse processo hoje? O que dá errado, atrasa ou custa caro?
3. Você decide sobre esse processo? Se não, quem decide?
4. Quem executa esse processo no dia a dia? Quantas pessoas?
5. Existem documentos, planilhas ou sistemas que registram esse processo?
6. Vocês estariam dispostos a dar acesso a esses dados e documentos e a liberar quem executa o processo para conversar conosco?

**Ações do engenheiro**

- [ ] Levantar informação pública sobre a organização e o setor. Guardar numa pasta **fora** do caso; esse material só entra no caso depois da 0d, com marca `I · tipo_fonte: externa`.
- [ ] Nomear um único processo candidato.
- [ ] Redigir o registro de contato qualificado: interlocutor, cargo, processo candidato, disposição de acesso.

**Passa se:** há interlocutor com autoridade e um processo delimitado.

**Não passa se:** a demanda é "usar IA na empresa", sem processo, ou o interlocutor não decide sobre o processo que descreve. Isso não é rejeição do cliente: sem processo, não há o que enquadrar.

---

## Etapa 0b — Formalização do escopo

**Objetivo:** registrar por escrito o que o trabalho cobre, o que não cobre e como a informação circula.

**Perguntas para fechar a formalização**

1. Quem tem competência para assinar a carta de escopo e o acordo de confidencialidade?
2. Vocês autorizam a gravação das sessões de levantamento?
3. Vocês autorizam que documentos e dados do processo sejam processados por um modelo de IA de terceiro? Qual provedor e qual localização de processamento são aceitáveis?
4. Há dado pessoal ou sensível no processo? Que regra de anonimização precisa ser seguida?
5. Está claro que o serviço entrega diagnóstico e especificação, e não implanta, não integra sistemas e não opera a solução?

**Ações do engenheiro**

- [ ] Emitir a carta de escopo com o processo-alvo, as fases F0 a F4, os cinco entregáveis e o limite do serviço.
- [ ] Firmar o acordo de confidencialidade.
- [ ] Obter o termo de consentimento para gravação das sessões e uso do dado, incluindo o provedor de modelo que será usado.

**Passa se:** os três documentos estão assinados por quem tem competência.

**Não passa se:** a organização exige implantação, ou recusa a gravação das sessões. Sem gravação, não há como demonstrar quem disse cada regra.

---

## Etapa 0c — Concessão de acesso

**Objetivo:** transformar a autorização escrita em acesso efetivo.

**Perguntas ao patrocinador**

1. Quem será o patrocinador nomeado do trabalho, com nome e cargo?
2. Quem será o executor que participará da sessão presencial? Em que data?
3. A que dados, sistemas e documentos teremos acesso? Leitura direta ou amostra exportada?
4. De que período é a amostra? Ela representa o processo normal ou um período atípico?
5. O que **não** poderá ser acessado, e por quê?

**Ações do engenheiro**

- [ ] Registrar o nome do patrocinador e do executor.
- [ ] Reservar a data da sessão presencial do passo 3. Este é o ponto mais frágil do cronograma.
- [ ] Receber a documentação do processo. **Não processar nada no Claude Code antes da 0d.**
- [ ] Montar a matriz de acessos:

| Item | Concedido | Negado | Restrição aplicada | Motivo |
|---|---|---|---|---|
| | | | | |

**Passa se:** patrocinador e executor nomeados, data reservada e ao menos uma fonte acessível.

**Não passa se:** nenhum acesso a dado é concedido, ou o executor não é liberado para a sessão presencial.

Registre o que foi negado com o mesmo cuidado que o concedido. É isso que permite separar, no final, uma lacuna do diagnóstico de uma falha do método.

---

## Etapa 0d — Abertura do caso

**Objetivo:** preparar o ambiente antes de processar dados operacionais do cliente. Informações administrativas anteriores seguem EMCIA-HAB-01, seção 3.7.

**Ações do engenheiro** (comandos no passo a passo do engenheiro, Parte B4)

- [ ] Criar o caso com `novo-caso.sh`.
- [ ] Copiar os documentos do método para `metodo/`.
- [ ] Colocar a documentação recebida em `fontes/`, com nomes estáveis e datados, e os artefatos da habilitação em `fontes/habilitacao/`.
- [ ] Conferir o estado do caso com `/eiac-nucleo:estado`.
- [ ] Rodar os testes de trava dentro do caso e conferir `registro/eventos.jsonl`.
- [ ] Gravar o desfecho da habilitação em `caso/00-habilitacao.md`, com marca de procedência em cada linha.
- [ ] Selar o caso.

**Passa se:** o estado inicial está selado e o validador de procedência está ativo.

Esta etapa não tem recusa. Se algo falhar, repita.

---

## Desfecho

| Desfecho | Quando | O que acontece |
|---|---|---|
| **Prosseguir** | Os quatro pré-requisitos estão satisfeitos e nenhum acesso essencial foi negado | F0 começa |
| **Prosseguir com restrição** | Os pré-requisitos estão satisfeitos, mas há acesso negado | O percurso segue, e a restrição aparece em cada entregável, no item afetado |
| **Não prosseguir** | Falta ao menos um pré-requisito | O trabalho não começa. A organização recebe o registro do que precisa mudar |

A restrição nunca vira ressalva genérica no fim do relatório. Ela acompanha o item que ficou sem verificação.

**Modelo para `caso/00-habilitacao.md`:**

```text
- [V · documento: habilitacao/carta-de-escopo-AAAA-MM.pdf · AAAA-MM-DD · <engenheiro>]
  Carta de escopo, confidencialidade e consentimento assinados por <nome, cargo>.
- [D · <patrocinador> · AAAA-MM-DD]
  Patrocinador: <nome, cargo>. Executor: <nome>, sessão presencial em AAAA-MM-DD.
- [V · documento: habilitacao/matriz-de-acessos-AAAA-MM.xlsx · AAAA-MM-DD · <engenheiro>]
  Acesso concedido a <item>; negado a <item> (<motivo>).
- [D · <engenheiro> · AAAA-MM-DD]
  Desfecho: <prosseguir | prosseguir com restrição | não prosseguir>.
```

---

## Durante o percurso: perda de pré-requisito

Se o patrocinador sair, o executor for realocado ou um acesso for revogado:

1. Suspenda o percurso e registre a data e a causa no diário de campo.
2. Volte à etapa 0c e substitua o pré-requisito perdido.
3. Só retome depois da substituição registrada.

Retomar sem substituir produz entregável sem autoridade. Um termo de autonomia assinado por um patrocinador que saiu não vincula ninguém.
