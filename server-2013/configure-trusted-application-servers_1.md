---
title: Configurar servidores de aplicativos confiáveis
TOCTitle: Configurar servidores de aplicativos confiáveis
ms:assetid: 47a9e72e-566c-4c23-bec2-760a3098a974
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204865(v=OCS.15)
ms:contentKeyID: 49306583
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar servidores de aplicativos confiáveis

 

_**Tópico modificado em:** 2012-10-04_

Em um ambiente misto, se você criar um novo servidor de aplicativo confiável após mesclar a topologia Office Communications Server de legado com Lync Server 2013 e definir um novo servidor de aplicativo confiável utilizando o Construtor de Topologia, você deverá definir o próximo pool de salto para um pool Lync Server 2013. Em um ambiente mesclado, tanto o pool Office Communications Server de legado quanto o pool Lync Server 2013 aparecem na lista suspensa. Selecionar o pool de legado *não* é suportado.

## Para selecionar Lync Server 2013 como próximo salto ao criar um servidor de aplicativos confiável

1.  Abra uma topologia existente no Construtor de Topologia.

2.  No painel à esquerda, clique com o botão direito do mouse em **Servidores de aplicativos confiáveis** e clique em **Novo pool de aplicativo confiável** .

3.  Insira o **Pool FQDN** para o pool de aplicativo confiável e selecione se será uma implantação de servidor único ou de vários servidores.

4.  Clique em **Avançar** .

5.  Na página **Selecionar próximo salto** , a partir da lista, selecione o pool de Front End Lync Server 2013.
    
    ![Caixa de diálogo Definir Novo Pool de Aplicativos Confiáveis](images/JJ204865.ecfe2bb8-758b-4b36-8146-573005c4ab09(OCS.15).jpg "Caixa de diálogo Definir Novo Pool de Aplicativos Confiáveis")  

6.  Clique em **Concluir** .

7.  Selecione o nó superior **Servidor Lync** e, do painel **Ações** , selecione **Publicar** .

8.  Verifique se o **Pool de aplicativo confiável** foi criado com êxito e associado ao pool de Front End correto.

