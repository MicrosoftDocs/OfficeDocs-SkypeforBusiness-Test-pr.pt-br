---
title: Exibir números de acesso para conferência discada
TOCTitle: Exibir números de acesso para conferência discada
ms:assetid: 41a7dfb4-0c89-4650-b61b-0e1bf875c62b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688037(v=OCS.15)
ms:contentKeyID: 49886191
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir números de acesso para conferência discada

 

_**Tópico modificado em:** 2013-02-23_

Em Painel de Controle do Lync Server 2013, você fornece números de acesso por discagem aos usuários para que eles possam participar de uma reunião externamente.

## Para visualizar números de acesso por discagem

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Conferência** e, então, em **Número de acesso de discagem**.

4.  Na página **Número de acesso de discagem**, clique no número de acesso que gostaria de visualizar.

5.  Em **Editar**, selecione a caixa de verificação **Exibir detalhes…**.

## Visualizando os números de acesso de conferência por discagem utilizando os cmdlets do Lync Server PowerShell

Os números de acesso de conferência por discagem também podem ser visualizados utilizando o Lync Server PowerShell e o cmdlet Get-CsDialInConferencingAccessNumber. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Visualizando informações de configuração do tronco SIP

  - Para visualizar informações sobre todos os números de acesso à conferência por discagem, digite o comando a seguir no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsDialInConferencingAccessNumber
    
    Isso retornará uma informação similar à essa:
    
        Identity           : CN={20ca8dc8-5ff8-41f4-b5bb-22ba9972ae2e},
                             CN=Application Contacts,CN=RTCService=Services,
                             CN=Configuration,DC=litwareinc,DC=com
        PrimaryUri         : sip:testnumber@litwareinc.com
        DisplayName        : Test
        DisplayNumber      : 1-425-555-1019
        LineUri            : tel:+14255551019
        PrimaryLanguage    : en-US
        SecondaryLanguages : {}
        Pool               : atl-cs-001.litwareinc.com
        HostingProvider    :
        Regions            : {US}

Para mais informações, consulte o tópico de ajuda para o cmdlet [Get-CsDialInConferencingAccessNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDialInConferencingAccessNumber).

