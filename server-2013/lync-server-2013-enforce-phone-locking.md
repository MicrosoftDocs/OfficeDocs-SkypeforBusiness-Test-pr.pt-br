---
title: Aplicar Bloqueio de Telefone
TOCTitle: Aplicar Bloqueio de Telefone
ms:assetid: 1f89298b-aea9-4952-93ca-0270b565792b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520963(v=OCS.15)
ms:contentKeyID: 49306089
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Aplicar Bloqueio de Telefone

 

_**Tópico modificado em:** 2013-02-23_

Dispositivos Lync Phone Edition podem ser bloqueados para propósitos de segurança. Se você impor o bloqueio do telefone, o dispositivo executando o Lync Phone Edition bloqueia após um período de tempo que você configurar. Quando um telefone está bloqueado, o usuário pode fazer chamadas mas não pode acessar o calendário e informações de contato, mensagem de voz ou logs de chamada ou usar a pesquisa. Para desbloquear, o usuário insere um PIN.

Para impor o bloqueio do telefone, ative e configure isso ao usar o Painel de Controle do Lync Server ou so cmdlests do Lync Server PowerShell. Você pode impor o bloqueio do telefone globalmente ou apenas em um local o qual está configurado.

## Para configurar e impor o bloqueio do telefone

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Clique**Clientes** e em **Configuração do Dispositivo**.

4.  Na guia **Configuração do Dispositivo**, na lista de configurações do dispositivo, clique duas vezes na configuração de bloqueio do telefone que deseja alterar.

5.  Na caixa de diálogo **Editar Configuração do Dispositivo** verifique se a caixa de seleção **Impor bloqueio do dispositivo** está selecionado.

6.  Em **Tamanho mínimo do PIN**, aceite o valor padrão par ao número mínimo de dígitos que o   PIN usado para desbloquear o telefone deve conter ou especifique um novo valor. O intervalo do tamanho do PIN é 4 a 15 dígitos, e o tamanho padrão é 6 dígitos.

7.  Em **Tempo limite de bloqueio do telefone**, aceite o valor padrão para o período mínimo de tempo antes que o telefone bloqueie ou especifique um novo valor. O intervalo do tempo limite é 0 a 60 minutos; o valor padrão é 10 minutos. Insira o valor no formato HH:MM:SS.

8.  Clique em **Comprometer**.

## Forçar o bloqueio de telefone usando os cmdlets Windows PowerShell

O bloqueio de telefone pode ser forçado usando o cmdlet Set-CsUCPhoneConfiguration. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ativar o bloqueio do telefone

  - O seguinte comando habilita o bloqueio de telefone para o site Redmond. Para desativar o bloqueio de telefone, defina a propriedade EnforcePhoneLock para Falso ($False).
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True

## Para ativar o bloqueio do telefone e modificar o tempo limite de bloqueio

  - Este comando habilita o bloqueio de telefone e também define o tempo limite do bloqueio de telefone para 30 minutos.
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True -PhoneLockTimeout "00:30:00"

## Para ativar o bloqueio de telefone em toda a organização

  - Neste exemplo, o bloqueio de telefone está habilitado em todas as definições de configuração UC em uso na organização.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration  -EnforcePhoneLock $True

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Set-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUCPhoneConfiguration).

## Consulte Também

#### Conceitos

[Gerenciamento autenticação do Lync Server 2013](lync-server-2013-managing-lync-server-authentication.md)  

#### Outros Recursos

[Gerenciando dispositivos, telefones e aplicativos do cliente no Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)

