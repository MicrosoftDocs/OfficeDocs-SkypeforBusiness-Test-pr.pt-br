---
title: Criar links de região de rede no Lync Server 2013
TOCTitle: Criar links de região de rede no Lync Server 2013
ms:assetid: f8163910-8935-475d-88a2-3aa44feb9dbe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413047(v=OCS.15)
ms:contentKeyID: 49308653
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar links de região de rede no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Regiões dentro de uma rede são vinculadas através de uma conectividade WAN física. Um *link de região de rede* cria um link entre duas regiões configuradas para controle de admissão de chamada (CAC) e define os limites da largura de banda em tráfego de áudio e vídeo entre estas regiões.

Para obter detalhes sobre o trabalho com links da região de rede, consulte a documentação Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - [New-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegionLink)

  - [Get-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)

  - [Set-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkRegionLink)

  - [Remove-CsNetworkRegionLink](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkRegionLink)

A topologia de exemplo possui um link entre as regiões da América do Norte e APAC e um link entre as regiões EMEA e APAC. Cada um destes links de região são restritos pela largura de banda WAN, conforme descrito na tabela de Informação de largura de banda do link de região na seção [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) da documentação de implantação.

## Para criar links de região de rede usando o Shell de Gerenciamento do Lync Server

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsNetworkRegionLink para criar os links de região e aplicar os perfis da política de largura de banda adequados. Por exemplo, execute:
    
```
        New-CsNetworkRegionLink -NetworkRegionLinkID NA-EMEA-LINK -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID 50Mb_Link
```
```
   
       New-CsNetworkRegionLink -NetworkRegionLinkID EMEA-APAC-LINK -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -BWPolicyProfileID 25Mb_Link
```

## Para criar links de região de rede usando o Painel de controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede**.

3.  Clique no botão de navegação **Link de região**.

4.  Clique em **Novo**.

5.  Na página **Novo link de região**, clique em **Nome** e digite um nome para o link de região de rede.

6.  Clique em **Região de rede 1** e clique na região de rede da lista que deseja vincular para a Região de rede 2.

7.  Clique em **Região de rede 2** e clique na região de rede da lista que deseja vincular para a Região de rede 1.

8.  Opcionalmente, clique em **Política da largura de banda** e selecione o perfil da política de largura de banda que deseja aplicar para o link de região de rede.
    
    > [!NOTE]  
    > Aplique uma política de largura de banda apenas se o link de região de rede é restrito por largura de banda e se deseja usar o CAC para controlar o tráfego de mídia naquele link.

9.  Clique em **Confirmar**.

10. Para finalizar a criação de links de região de rede para sua topologia, repita as etapas 4 a 9 com as configurações de outras regiões.

