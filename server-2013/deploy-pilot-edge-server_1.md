---
title: Implantar servidor de borda piloto
TOCTitle: Implantar servidor de borda piloto
ms:assetid: 11a59c48-0a53-4de1-83ed-875f850febd5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204682(v=OCS.15)
ms:contentKeyID: 49305933
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar servidor de borda piloto

 

_**Tópico modificado em:** 2012-10-19_

Este tópico destaca as definições de configuração das quais você deve estar ciente antes de implantar seu Lync Server 2013  Servidor de Borda. Esta seção destaca somente os principais pontos a serem considerados como parte da implantação do seu pool de Borda piloto. Para etapas detalhadas, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de Implantação, que descreve o processo de implantação e também fornece informações de configuração para o acesso de usuário externo.

Conforme você navega pelo assistente **Definir Novo Pool de Borda** , reveja as principais definições de configuração exibidas nas etapas a seguir. Observe que somente algumas páginas do assistente **Definir Novo Pool de Borda** são mostradas.

**Definir um Pool de Borda**

1.  Abra a topologia do pool piloto usando o Construtor de Topologia

2.  Navegue até o nó Lync Server 2013. Clique com o botão direito em **Pools de borda** e clique em **Novo pool de borda** .
    
    ![Caixa de diálogo Definir novo pool de borda](images/JJ205306.a90d388c-49ff-4620-a19d-42e2f1bb559c(OCS.15).jpg "Caixa de diálogo Definir novo pool de borda")

3.  Um pool de Borda pode ser um **Pool de vários computadores** ou **Pool de computador único** .
    
    ![Caixa de diálogo Definir o FQDN do pool de borda](images/JJ205306.4904fe8f-537c-4e66-a399-1bd8a316dc10(OCS.15).jpg "Caixa de diálogo Definir o FQDN do pool de borda")

4.  Na página **Selecionar recursos** , não habilite a federação ou a federação XMPP. Ambas são atualmente roteadas através do Office Communications Server 2007 R2Servidor de Borda herdado. Estes recursos são configurados em uma fase posterior da migração.
    
    ![Caixa de diálogo Selecionar recursos](images/JJ205306.cb0b45a4-2856-45ba-bd97-e49fafbb077e(OCS.15).jpg "Caixa de diálogo Selecionar recursos")

5.  Em seguida, continue preenchendo as seguintes páginas do assistente: **Selecionar opções de IP** , **FQDNs Externos** , **Definir um endereço IP interno** e **Definir um endereço IP externo** .

6.  Na página **Definir o próximo salto**, selecione o Diretor para o próximo salto do Lync Server 2013 Pool de borda.
    
    ![Caixa de diálogo Definir Novo Pool de Borda, lista de pool do próximo salto](images/JJ204682.61d963d5-e0bd-4b1f-b437-e37c267347ba(OCS.15).jpg "Caixa de diálogo Definir Novo Pool de Borda, lista de pool do próximo salto")

7.  Na página **Associar pool de Front End** , não associe um pool a este Pool de borda neste momento. O tráfego de mídia externa é atualmente roteado através da Servidor de Borda do Office Communications Server 2007 R2 legado. Esta definição será configurada em uma fase posterior de migração.
    
    ![Caixa de diálogo Definir novo Pool de Borda](images/JJ204682.bb538039-bd2a-40ed-a120-8b80bd2cefc2(OCS.15).jpg "Caixa de diálogo Definir novo Pool de Borda")

8.  Clique em **Concluir** e **Publique** a topologia.

9.  Siga as etapas em [Instalar Servidores de Borda para Lync Server 2013](lync-server-2013-install-edge-servers.md) na documentação de Implantação para instalar os arquivos no novo Servidor de Borda, configurar certificados e iniciar os serviços.

É muito importante seguir as orientações dos tópicos [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de Implantação. Este seção forneceu somente algumas informações sobre definições de configuração ao instalar estas funções de servidor.

Agora você deve ter uma implantação de servidor de Borda do Office Communications Server 2007 R2 herdada, indicada pela presença do BackCompatSite, em paralelo com uma implantação de servidor de Borda do Lync Server 2013. A Federação está configurada para usar o Office Communications Server 2007 R2 Director. Verifique se ambas as implantações estão em execução adequadamente, se os serviços foram iniciados e se é possível administrar cada implantação antes de seguir para a próxima fase.

![Construtor de Topologias mostrando o Servidor de Borda de OCS](images/JJ204682.171363a3-eaf0-4c94-bd41-02b1ab6fa7dc(OCS.15).jpg "Construtor de Topologias mostrando o Servidor de Borda de OCS")

