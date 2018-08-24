---
title: Configurações de segurança para o Lync Phone Edition
TOCTitle: Configurações de segurança para o Lync Phone Edition
ms:assetid: 6e7cec17-8a79-4428-9300-8821256c46cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521014(v=OCS.15)
ms:contentKeyID: 49307049
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações de segurança para o Lync Phone Edition

 

_**Tópico modificado em:** 2013-02-23_

Ajude a aprimorar a segurança de dispositivos que executam o Lync Phone Edition pelas configurações de segurança SIP e de bloqueio de telefone.

## Para definir as configurações de segurança para o Lync Phone Edition

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e em **Configuração dos dispositivo**.

4.  Na página **Configuração de Dispositivo**, na lista de configurações de dispositivo, clique duas vezes na configuração para a qual você deseja alterar as configurações de segurança.

5.  Em **Editar Configuração dos Dispositivos**, em **Segurança SIP**, especifique o nível de segurança SIP. O nível padrão é **Alto** (recomendado).

6.  Em **Editar Configuração dos Dispositivos**, em **Bloqueio de Telefone**, selecione ou desmarque a caixa de seleção **Impor bloqueio de dispositivo** (selecionada por padrão) e especifique o tamanho mínimo do PIN (seis caracteres por padrão) e o período de tempo limite (10 minutos por padrão). Recomendamos usar esses padrões ou aumentar o tamanho do PIN e/ou reduzir o período de tempo limite.
    
    > [!NOTE]  
    > Para obter detalhes, consulte <a href="lync-server-2013-enforce-phone-locking.md">Aplicar Bloqueio de Telefone</a>.

## Definir configurações de segurança para telefones do Lync Phone Edition usando os cmdlets do Shell de Gerenciamento do Lync Server

As configurações de segurança também podem ser gerenciadas usando Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsUCPhoneConfiguration**. Esse cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para modificar o modo de segurança SIP

  - Este comando define SIPSecurityMode para o conjunto global de configurações de telefone UC como Médio. A segurança SIP também pode ser definida como Baixo ou Alto (valor padrão).
    
        Set-CsUCPhoneConfiguration -Identity global -SIPSecurityMode "Medium"

## Para modificar o tamanho mínimo do PIN

  - Neste exemplo, todas as configurações do telefone UC são modificadas para exigir um PIN com tamanho mínimo de sete dígitos.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -MinPhonePinLength 7

Para obter detalhes, consulte [Get-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUCPhoneConfiguration).

## Consulte Também

#### Conceitos

[Gerenciamento autenticação do Lync Server 2013](lync-server-2013-managing-lync-server-authentication.md)  

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

