---
title: 'Lync Server 2013: Configurando rotas de voz para chamadas de saída'
TOCTitle: Configurando rotas de voz para chamadas de saída
ms:assetid: 3c182cdd-7a4a-4a9d-bdac-4199f0abd947
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425890(v=OCS.15)
ms:contentKeyID: 49306463
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando rotas de voz para chamadas de saída no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Uma rota de voz do Lync Server 2013 associa os números de telefone de destino com um ou mais gateways de rede de telefone alternada (PSTN) ou troncos SIP e a um ou mais registros de utilização PSTN.

**Para exibir rotas de voz utilizando Painel de Controle do Lync Server**

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Clique em **Roteamento de voz**.

3.  Clique em **Rota**.

4.  Clique duas vezes em uma rota de voz para visualizar propriedades adicionais a partir da lista de rotas de voz ou selecione a rota e clique em **Editar**. Então, clique em **Exibir detalhes**.
    
    > [!NOTE]  
    > Você só pode visualizar informações detalhadas para uma única rota por vez.

**Para exibir rotas de voz utilizando Windows PowerShell**

  - Rotas de voz do Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**. podem ser exibidas utilizando os cmdlets Windows PowerShell e **Get-CsVoiceRoute**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    Para visualizar informações sobre todas as suas rotas de voz, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsVoiceRoute
    
    Isso retornará informações parecidas com:
    
        Identity          : global
        Priority          : -1
        Description       :
        NumberPattern     : ^(\+1[0-9]{10})$
        PstnUsages        : {}
        PstnGatewayList   : {}
        Name              : global
        SuppressCallerId  :
        AlternateCallerId :

> [!NOTE]  
> Para obter detalhes, consulte <a href="lync-server-2013-voice-routes.md">Rotas de voz no Lync Server 2013</a> na documentação de Planejamento.

## Nesta seção

  - [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md)

  - [Modificar um roteamento de voz no Lync Server 2013](lync-server-2013-modify-a-voice-route.md)

## Consulte Também

#### Outros Recursos

[Gerenciando o roteamento de voz no Lync Server 2013](lync-server-2013-managing-voice-routing.md)

