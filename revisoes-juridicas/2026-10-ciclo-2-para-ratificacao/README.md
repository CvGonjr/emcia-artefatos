# Ciclo 2 — minutas para ratificação jurídica

Responsável: Celso do Vale. Data: 05/10/2026. Estado: Em revisão. Aprovação: pendente.

## 1. Objeto do envio

Minutas HAB-02 e HAB-03 v0.3, redigidas conforme o parecer de 05/10/2026 e as decisões do engenheiro. O HAB-03 passa a se denominar Termo de Autorização Operacional e Governança de Dados; seu Anexo I (DPA) é vinculante e integra a mesma assinatura. As gravações são retidas até o encerramento do caso, por decisão expressa do engenheiro.

As cópias de leitura em Markdown e PDF preservam a identificação do caso e todo o texto contratual, inclusive o DPA, sem o controle interno do modelo, o bloco Revisão jurídica ou o histórico do modelo. Os placeholders permanecem visíveis porque são minutas de modelo, sem dados de cliente. O aviso de minuta para ratificação identifica sua finalidade e não representa aprovação ou emissão para assinatura.

**Pendência expressa:** o item de treinamento por terceiros da matriz do parecer ainda depende da verificação dos termos comerciais pelo engenheiro. A ausência de compromisso de não uso para treinamento é decisão do engenheiro submetida à ratificação, e não atendimento integral daquele item. Ver [quadro de correspondência](quadro-de-correspondencia.md), item M7, e [pendências por provedor](../pendencias-ciclo-2.md).

## 2. Identificação por hash

A ratificação deve identificar os hashes dos templates originais v0.3. Os hashes das cópias sem elementos internos e dos PDFs permitem conferir o material de leitura. Solicitar ao revisor a vinculação expressa entre o texto examinado e o hash do template correspondente. Se houver qualquer mudança de cláusula depois deste envio, revisar a versão, gerar novas cópias e recalcular os hashes antes da ratificação.

| Documento | Artefato | Arquivo | SHA-256 |
| :--- | :--- | :--- | :--- |
| HAB-02 v0.3 | Template original | [Fonte canônica](../../auxiliares/HAB-02-acordo-confidencialidade.md) | 45aa3e33334bce97a197bb5f99a16e8b7828ebd3315b735cf59e3960c990fa3f |
| HAB-02 v0.3 | Markdown para leitura | [HAB-02-acordo-confidencialidade.md](HAB-02-acordo-confidencialidade.md) | 9646eddc5e07ceaae5db9fd607e9b27d87e8fc39770001cd71695a0a77357f79 |
| HAB-02 v0.3 | PDF para leitura | [HAB-02-acordo-confidencialidade.pdf](HAB-02-acordo-confidencialidade.pdf) | 9634f1379097aa26dbb9c05a04a7b19dce2d305b67c5c7d9187040e058d0a610 |
| HAB-03 v0.3 | Template original | [Fonte canônica](../../auxiliares/HAB-03-termo-de-autorizacao-e-governanca-de-dados.md) | 285f5b91fb58981d7f2d0260ece55f41ec1e4215abaca77081df1fa936500ba0 |
| HAB-03 v0.3 | Markdown para leitura | [HAB-03-termo-de-autorizacao-e-governanca-de-dados.md](HAB-03-termo-de-autorizacao-e-governanca-de-dados.md) | d0cc0a117ab995fc9bb75369f2afd00c398764330e95f22c3ca1a31cff9eaa56 |
| HAB-03 v0.3 | PDF para leitura | [HAB-03-termo-de-autorizacao-e-governanca-de-dados.pdf](HAB-03-termo-de-autorizacao-e-governanca-de-dados.pdf) | d3b8c7ecb1dca2d7694ad04ae6662f4ea4908124c5ec11d8d4090c71307990af |

