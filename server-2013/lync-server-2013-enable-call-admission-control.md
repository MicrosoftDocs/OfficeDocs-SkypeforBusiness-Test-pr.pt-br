---
title: Habilitar o controle de admissão de chamadas no Lync Server 2013
TOCTitle: Habilitar o controle de admissão de chamadas no Lync Server 2013
ms:assetid: 80201105-18f7-4c02-9c71-8df5a952f6c7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398642(v=OCS.15)
ms:contentKeyID: 49307269
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar o controle de admissão de chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Após definir as configurações de rede para a implantação do serviço de controle de admissão de chamadas, habilite o CAC para que as políticas de largura de banda entrem em vigor.

Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server sobre os seguintes cmdlets:

  - [Get-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkConfiguration)

  - [Set-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkConfiguration)

  - [Remove-CsNetworkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkConfiguration)

## Para habilitar o controle de admissão de chamada usando o Shell de gerenciamento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsNetworkConfiguration para ativar o CAC na rede. Por exemplo, execute:
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 1
    
    Se você deseja desativar o CAC na rede, execute o seguinte:
    
        Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck 0

## Para habilitar o controle de admissão de chamada usando o painel de controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de Rede**.

3.  Clique no botão de navegação **Global**.

4.  Clique em **Global** na lista e selecione **Exibir detalhes** no menu **Editar**.

5.  Na página **Editar Configurações Globais**, marque a caixa de seleção **Ativar controle de admissão de chamada**.
    
    > [!NOTE]  
    > Se você deseja desativar o controle de admissão de chamada durante a implantação, desmarque esta caixa de seleção.

6.  Clique em **Confirmar**.

