# Habilitação — proposta de fluxo com Tally e assinatura

**Estado:** fluxo com implementação inicial no `eiac-campo`; decisões operacionais registradas abaixo e incorporadas ao protocolo na seção 3.7.  
**Data:** 25/09/2026.  
**Base:** EMCIA-HAB-01, roteiro EMCIA-HAB-02 e templates HAB-01, HAB-02 e HAB-03.  
**Decisões humanas recebidas nesta sessão:** exceção para informações administrativas antes de 0d; reserva do identificador do futuro caso; assinatura pelo painel escolhido pelo cliente, sem integração; manutenção da carta com revisão humana obrigatória. Nenhuma autoria nominal é presumida.

## 1. Fluxo proposto

Cliente responde ao formulário → engenheiro revisa → havendo dúvidas, prepara uma rodada de esclarecimentos → cliente responde → engenheiro resolve ou reabre cada pendência → informações consolidadas → minutas dos três documentos → revisão humana → assinatura das partes → conferência das evidências → acesso efetivo (0c) → abertura e selo (0d) → F0.

O “ok” do engenheiro encerra a revisão das informações. Não equivale a assinatura, concessão de acesso ou conclusão da habilitação. Cada passagem conserva os critérios do protocolo.

O cliente interage com formulários e pessoas. O agente auxilia o engenheiro, conforme a decisão 008 do marketplace. Publicar perguntas e encaminhar documentos exige revisão do engenheiro; respostas nunca autorizam o agente a decidir pelo cliente.

## 2. Coleta inicial e esclarecimentos

O formulário inicial reúne declarações sobre 0a, condições de formalização e disponibilidade futura de acesso. Perguntas sobre 0b e 0c não significam que essas etapas foram cumpridas. Não solicitar credenciais, bases de dados ou documentos operacionais nesta coleta.

Antes de existir caso, usar um identificador de habilitação. Manter o expediente fora dos repositórios da ferramenta e do método. Na abertura, registrar a correspondência entre esse identificador e o identificador do caso.

Para cada resposta, conservar identificação do formulário e da submissão, versão das perguntas, data de recebimento, respondente declarado e cópia original. O nome declarado não é prova de identidade nem de competência para assinar. A consolidação deve apontar para as respostas de origem; não substituir os originais.

Cada pendência contém:

| Campo | Conteúdo |
|---|---|
| Identificação | Habilitação, rodada e identificador estável da pendência |
| Origem | Pergunta e resposta que motivaram a dúvida |
| Esclarecimento | Pergunta objetiva aprovada pelo engenheiro |
| Efeito | Etapa ou documento impedido enquanto não for resolvida |
| Resposta | Submissão, respondente declarado e data |
| Decisão | Aberta, respondida, resolvida ou reaberta; motivo, pessoa responsável e data |

Criar um formulário de esclarecimentos por habilitação e rodada, contendo apenas as pendências daquela rodada. Conservar as versões anteriores. Uma resposta nova não apaga a anterior; divergências ficam explícitas para decisão humana. Várias pendências podem ser respondidas no mesmo formulário.

O vínculo entre formulário, rodada e habilitação deve ser conferido no registro interno. Um identificador em URL ou campo oculto não autentica o respondente. Resposta duplicada não gera segunda transição; resposta de rodada antiga não encerra pendência atual automaticamente.

Ausência de resposta mantém o expediente aguardando. Recusa explícita de requisito produz registro com causa e condição necessária para retomada. Nenhuma negativa é silenciosa.

## 3. Preparação dos documentos

Após qualificação em 0a e resolução das pendências que afetam a formalização, preencher os templates existentes. Não inventar informações ausentes.

| Documento | Conteúdo a consolidar |
|---|---|
| HAB-01 — Carta de escopo | Organização, processo e limites, participantes, escopo, entregáveis e restrições |
| HAB-02 — Confidencialidade | Partes, finalidade, informações abrangidas e condições de tratamento |
| HAB-03 — Consentimento | Autorizações de gravação, fontes, processamento por IA, ambientes permitidos e restrições |

