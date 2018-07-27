---
title: 'Lync Server 2013: Sincronizar uma senha de conta de autenticação Kerberos com o IIS'
TOCTitle: Sincronizar uma senha de conta de autenticação Kerberos com o IIS
ms:assetid: 05925a66-2684-4c1b-adfa-69bd0da1bf38
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398107(v=OCS.15)
ms:contentKeyID: 49305735
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Sincronizar uma senha de conta de autenticação Kerberos com o IIS no Lync Server 2013

 

_**Tópico modificado em:** 2010-11-08_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

Em um site, Servidores Front-End, servidores Standard Edition e Diretores podem usar uma conta de autenticação Kerberos para propósitos de solicitação de autenticação ao serviço Serviços Web. Esse procedimento aloca cada servidor que execute o Serviços Web em um site ao qual tenha sido designada uma conta Kerberos e atualiza as definições de configuração do IIS (Serviços de Informações da Internet) para o uso dessa conta. Para obter mais detalhes, consulte [Configurar uma senha da conta de autenticação Kerberos authentication em um servidor no Lync Server 2013](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md).

## Para definir e configurar uma senha de autenticação de conta Kerberos

1.  Conecte-se a um computador de origem (como um fe01.contoso.com) como membro do grupo RTCUniversalServerAdmins.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  A partir da linha de comando Shell de Gerenciamento do Lync Server, execute os dois comandos a seguir:
    
        Set-CsKerberosAccountPassword -FromComputer SourceComputer -ToComputer DestinationComputer
    
    Por exemplo:
    
        Set-CsKerberosAccountPassword -FromComputer fe01.contoso.com -ToComputer dir01.contoso.com
    
    > [!IMPORTANT]  
    > O nome do computador de origem e do computador de desinto deve ser um nome de domínio Totalmente qualificado (FQDN) do servidor. Você não pode usar o FQDN do pool, a não ser que o nome do pool seja o mesmo do nome do computador sendo usado como computador de origem ou de destino.    
    > [!IMPORTANT]  
    > Depois de aplicar quaisquer alterações para a autenticação Kerberos, como adicionar ou remover uma conta, você deve executar o <strong>Enable-CsTopology</strong> a partir do prompt de comando do Shell de Gerenciamento do Lync Server.
