---
title: Implantar Servidor de Borda piloto
TOCTitle: Implantar Servidor de Borda piloto
ms:assetid: dab345c0-8577-4c11-ac73-fe8b2a75f4cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205306(v=OCS.15)
ms:contentKeyID: 49308311
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar Servidor de Borda piloto

 

_**Tópico modificado em:** 2012-10-19_

Este tópico destaca as definições de configurações que você deve ter cuidado antes de implantar seu Lync Server 2013  Servidor de Borda. Os processos de implantação e configuração do Lync Server 2013 são muito semelhantes ao Lync Server 2010. Esta seção destaca somente os principais pontos que você deve considerar como parte da implantação do pool piloto. Para obter etapas detalhadas, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de Implantação, que descreve o processo de implantação e também oferece informação de configuração para acesso do usuário externo.

Conforme você navega pelo assistente **Definir Novo Pool de Borda** , reveja as principais definições de configuração exibidas nas etapas a seguir. Observe que somente algumas páginas do assistente **Definir Novo Pool de Borda** são mostradas.

**Definir um Pool de Borda**

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Navegue para o nó Lync Server 2013. Com o botão direito em **Pools de borda** e clique em **Novo pool de borda** .
    
    ![Caixa de diálogo Definir novo pool de borda](images/JJ205306.a90d388c-49ff-4620-a19d-42e2f1bb559c(OCS.15).jpg "Caixa de diálogo Definir novo pool de borda")

3.  Um pool de Borda pode ser um **Pool de vários computadores** ou **Pool de computador único** .
    
    ![Caixa de diálogo Definir o FQDN do pool de borda](images/JJ205306.4904fe8f-537c-4e66-a399-1bd8a316dc10(OCS.15).jpg "Caixa de diálogo Definir o FQDN do pool de borda")

4.  Na página **Selecionar recursos** , não habilite a federação ou a federação XMPP. A federação e federação XMPP são atualmente roteadas através do Lync Server 2010Servidor de Borda herdado. Estes recursos serão configurados posteriormente na fase de migração.
    
    ![Caixa de diálogo Selecionar recursos](images/JJ205306.cb0b45a4-2856-45ba-bd97-e49fafbb077e(OCS.15).jpg "Caixa de diálogo Selecionar recursos")

5.  Em seguida, continue preenchendo as seguintes páginas do assistente: **FQDN's Externos** , **Definir o endereço IP interno** e **Definir o endereço IP externo** .

6.  Na página **Definir o próximo salto** , selecione o Diretor para o próximo salto do Pool de borda do Lync Server 2010. 
    
    ![Caixa de diálogo Definir próximo salto](images/JJ205306.11baf3ea-74f5-4eb7-8650-b03b3b190416(OCS.15).jpg "Caixa de diálogo Definir próximo salto")

7.  Na página **Associar pool de mediação ou front-end** , não associe um pool dentro deste Pool de borda neste momento. O tráfego de mídia externo é atualmente roteado pelo Lync Server 2010  Servidor de Borda herdado. Esta configuração será definida posteriormente na fase de migração.
    
    ![Caixa de diálogo Pools de front-end associados](images/JJ205306.fe0da887-7b51-4564-afc5-d57da95a2eb6(OCS.15).jpg "Caixa de diálogo Pools de front-end associados")

8.  Clique em **Concluir** e **Publique** a topologia.

9.  Siga as etapas em [Instalar Servidores de Borda para Lync Server 2013](lync-server-2013-install-edge-servers.md) na documentação de Implantação para instalar os arquivos no novo Servidor de Borda, configurar certificados e iniciar os serviços.

É muito importante seguir as orientações dos tópicos [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de Implantação. Este seção forneceu somente algumas informações sobre definições de configuração ao instalar estas funções de servidor.

Você deve ter agora um Servidor de Borda do Lync Server 2010 herdado em paralelo com uma implantação do servidor de Borda do Lync Server 2013. Verifique se ambas as implantações estão em execução adequadamente, se os serviços foram iniciados e se você pode administrar cada implantação antes de seguir para a próxima fase.

