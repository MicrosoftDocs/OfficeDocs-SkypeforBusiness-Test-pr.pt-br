---
title: Migrar telefones de área comum
TOCTitle: Migrar telefones de área comum
ms:assetid: 31bd26fc-861b-45c6-8221-18df16e575de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688015(v=OCS.15)
ms:contentKeyID: 49886164
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar telefones de área comum

 

_**Tópico modificado em:** 2012-09-29_

Os telefones de área comum são telefones IP que quase sempre se encontram em um espaço de trabalho compartilhado ou área comum, como um lobby, uma cozinha ou um andar de fábrica. Os telefones de área comum não precisam estar conectados a um computador para oferecer a funcionalidade de comunicações unificadas do Lync Server. Depois de migrar uma implantação do Lync Server 2010 para o Lync Server 2013,você deve migrar também os objetos de contato associados ao telefone de área comum herdado. Usando o Shell de Gerenciamento do Lync Server, primeiro você recupera todos os objetos de contato associados aos telefones de área comum do Lync Server 2010 e, em seguida, move esses objetos para o pool do Lync Server 2013.

**Migrar telefones de área comum**

1.  No servidor Front-End do Lync Server 2013, abra o Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsCommonAreaPhone -Target pool02.contoso.net

3.  Para verificar se todos os objetos de contato foram movidos para o pool do Lync Server 2013, no Shell de Gerenciamento do Lync Server, digite o seguinte:
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool02.contoso.net"}
    
    Verifique se todos os objetos de contato estão agora associados ao pool do Lync Server 2013.

