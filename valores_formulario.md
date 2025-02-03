
Lista de valores disponíveis que podem ser utilizados para preenchimento dinamico de um formulário/processo/anexo/email/descricao/observacoes

[[DIA]]: 18

[[ANO]]: 2023

[[HOJE]]: 18/07/2023

[[HOJE_EXTENSO]]: 18 de julho de 2023

[[HOJE_EXTENSO_MA]] : 18 DE JULHO DE 2023

[[HOJE_EXTENSO_COM_SEMANA]]: terça-feira, 18 de julho de 2023

[[HOJE_EXTENSO_COM_SEMANA_MA]]: TERÇA-FEIRA, 18 DE JULHO DE 2023

[[HOJE_EXTENSO_COM_SEMANA_1MA]]: Terça-feira, 18 de julho de 2023

[[MES]]: julho

[[MES_MA]]: JULHO

[[MES_1MA]]: Julho

[[DIA_DA_SEMANA]]: terça-feira

[[DIA_DA_SEMANA_MA]]: TERÇA-FEIRA

[[DIA_DA_SEMANA_1MA]]: Terça-feira

[[LINK_SEI("145666")]]: 1

[[LINK_SEI_RELACIONADO("CGM:")]]: Link

[[DOC_GERADO.nomeAnexo]]: Despacho Administrativo

[[DOC_GERADO.numeroAnexo]]: 39

[[LISTA]]: cria uma lista simples conforme abaixo:

NFS-e 1642745 (1423422)

NFS-e 1649292 (1423423)

NFS-e 1658087 (1423424)

NFS-e 1658098 (1423425)

NFS-e 1658110 (1423426)

[[LISTA_COM_MARCADORES]]: cria uma lista com marcadores conforme abaixo:

* NFS-e 1642745 (1423422);

* NFS-e 1649292 (1423423);

* NFS-e 1658087 (1423424);

* NFS-e 1658098 (1423425);

* NFS-e 1658110 (1423426);

[[LISTA_NUMERADA]]:  cria uma lista numerada conforme abaixo:

1. NFS-e 1642745 (1423422);

2. NFS-e 1649292 (1423423);

3. NFS-e 1658087 (1423424);

4. NFS-e 1658098 (1423425);

5. NFS-e 1658110 (1423426);

[[LISTA_POR_EXTENSO_REDUZIDA]]:  cria uma lista com os itens escritos por extenso conforme abaixo, nesse caso é removido o tipo do documento mantendo somente o número do documento e o número de pesquisa:

1642745 (1423422), 1649292 (1423423), 1658087 (1423424), 1658098 (1423425) e 1658110 (1423426)

[[LISTA_POR_EXTENSO_COMPLETA]]: cria uma lista com os itens escritos por extenso conforme abaixo, com o tipo, o número do documento e o número de pesquisa:

NFS-e 1642745 (1423422), NFS-e 1649292 (1423423), NFS-e 1658087 (1423424), NFS-e 1658098 (1423425) e NFS-e 1658110 (1423426)

[[LISTA_POR_EXTENSO_REDUZIDA_SEM_LINK]]: cria uma lista com os itens escritos por extenso conforme abaixo, só com o número do documento:

1642745, 1649292, 1658087, 1658098 e 1658110

[[LISTA_POR_EXTENSO_COMPLETA_SEM_LINK]]: cria uma lista com os itens escritos por extenso conforme abaixo, com o tipo e o número do documento:

NFS-e 1642745, NFS-e 1649292, NFS-e 1658087, NFS-e 1658098 e NFS-e 1658110

[[LISTA_MANUAL]]: cria uma lista manual usando as propriedades dos documentos selecionados caso alguma das listas acima não atenderem


LISTA_MANUAL(modelo, tipo, classe);

modelo: crie um modelo assim utilizando as propriedades do documento:  "[[numeroAnexo]] ([[LINK]])"

tipo: escolha entre "NUMERADA" | "MARCADOR" | "PARAGRAFOS" | "EXTENSO"

classe: escolha uma disponível no seu sistema, por exemplo

preenchendo ficaria assim:

LISTA_MANUAL("[[numeroAnexo]] ([[LINK]])", "NUMERADA", "Texto_Justificado") => string;



[[ADD_S]]: S

[[ADD_s]]: s

[[SAUDACAO]]: Boa noite/Bom dia/Boa tarde - dependendo o horário

[[NOME_USUARIO]]: Fulano
