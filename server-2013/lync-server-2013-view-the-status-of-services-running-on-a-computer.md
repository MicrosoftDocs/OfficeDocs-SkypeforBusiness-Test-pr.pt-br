---
title: Exibir o status dos serviços executados em um computador no Lync Server 2013
TOCTitle: Exibir o status dos serviços executados em um computador no Lync Server 2013
ms:assetid: f41918e7-4c02-431e-840a-88a1f36ae499
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182606(v=OCS.15)
ms:contentKeyID: 49308589
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir o status dos serviços executados em um computador no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

É possível usar o Painel de Controle do Lync Server 2013 para exibir todos os serviços executados em um determinado computador em sua topologia do Lync Server e ver o status de cada serviço.

## Para exibir o status dos serviços executados em um computador

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Topologia**.

4.  Na página **Status**, classifique ou pesquise a lista conforme necessário para localizar o computador que deseja e clique no nome do computador.

5.  Faça qualquer um dos seguintes:
    
      - Para ver os status de serviços mais atuais executados no computador, clique em **Obter status de serviço**.
    
      - Para ver uma lista de serviços específicos executados no computador e o status de cada serviço, clique em **Propriedades** e em **Fechar** para retornar à lista.

## Exibindo o status do serviço usando os cmdlets do Shell de Gerenciamento do Lync Server

Também é possível exibir o status do serviço usando o Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsWindowsService**. Esse cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876)..

## Para exibir o status do serviço

  - Para exibir o status do serviço em um computador, digite um comando parecido com o seguinte noShell de Gerenciamento do Lync Server e pressione Enter:
    
        Get-CsWindowsService -ComputerName atl-cs-001.litwareinc.com | Select-Object RoleName, Status
    
    Esse comando retornará informações parecidas com:
    
        RoleName                                  Status
        --------                                  ------
        {W3SVC}                                   Running
        {CentralManagement}                       Running
        {ClsAgent}                                Running
        {Registrar, UserServer, EdgeServer}       Running
        {ApplicationServer}                       Running
        {ConferencingServer}                      Running
        {MediationServer}                         Running

Para obter mais informações, consulte [Get-CsWindowsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsWindowsService).

## Consulte Também

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

