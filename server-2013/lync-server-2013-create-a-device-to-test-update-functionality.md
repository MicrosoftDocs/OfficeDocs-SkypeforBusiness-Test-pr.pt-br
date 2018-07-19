---
title: Criar um dispositivo para testar a funcionalidade de atualização
TOCTitle: Criar um dispositivo para testar a funcionalidade de atualização
ms:assetid: ce509fd1-17b3-4b78-b269-fe5d06fe2e1d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182587(v=OCS.15)
ms:contentKeyID: 49308141
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar um dispositivo para testar a funcionalidade de atualização

 

_**Tópico modificado em:** 2013-02-23_

É possível adicionar um dispositivo de teste à página **Dispositivo de Teste** e usar esse dispositivo para verificar a funcionalidade de novas atualizações antes de implantar as atualizações nos dispositivos de produção. É possível testar um dispositivo globalmente (em todo o ambiente do Lync Server) ou dentro de um único local. Identifique um dispositivo de teste pelo seu endereço MAC (Controle de Acesso de Mídia) ou pelo número de série. Quando você adiciona um dispositivo, ele aparece na lista da página **Dispositivo de Teste** do Painel de Controle do Lync Server.

## Para adicionar um dispositivo de teste

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Cliente** e em **Dispositivo de Teste**.

3.  Clique em **Novo** e em **Dispositivo de teste global** ou **Dispositivo de teste de site**.

4.  Siga um destes procedimentos:
    
      - Se você clicou em **Dispositivo de teste global**, vá para a próxima etapa.
    
      - Se você clicou em **Dispositivo de teste de site**, selecione um site na lista de sites disponíveis e clique em **OK**.

5.  Em **Novo Dispositivo de Teste**, digite um nome para o dispositivo em **Nome do dispositivo**.

6.  Em **Tipo de identificador**, clique em **Endereço MAC** ou **Número de série**.

7.  Na caixa **Identificador exclusivo**, digite o endereço MAC ou número de série do dispositivo.

8.  Clique em **Confirmar**.

## Para criar dispositivos de teste usando os cmdlets do Windows PowerShell

Os dispositivos de teste podem ser criados usando o Windows PowerShell e o cmdlet New-CsTestDevice. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

Ao criar dispositivos de teste usando este cmdlet, você deve fazer duas coisas:

  - Especificar o MACAddress ou SerialNumber como o IdentifierType.

  - Incluir o escopo ao especificar a Identidade do dispositivo. Para criar um novo dispositivo no escopo global, use uma sintaxe semelhante a seguinte:
    
        -Identity "global/WindowsPhone"
    
    Para criar um dispositivo de teste no escopo do site, use uma sintaxe semelhante a esta:
    
        -Identity "site:Redmond/WindowsPhone"

## Para criar um dispositivo de teste utilizando o endereço MAC

  - Este comando cria um dispositivo de teste no escopo global e usando o endereço MAC como o IdentifierType:
    
        New-CsTestDevice -Identity "global/WindowsPhone" -IdentifierType "MACAddress" -Identifier "01:02:03:04:05:06"

## Para criar um dispositivo de teste utilizando o número serial

  - Este comando cria um novo dispositivo de teste no escopo local (o local Redmond) e usa o número de série como o IdentifierType:
    
        New-CsTestDevice -Identity "site:Redmond/WindowsPhone" -IdentifierType "SerialNumber" -Identifier "01ABC5419JKR55T"

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [New-CsTestDevice](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsTestDevice).