Os mesmos valores estão em [hashes.json](hashes.json). O [parecer do ciclo 1](../2026-10-05-ciclo-1/parecer.pdf) permanece sem edição, SHA-256 `1ed5168e9e3f41dd01964c7bd21f8212404854ef6617b30dccbf28cade508fe1`.

## 3. Correspondência e próximos atos

- [Quadro de correspondência](quadro-de-correspondencia.md): oito itens da matriz do parecer, demais pontos do diagnóstico e decisões aplicadas, com cláusulas de destino e pendência de treinamento explicitada.
- [Pendências do ciclo 2](../pendencias-ciclo-2.md): verificações comerciais de Tally, Google e Anthropic e campos sugeridos, sem novos placeholders.
- [Registro dos ciclos](../README.md): versões e hashes examinados no ciclo 1, resultado condicionado e regra de ratificação sem condição.

O parecer condicionado não libera geração para cliente. Somente ratificação sem condição sobre os hashes exatos, seguida de aprovação documental e nova linha de base aprovada, permite a implantação. Nenhuma aprovação ou tag foi criada nesta tarefa. O APR-01 e a tag metodo-v1.0 permanecem intactos.

## 4. Geração das cópias e conferência

A transformação das cópias usou as funções existentes documento_cliente e pdf_bytes de eiac-campo/scripts/habilitacao.py, no marketplace commit 148aca4c70e856d91ee32174aa852c109595826c. Primeiro foi retirado o conteúdo interno por seus delimitadores; em seguida foi acrescentado o aviso de minuta para ratificação, padronizado o final do arquivo com uma única quebra de linha e convertido o Markdown em PDF por Google Chrome. A geração foi uma conversão local para leitura pelo revisor, sem expediente de cliente ou operação gerar, que exige aprovação por hash no APR-01. Nenhum script do marketplace foi alterado.

Conferências realizadas antes dos commits das minutas:

| Conferência | Resultado |
| :--- | :--- |
| testes/negativos.sh e testes/contexto.py antes das mudanças | Todas as travas passaram; 11 testes estruturais passaram |
| testes/habilitacao.py, Python 3.12.12 | 29 testes passaram contra os templates aprovados da tag, preservados nas fixtures do marketplace |
| manual_a25.py contra o MAN-01 v1.1, Python 3.12.12 | Conferir() retornou lista vazia; 5 testes passaram, incluindo os quatro negativos, com o caminho do manual alterado somente em memória |
| Placeholders das minutas | Mesmos conjuntos de campos dos templates v0.2; nenhum placeholder novo |
| Delimitadores internos | documento_cliente aceitou os dois templates v0.3 e recusou separadamente a ausência das marcas de controle, identificação e histórico |
| Identificação e texto contratual | Identificação preservada byte a byte na transformação; seções contratuais e DPA completos nas cópias |
| Texto extraído dos PDFs por pdftotext | Sem Controle do modelo, Revisão jurídica, histórico do modelo ou aprovação nominal interna; identificação, cláusulas finais e Anexo I presentes |
| Inspeção visual | Primeira página do HAB-02 e última do HAB-03 conferidas, com texto, identificação e tabelas legíveis; PDFs de 5 e 9 páginas, respectivamente |
| Integridade | PDF recebido, APR-01 e HAB-01 preservados; linhas históricas anteriores preservadas; hashes das cópias conferidos |

A compatibilidade estrutural da transformação não equivale à liberação do gerador. Seu TEMPLATES ainda usa o nome antigo de HAB-03 e os hashes aprovados v0.2. A nova implantação dependerá de ratificação jurídica, aprovação documental, nova linha de base e atualização controlada no marketplace; essa incompatibilidade está registrada nas pendências do ciclo 2.

## Histórico

| Data | Autor | Registro |
| :--- | :--- | :--- |
| 05/10/2026 | Celso do Vale | Minutas 0.3 para ratificação, cópias sem controle interno, hashes e quadro de correspondência; sem aprovação ou tag |
