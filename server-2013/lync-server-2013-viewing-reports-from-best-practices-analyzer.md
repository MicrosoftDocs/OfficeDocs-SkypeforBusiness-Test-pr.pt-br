---
title: Exibir Relatórios do Analisador de Práticas Recomendadas
TOCTitle: Exibir Relatórios do Analisador de Práticas Recomendadas
ms:assetid: 7217a47b-36b1-4923-81ea-df754cff29bb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg607690(v=OCS.15)
ms:contentKeyID: 49307087
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Relatórios do Analisador de Práticas Recomendadas

 

_**Tópico modificado em:** 2012-09-21_

Quando você usa o Analisador de Práticas Recomendadas para verificar o ambiente, um nome é especificado para a verificação. Depois que o Analisador de Práticas Recomendadas conclui uma verificação, ele armazena os resultados em relatórios e os salva com o nome da verificação. Após a conclusão da verificação, você pode visualizar os relatórios gerados clicando em **Exibir um relatório desta verificação das Práticas Recomendadas** diretamente na página **Verificação Concluída**. Você também pode visualizar relatórios dessa verificação ou de verificações anteriores posteriormente. Você pode visualizar relatórios no computador local no qual a verificação foi executada, importar resultados de verificações de outro computador ou exportar resultados de verificações para visualizar os relatórios em outro computador com o Analisador de Práticas Recomendadas instalado.

Os resultados da verificação são apresentados nos seguintes tipos de relatórios:

  - Relatórios de lista

  - Relatórios de árvore

  - Outros relatórios

Esses relatórios incluem erros, avisos e outras informações. Para obter detalhes sobre cada um desses tipos de relatórios e problemas, consulte [Entendendo os relatórios criados pelo Analisador de Práticas Recomendadas](lync-server-2013-understanding-reports-created-by-best-practices-analyzer.md).

Use o procedimento a seguir para visualizar resultados de verificações gerados anteriormente pelo Analisador de Práticas Recomendadas.

## Para visualizar relatórios de uma verificação anterior

1.  Faça logon em um computador com o Analisador de Práticas Recomendadas instalado usando uma conta que seja membro da conta de usuário local.
    
    > [!NOTE]  
    > Você pode visualizar os resultados de uma verificação usando uma conta que seja membro do grupo Administradores local, mas não pode executar uma verificação a menos que tenha os direitos e permissões de usuário corretos. Para obter detalhes, consulte <a href="lync-server-2013-group-memberships-and-user-rights-requirements-for-best-practices-analyzer.md">Associações de Grupo e Requisitos de Direitos do Usuário para o Analisador de Práticas Recomendadas</a>.

2.  Clique em **Iniciar**, aponte para **Todos os Programas**, clique em **Microsoft Lync Server 2013** e clique em **Analisador de Práticas Recomendadas**.

3.  Na tela **Bem-vindo**, clique em **Selecionar os resultados da verificação para exibir**.

4.  Na página **Selecionar uma Verificação de Práticas Recomendadas para Exibir**, realize um dos seguintes procedimentos:
    
      - Para exibir relatórios da lista de resultados de verificação armazenados localmente, clique no nome da verificação e clique em **Exibir um relatório desta verificação**.
        
        > [!NOTE]  
        > O Analisador de Práticas Recomendadas cria a lista de arquivos locais na pasta <em>&lt;systemDrive&gt;</em>\Documents and Settings\<em>&lt;user&gt;</em>\Application Data\Microsoft\RtcBPA.    
      - Para exibir os relatórios de resultados de uma verificação armazenados em outro local, clique em **Importar verificação**, localize o arquivo que contém os resultados da verificação e clique em **Abrir**.
        
        > [!NOTE]  
        > Caso a versão do Analisador de Práticas Recomendadas neste computador não corresponda à versão usada para coletar os dados no arquivo importado, a ferramenta no computador poderá analisar o arquivo novamente após a importação.

5.  Na página **Exibir Relatório das Práticas Recomendadas**, realize um dos seguintes procedimentos:
    
      - Para exibir relatórios em uma lista organizada por componente do servidor, clique em **Listar Relatórios** e, em seguida, clique na guia **Todos os Problemas** ou na guia **Itens Informativos**.
    
      - Para exibir relatórios como uma lista hierárquica organizada por tipo de resultado, clique em **Relatórios em Árvore** e, em seguida, clique na guia **Exibição Detalhada** ou na guia **Exibição Resumida**.
    
      - Para exibir outros relatórios, clique em **Outros Relatórios**.
    
    > [!NOTE]  
    > Para obter detalhes sobre relatórios do Analisador de Práticas Recomendadas e os problemas identificados, consulte <a href="lync-server-2013-viewing-and-working-with-reports-created-by-best-practices-analyzer.md">Exibir e trabalhar com relatórios gerados pelo Analisador de Práticas Recomendadas</a> e <a href="lync-server-2013-analyzing-and-resolving-issues-identified-by-best-practices-analyzer.md">Analisando e Resolvendo Problemas Identificados pelo Analisador de Práticas Recomendadas</a>.
