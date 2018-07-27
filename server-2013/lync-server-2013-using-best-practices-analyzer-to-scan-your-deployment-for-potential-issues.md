---
title: Usando o analisador de práticas recomendadas para buscar possíveis problemas em sua implantação
TOCTitle: Usando o analisador de práticas recomendadas para buscar possíveis problemas em sua implantação
ms:assetid: 09c84509-dc91-4e7b-882b-3c467b6b026d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg591343(v=OCS.15)
ms:contentKeyID: 49305824
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando o analisador de práticas recomendadas para buscar possíveis problemas em sua implantação

 

_**Tópico modificado em:** 2012-10-21_

Para executar um exame do Analisador de Práticas Recomendadas, é necessário especificar o seguinte:

  - **Credenciais**   Para executar um exame, é necessário fazer logon em um computador no qual o Analisador de Práticas Recomendadas está instalado usando uma conta membro do grupo local Administradores. Além disso, é necessário fazer logon usando uma conta de usuário que tenha os direitos e permissões necessários para executar os exames apropriados, ou é necessário especificar credenciais que tenham os direitos e permissões de usuário apropriados ao executar o Analisador de Práticas Recomendadas. Para obter detalhes, consulte [Associações de Grupo e Requisitos de Direitos do Usuário para o Analisador de Práticas Recomendadas](lync-server-2013-group-memberships-and-user-rights-requirements-for-best-practices-analyzer.md).

  - **Escopo do exame**   Para especificar o escopo do exame, selecione as categorias e servidores que você deseja examinar. É possível selecionar todas as categorias, um ou mais categorias, ou um ou mais servidores dentro de uma categoria específica em seu ambiente do Lync Server.

  - **Tipo de exame**   Atualmente, o exame de Verificação de Integridade é o único tipo de exame disponível (selecionado por padrão). A Verificação de Integridade pode gerar um relatório que inclui erros, avisos e outras informações para todos os servidores especificados no escopo.

  - **Velocidade de rede**   As opções de velocidade de rede incluem Fast LAN (100 Mbps ou mais), LAN (10 Mbps), Fast WAN (1,5 Mbps) ou WAN (64 kbps). O tempo estimado para completar o exame tem base nessa configuração. Essa configuração também é usada para definir o período de tempo limite. Durante o exame, o Analisador de Práticas Recomendadas espera uma resposta de um servidor durante um tempo especificado. Se não receber uma resposta dentro do período de tempo limite especificado, ele vai para o próximo servidor no exame. Em redes mais lentas, esse período de tempo limite especificado é maior para acomodar latências de rede maiores. Recomendamos a seleção do link mais lento em sua topologia para esse parâmetro de modo que a ferramenta não ultrapasse o tempo limite muito rápido.

## Para examinar sua implantação do Lync Server 2013

1.  Faça logon em um computador no qual o Analisador de Práticas Recomendadas está instalado usando uma conta membro do grupo local Administradores, e com outros direitos e permissões necessárias.

2.  Clique em **Iniciar**, aponte para **Todos os Programas**, clique em **Microsoft Lync Server 2013** e clique em **Analisador de Práticas Recomendadas**.

3.  Na tela **Boas-vindas**, clique em **Selecionar opções para uma nova verificação**.

4.  Na página **Conectar ao Active Directory**, verifique o nome especificado em **Servidor Active Directory** e execute uma das seguintes opções:
    
      - Para executar um exame usando as credenciais usadas para fazer logon no computador, clique em **Conectar ao servidor do Active Directory**.
    
      - Para especificar credenciais diferentes que você deseja usar para os Serviços de Domínio do Active Directory, Servidor de Borda ou Exchange Server, clique em **Mostrar opções avançadas de logon**, marca cada caixa de seleção para a qual as credenciais separadas são necessárias, especifique as credenciais para cada caixa de seleção marcada e clique em **Conectar ao servidor do Active Directory**.
    
    > [!NOTE]  
    > Antes de começar o exame, o Analisador de Práticas Recomendadas executa uma verificação de rede e de permissões a fim de assegurar que as credenciais de conta especificadas sejam válidas e que o Analisador de Práticas Recomendadas possa se conectar aos Serviços de Domínio do Active Directory. Se a ferramenta estiver em execução em um servidor de grupo de trabalho, a ferramenta também verificará se pode se conectar aos Servidores de Borda na rede de perímetro (ou seja, se estiverem incluídos no exame).

5.  Na página **Iniciar uma nova verificação das Práticas Recomendadas**, selecione as opções que você deseja incluir no exame, especifique a velocidade da rede e clique em **Iniciar exame**.

6.  Na página **Verificação concluída**, clique em **Exibir um relatório desta verificação das Práticas Recomendadas**.

7.  Na página **Exibir Relatório das Práticas Recomendadas**, execute uma das seguintes ações:
    
      - Para exibir os relatórios em uma lista organizada pelo componente de servidor, clique em **Listar Relatórios** e clique na guia **Todos os Problemas** ou na guia **Itens Informativos**.
    
      - Para exibir os relatórios como uma lista hierárquica organizada por tipos de resultados, clique em **Relatórios em Árvore** e clique na guia **Exibição Detalhada** ou na guia **Exibição Resumida**.
    
      - Para exibir outros relatórios, clique em **Outros Relatórios**.
    
    > [!NOTE]  
    > Para obter detalhes sobre os relatórios do Analisador de Práticas Recomendadas e os problemas identificados por eles, consulte <a href="lync-server-2013-viewing-and-working-with-reports-created-by-best-practices-analyzer.md">Exibir e trabalhar com relatórios gerados pelo Analisador de Práticas Recomendadas</a> e <a href="lync-server-2013-analyzing-and-resolving-issues-identified-by-best-practices-analyzer.md">Analisando e Resolvendo Problemas Identificados pelo Analisador de Práticas Recomendadas</a>.