Separar dados declarados pelo cliente, decisões registradas pelo engenheiro e cláusulas do template. Todo campo preenchido deve ter origem recuperável. Campos desconhecidos impedem finalizar a minuta quando necessários ao compromisso; não usar “não se aplica” por suposição.

Conferir signatários por documento: a pessoa que responde, o patrocinador e a pessoa competente para assinar podem ser diferentes. Os templates atuais também preveem assinatura da parte EMCIA. Conferir a revisão jurídica já exigida pelo HAB-02 antes do uso contratual.

## 4. Assinatura como etapa própria de 0b

Gerar os três documentos finais em PDF, revisar e congelar suas versões, encaminhá-los para assinatura e recolher os arquivos assinados com as evidências disponíveis.

**Orientação operacional confirmada:** começar apenas pelo painel da ferramenta de assinatura, sem integração com o plugin. O cliente pode escolher a ferramenta em cada engajamento. Não há fornecedor obrigatório. Essa escolha não resolve as demais decisões de método pendentes.

### Operação inicial pelo painel

1. O plugin prepara os documentos e o engenheiro revisa os PDFs finais e os signatários exigidos.
2. O cliente indica a ferramenta. Cliente e engenheiro combinam quem operará o painel e recolherá os arquivos finais.
3. A pessoa responsável pela operação carrega os PDFs revisados no painel, cadastra os signatários e encaminha a solicitação de assinatura.
4. As partes assinam pela ferramenta escolhida. O acompanhamento de pendências, recusas e prazos é manual.
5. A pessoa responsável baixa os documentos assinados e os comprovantes ou relatórios disponíveis e os entrega ao engenheiro.
6. O engenheiro confere as evidências e registra os arquivos e o resultado da conferência no expediente de habilitação, pelos mecanismos autorizados. O controle de 0b usa esses registros.

Nesta versão, o plugin não acessa o serviço de assinatura por API ou MCP, não recebe webhooks e não consulta automaticamente o andamento. Sua responsabilidade é preparar os documentos e registrar o retorno e a conferência humana. Uma integração futura depende de escopo próprio; não é condição para operar a habilitação.

A ferramenta escolhida deve permitir recolher os três documentos finais com as assinaturas exigidas e evidências suficientes para a conferência descrita abaixo. A escolha do fornecedor não dispensa essas condições.

O método deve exigir evidência, sem depender de um fornecedor específico. Para cada documento registrar:

- código e versão do template; versão e hash do PDF encaminhado;
- pessoas e papéis exigidos para assinatura, com competência conferida pelo engenheiro;
- identificador da solicitação ou envelope, quando houver;
- estado por signatário: aguardando, assinado, recusado, expirado ou cancelado;
- arquivo final assinado, hash próprio e comprovante ou relatório de assinatura disponível;
- data, pessoa e resultado da conferência, incluindo vínculo entre versão enviada e versão assinada.

Não exigir igualdade entre o hash do PDF enviado e o do PDF assinado: a assinatura pode modificar o arquivo. Guardar ambos e conferir sua vinculação. Um status de fornecedor, isoladamente, não substitui o documento final nem a conferência.

O registro do engenheiro de que o cliente aceitou continua sendo testemunho, conforme a decisão 008; não constitui por si a assinatura.

**Passagem de 0b:** todos os documentos exigidos estão na versão vigente, assinados pelas pessoas competentes e com evidência conferida. Falta de assinatura, recusa, expiração, signatário divergente ou conteúdo alterado mantém a etapa pendente ou registra a recusa pertinente.

Se o conteúdo mudar após envio, cancelar ou substituir a solicitação e emitir nova versão para assinatura. Preservar a anterior como histórico. Mudança após assinatura exige nova formalização do conteúdo afetado antes de utilizá-lo.

### Alternativa: assinatura no Tally

