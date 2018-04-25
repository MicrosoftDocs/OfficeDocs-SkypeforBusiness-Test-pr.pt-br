---
title: Configurar servidores de aplicativo confiáveis
TOCTitle: Configurar servidores de aplicativo confiáveis
ms:assetid: 20c3815f-3048-4940-8c0f-cdfcd0801d5d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204735(v=OCS.15)
ms:contentKeyID: 49306102
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar servidores de aplicativo confiáveis

 

_**Tópico modificado em:** 2014-11-05_

Em um ambiente misturado, se você criar um novo servidor do aplicativo confiável, deve definir o próximo pool de salto como um pool do Lync Server 2013. Em um ambiente misturado, o pool herdado do Lync Server 2010 e o pool do Lync Server 2013 aparecem na lista suspensa. Selecionar o pool herdado não é suportado.

**Selecione Lync Server 2013 como o próximo salto ao criar um servidor de aplicativo Confiável**

1.  Abra o Construtor de Topologia.

2.  No painel à esquerda, clique com o botão direito do mouse em **Servidores de aplicativos confiáveis** e clique em **Novo pool de aplicativo confiável** .

3.  Insira o **FQDN do Pool** do pool de aplicativos confiáveis e selecione se será um servidor múltiplo ou único.

4.  Clique em **Avançar** .

5.  Na página **Selecionar próximo salto** , a partir da lista, selecione o pool de Front End Lync Server 2013.

6.  Clique em **Concluir** .

7.  Selecione o nó superior **Lync Server** e no menu **Ações** , selecione **Publicar** .
    
    Verifique se o **Pool de Aplicativos Confiáveis** foi criado com êxito e estará associado ao pool de Front-End correto.

