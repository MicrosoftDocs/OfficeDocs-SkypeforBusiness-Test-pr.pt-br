---
title: Exibir políticas de versão do cliente
TOCTitle: Exibir políticas de versão do cliente
ms:assetid: 6cd9a897-c694-4d6a-8259-2d3c01fce275
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ898479(v=OCS.15)
ms:contentKeyID: 52057631
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir políticas de versão do cliente

 

_**Tópico modificado em:** 2013-02-23_

Políticas de versão de cliente são utilizadas para aplicar globalmente ou a um site, pool ou grupo de usuários em específico, um conjunto de regras para versionamento de cliente. Você pode visualizar as políticas de versão de cliente que foram configuradas em seu ambiente Lync Server 2013 a partir de Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para visualizar políticas de versão de cliente utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e então no botão de navegação **Política de Versão de Cliente**.

4.  Se quiser visualizar as regras para uma política de versão de cliente, na página **Política de Versão de Cliente** dê um duplo-clique na política que deseja visualizar.

## Para visualizar políticas de versão de cliente utilizando Cmdlets Windows PowerShell

Você pode visualizar políticas de versão de cliente utilizando o cmdlet **Get-CsClientVersionPolicy**. Esse cmdlet pode ser executado pelo Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar políticas de versão de cliente

  - Para visualizar informações sobre todas as suas políticas de versão de cliente, digite o comando a seguir no Shell de Gerenciamento do Lync Server e então pressione ENTER:
    
        Get-CsClientVersionPolicy
    
    Isso terá como retorno informações similares a essas:
    
        Identity    : Global
        Rules       : {RuleId=2336c611-a243-4c5d-994b-eea8a524d0e4;
                      Description=;Action=Block;ActionUrl=;MajorVersion=1;
                      MinorVersion=3;BuildNumber=;QfeNumber=;
                      UserAgent=RTC;UserAgentFullName=;Enabled=True;
                      CompareOp=LEQ, RuleId=342c9b90-4cef-483a-a73a-
                      4fe75c88711d;Description=;Action=Block;ActionUrl=;
                      MajorVersion=5;MinorVersion=;BuildNumber=;QfeNumber=;
                      UserAgent=WM;UserAgentFullName=;Enabled=True;
                      CompareOp=LEQ,RuleId=ea03af61-9db5-4bf9-af3f-042
                      ab8dd9994;Description=;Action=Block;ActionUrl=;
                      MajorVersion=3;MinorVersion=5;BuildNumber=6907;
                      QfeNumber=83;UserAgent=OC;UserAgentFullName=;
                      Enabled=True;CompareOp=LEQ, RuleId=831edb68-
                      e482-4431-a10e-add365ba8099;Description=;
                      Action=Block;ActionUrl=;MajorVersion=2;MinorVersion=0;
                      BuildNumber=5999;QfeNumber=;UserAgent=UCCP;
                      UserAgentFullName=;Enabled=True;CompareOp=LEQ...}
        Description :

Para detalhes, veja o tópico Ajuda para o cmdlet [Get-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientVersionPolicy).

