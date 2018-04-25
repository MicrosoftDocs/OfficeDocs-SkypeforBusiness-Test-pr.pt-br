---
title: Verificar ambiente do Lync Server 2010
TOCTitle: Verificar ambiente do Lync Server 2010
ms:assetid: bfc7c620-556a-43cd-b1ed-2c268ec2b5cc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205231(v=OCS.15)
ms:contentKeyID: 49307990
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar ambiente do Lync Server 2010

 

_**Tópico modificado em:** 2012-10-19_

Antes de implantar o Lync Server 2013 em um estado de coexistência com Lync Server 2010, é necessário verificar se os serviços do Lync Server 2010 foram configurados e inicializados. É importante identificar serviços chave e recursos que existem em seu ambiente herdado, antes de implantar um pool piloto do Lync Server 2013. Antes de implantar o XMPP do Microsoft Lync Server 2013 em um estado de coexistência com uma implantação XMPP herdada, você precisa verificar se os serviços XMPP herdados foram configurados e inicializados, bem como identificar qual parceiro federado é suportado pela configuração XMPP. A verificação da implantação herdada do Lync Server 2010 acarreta no seguinte:

  - Verificando se os serviços do Lync Server 2010 foram inicializados

  - Analisando a topologia e os usuários no Lync Server 2010.

  - Verificando a federação e as configurações do servidor de borda.

  - Verificando serviços XMPP e parceiros federados.

**Verificar se os serviços do Lync Server 2010 foram inicializados**

1.  No servidor Front End Lync Server 2010, navegue em Ferramentas Administrativas\\Serviços applet.

2.  Verifique se os serviços a seguir estão sendo executados no servidor Front End:
    
    ![Lista de serviços em execução do Servidor Front-End](images/JJ205231.639f2729-b759-4d8e-b4ad-59d7f68adcd2(OCS.15).jpg "Lista de serviços em execução do Servidor Front-End")

**Analisar a topologia do Lync Server 2010 no Painel de Controle do Lync Server**

1.  Faça o logon no Servidor Front-End com uma conta que seja membro do grupo RTCUniversalServerAdmins ou membro da função administrativa do CsAdministrator ou do CsUserAdministrator .

2.  Abra o painel de controle do Lync Server.

3.  Selecione **Topologia** . Verifique se vários servidores em sua implantação do Lync Server 2010 estão listados.
    
    ![Página de topologia do Painel de Controle do Lync Server 2010](images/JJ205231.338ce4fb-2162-4176-a249-ec4ae021fa6a(OCS.15).jpg "Página de topologia do Painel de Controle do Lync Server 2010")

**Para analisar usuários do Lync Server 2010 no Painel de Controle do Lync Server**

1.  Abra o painel de controle do Lync Server.

2.  Selecione **Usuários** e clique em **Localizar** .

3.  Verifique se a coluna **Pool do registrador** aponta para o pool do Lync Server 2010 para cada usuário listado.
    
    ![Painel de Controle do Lync Server 2010 que lista os usuários](images/JJ205231.a9378c40-7a52-4c78-ad83-1463847c9edb(OCS.15).jpg "Painel de Controle do Lync Server 2010 que lista os usuários")

**Para verificar as configurações de federação e borda do Lync Server 2010**

1.  Inicie o Construtor de topologia.

2.  Selecione **Baixar topologia da implantação existente**.

3.  Escolha um nome de arquivo e salve a topologia com o tipo de arquivo .tbxml padrão.

4.  Expanda o nó Lync Server 2010 para revelar várias funções de servidor na implantação.

5.  Selecione o nó do site e verifique se um valor de **Atribuição de tora de federação do site** está definido.
    
    ![Construtor de Topologias, Rota de Federação de Site](images/JJ205231.87de3735-af7e-4280-8d72-c42cb0ea1c05(OCS.15).jpg "Construtor de Topologias, Rota de Federação de Site")

6.  Em seguida, selecione o pool front-end do servidor Standard Edition ou Enterprise Edition. Determine se um pool de borda foi configurado para Mídia abaixo de **Associações**.
    
    ![Construtor de Topologias mostrando servidores e pools](images/JJ205231.5ad5ea3b-b122-44dd-8968-f1147d6d45f1(OCS.15).jpg "Construtor de Topologias mostrando servidores e pools")

7.  Por fim, selecione o pool de borda e identifique se um pool de Próximo salto está configurado abaixo de **Seleção do próximo salto**.
    
    ![Construtor de Topologias, Seleção de próximo salto](images/JJ205231.3121e723-fba7-498e-a786-bde7be1a55e2(OCS.15).jpg "Construtor de Topologias, Seleção de próximo salto")

**Verificar a configuração de parceiro federado XMPP herdado**

1.  Do servidor de XMPP herdado, navegue para o applet Serviços/Ferramentas Administrativas.

2.  Verifique se o serviço de Gateway XMPP do Office Communications Server foi iniciado.
    
    ![Servidor de Gateway XMPP do Office Communications Server](images/JJ721906.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Servidor de Gateway XMPP do Office Communications Server")