O Tally oferece assinatura eletrônica simples, conserva a assinatura como imagem e permite exportar a submissão assinada em PDF. Isso foi confirmado na [documentação oficial](https://tally.so/help/electronic-signatures), consultada em 25/09/2026.

Essa capacidade não comprova, sozinha, o fluxo exigido para estes três documentos e ambas as partes. Para adotá-la, demonstrar que o conteúdo integral e a versão de cada documento estão vinculados ao ato de assinatura, que todas as partes exigidas assinam e que as evidências podem ser preservadas e conferidas. Não colar uma imagem de assinatura em um documento gerado posteriormente.

A escolha da modalidade e sua adequação contratual ficam pendentes de decisão humana. A existência do campo de assinatura não resolve essa escolha.

## 5. Acesso e abertura

Somente depois de 0b concluída, confirmar em 0c patrocinador, executor liberado, agenda reservada e acesso efetivo a pelo menos uma fonte do processo. Registrar acesso concedido, negado, motivo e restrição por item. Declaração de disponibilidade no formulário não comprova acesso efetivo.

Em 0d, abrir o caso, conservar em `fontes/habilitacao/` os originais pertinentes e importar pelos mecanismos autorizados do caso. Preservar origem, datas e vínculo com o expediente anterior. Classificar procedência segundo as regras vigentes, sem converter automaticamente respostas em verificação.

Registrar o desfecho e selar o estado inicial antes de F0. Uma falha técnica em 0d é registrada e corrigida com repetição da etapa. A restrição nunca dispensa um dos quatro pré-requisitos; acompanha o item afetado nos entregáveis. Perda superveniente de pré-requisito suspende o percurso conforme o protocolo.

## 6. Decisões recebidas e limite documental

1. **Processamento anterior a 0d — aprovado:** somente informações administrativas, em expediente separado, com origem e condições de tratamento previamente registradas. O protocolo incorpora essa exceção na seção 3.7. Dados operacionais continuam aguardando 0d.
2. **Conteúdo da carta — manter com revisão humana:** o usuário decidiu manter o template atual e exigir revisão humana antes da emissão. A divergência de conteúdo permanece explícita; o agente não altera fases, entregáveis ou limites por inferência.
3. **Identificador antes do caso — aprovado:** reservar o identificador do futuro caso e indicar nos documentos que ele ainda não foi aberto.

## 7. Implementação e verificação

Ajuste editorial futuro no formulário publicado: esclarecer que o envio inicia revisão e pode gerar esclarecimentos, formalização e assinatura. Identificar as perguntas de 0c como disponibilidade declarada. Incluir campos específicos para condições de gravação e ambientes de IA permitidos quando necessários; não presumir autorização irrestrita a partir de “sim”.

O roteiro agora remete ao ciclo de rodadas, à preparação de minutas e à conferência de assinatura. Os templates permanecem intactos: o componente registra o controle ampliado no expediente e acrescenta aos documentos gerados a versão de emissão e o aviso de identificador reservado. O procedimento permanece nos documentos do método; o comando apenas remete a eles e documenta a interface técnica. O núcleo não foi alterado.

Antes de automatizar, demonstrar os casos negativos: resposta incompleta; resposta conflitante; rodada incorreta; duplicação; pessoa sem competência; assinatura parcial; versão substituída; recusa; expiração; documento final ausente; acesso apenas prometido; tentativa de F0 antes do selo. Cada negativa precisa deixar registro com pessoa responsável nomeada, data e motivo. Passagem e procedência devem ser verificadas por regras determinísticas sobre registros estruturados, nunca por julgamento do modelo.

**Implementação inicial:** comando `eiac-campo:habilitacao` e script `habilitacao.py`, com expediente separado, condições administrativas, fontes, rodadas, revisão humana, geração de Markdown/PDF, assinatura externa e conferência de prontidão para 0d. O protocolo e o roteiro foram atualizados nas decisões expressamente aprovadas. Formulários publicados e templates HAB não foram alterados; submissões de clientes não foram consultadas. Abertura, importação e selo continuam pelos mecanismos existentes; o script não abre caso nem libera F0.


**Verificação da implementação:** 19 testes do expediente aprovados, além das suítes obrigatórias e das suítes do campo 2.6.2 a 2.6.6. Geração real dos três PDFs verificada com Chrome, templates canônicos e dados exclusivamente sintéticos. A automação não foi executada sobre submissões reais nem alterou formulários publicados.
