---
title: Modificar a ação padrão para clientes não explicitamente suportados ou restritos
TOCTitle: Modificar a ação padrão para clientes não explicitamente suportados ou restritos
ms:assetid: 548dd0f5-62fe-4c3f-8952-2b9fd4c5fff3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520994(v=OCS.15)
ms:contentKeyID: 49306735
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar a ação padrão para clientes não explicitamente suportados ou restritos

 

_**Tópico modificado em:** 2013-02-23_

Além de especificar a versão de clientes aos quais você deseja oferecer suporte em seu ambiente do Lync Server 2013, você também pode especificar uma ação padrão para clientes que ainda não têm uma política de versão definida. Isso permite restringir as versões de clientes que são usadas no ambiente do Lync Server, o que pode ajudá-lo a controlar os custos associados ao suporte a várias versões de clientes.

## Para modificar a ação padrão para clientes não explicitamente suportados ou restritos

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e em **Configuração de Versão de Cliente**.

4.  Na página **Configuração de Versão de Cliente**, clique duas vezes na configuração **Global** da lista.

5.  Na caixa de diálogo **Editar Configuração de Versão de Cliente**, verifique se que a caixa de seleção **Habilitar Controle de Versão** está marcada e, em **Ação padrão**, selecione uma das seguintes opções:
    
      - **Permitir** Permite que o cliente faça logon quando a versão do cliente não corresponde a nenhum filtro na lista **Políticas de Versões de Clientes**.
    
      - **Bloquear** Impede que o cliente faça logon quando a versão do cliente não corresponde a nenhum filtro na lista **Políticas de Versões de Clientes**.
    
      - **Bloquear com URL** Impede que o cliente faça logon quando a versão do cliente não corresponde a nenhum filtro na lista **Políticas de Versões de Clientes** e inclui uma mensagem de erro que contém uma URL onde um cliente mais recente pode ser baixado.
    
      - **Permitir com URL** Permite que o cliente faça logon quando a versão do cliente não corresponde a nenhum filtro na lista **Políticas de Versões de Clientes** e inclui uma mensagem de erro que contém uma URL onde um cliente mais recente pode ser baixado.

6.  Se você tiver selecionado **Bloquear com URL**, digite a URL de download do cliente para incluir na mensagem de erro na caixa **URL**.

7.  Clique em **Confirmar**.

## Para desabilitar o controle de versão de cliente

  - Para desabilitar o controle de versão para permitir que todos os clientes façam logon, independentemente da versão de cliente, desmarque a caixa de seleção **Habilitar controle de versão** e clique em **Confirmar**.

## Modificação da ação padrão utilizando cmdlets do Lync Server PowerShell

A ação padrão a ser executada quando os usuários tentarem entrar utilizando os clientes que não são explicitamente suportados ou restritos por uma política de versão do cliente também pode ser gerenciada utilizando Interface da linha de comando do Windows PowerShell e o cmdlet **Set-CsClientVersionPolicy**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Configuração da ação padrão para Bloquear acesso

  - O seguinte comando define a ação padrão para o bloqueio do site de Redmond. Isso bloqueará o registro de qualquer cliente para o qual nenhuma regra de configuração de versão do cliente existir.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Block

## Configuração da ação padrão para Permitir acesso

  - Neste exemplo, a ação padrão para o site de Redmond é definir como Permitir. Isso permitirá o registro de qualquer cliente para o qual nenhuma regra de configuração de versão do cliente existir.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -DefaultAction Allow

Para obter detalhes, consulte o tópico de ajuda para o cmdlet [Set-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionPolicy).

## Consulte Também

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

