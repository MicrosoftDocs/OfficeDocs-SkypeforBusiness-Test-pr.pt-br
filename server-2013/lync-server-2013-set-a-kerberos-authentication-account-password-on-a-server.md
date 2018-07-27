---
title: 'Lync Server 2013: Configurar uma senha da conta de autenticação Kerberos authentication em um servidor'
TOCTitle: Configurar uma senha da conta de autenticação Kerberos authentication em um servidor
ms:assetid: 902d3292-678d-4512-9248-586053cb638b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398734(v=OCS.15)
ms:contentKeyID: 49307439
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar uma senha da conta de autenticação Kerberos authentication em um servidor no Lync Server 2013

 

_**Tópico modificado em:** 2012-01-16_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

Você deve configurar uma senha na conta Kerberos para cada site que possua Servidores front end, servidores Standard Edition e Diretores. Você pode configurar a senha executando o cmdlet **Set-CsKerberosAccountPassword**  Windows PowerShell em um servidor no site (por exemplo, um Servidor Front-End). Para cada site você deve executar o cmdlet **Set-CsKerberosAccountPassword** . O cmdlet configura o IIS (Serviços de Informações da Internet) para o serviço do Serviços Web e define a senha na conta de computador no Serviços de Domínio Active Directory. Um método alternativo, com base no parâmetro usado com o cmdlet, configura o IIS em um servidor enquanto usa outro servidor que tenha sido configurado como origem da senha da conta Kerberos.

Ao usar o cmdlet **Set-CsKerberosAccountPassword** para definir uma senha, o Kerberos define a senha para uma cadeia de caracteres gerada de forma aleatória. Este cmdlet contata todas as instâncias do IIS em todos os sites centrais do Lync Server 2013 para os quais esta conta está atribuída.

## Para definir uma senha para uma conta de autenticação Kerberos

1.  Faça logon em qualquer computador do domínio com o Shell de Gerenciamento do Lync Server instalado como membro do grupo RTCUniversalServerAdmins.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute os dois seguintes comandos:
    
        Set-CsKerberosAccountPassword -UserAccount "Domain\UserAccount"
    
    Por exemplo:
    
        Set-CsKerberosAccountPassword -UserAccount "contoso\KerbAuth"
    
    > [!NOTE]  
    > Você deve especificar o parâmetro UserAccount usando o formato Domínio\Usuário. O formato Usuário@Domínio.extensão não é compatível para referenciar os objetos computador criados para fins de autenticação Kerberos.    
    > [!IMPORTANT]  
    > Depois de aplicar quaisquer alterações para a autenticação Kerberos, como adicionar ou remover uma conta, você deve executar o <strong>Enable-CsTopology</strong> a partir do prompt de comando do Shell de Gerenciamento do Lync Server.
