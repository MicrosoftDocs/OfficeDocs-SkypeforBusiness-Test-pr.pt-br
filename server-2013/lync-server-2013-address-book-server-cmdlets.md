---
title: Cmdlets do servidor de catálogo de endereços
TOCTitle: Cmdlets do servidor de catálogo de endereços
ms:assetid: 33da45da-3c57-4d04-9679-f0e5a0cfd37e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg415643(v=OCS.15)
ms:contentKeyID: 49306332
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets do servidor de catálogo de endereços

 

_**Tópico modificado em:** 2016-12-08_

Servidores de Catálogo de Endereços são intermediários entre os Serviços de Domínio Active Directory e o Microsoft Lync Server 2013. O Servidor de Catálogo de Endereços garante que as informações do usuário armazenadas no Lync Server 2013 estejam sincronizadas com as informações do usuário armazenadas no Active Directory. Isso é feito pela sincronização periódica dos arquivos do Catálogo de Endereços com as informações armazenadas no banco de dados do Usuário. Na sequência, o Lync Server inclui vários cmdlets para gerenciamento dos Servidores de Catálogo de Endereços.

## Cmdlets do Servidor de Catálogo de Endereços

Não é possível definir as configurações do Servidor de Catálogo de Endereços no Painel de Controle do Lync Server. Windows PowerShell é a principal ferramenta para gerenciar essas configurações. Veja a seguir uma lista de cmdlets que se relacionam diretamente com o gerenciamento do Servidor de Catálogo de Endereços:

**Servidor do Catálogo de Endereços**

  -   
    [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

  -   
    [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)

  -   
    [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

  -   
    [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

<!-- end list -->

  -   
    [Update-CsAddressBook](update-csaddressbook.md)

  -   
    [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)

<!-- end list -->

  -   
    [Test-CsAddressBookService](test-csaddressbookservice.md)

  -   
    [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

## Consulte Também

#### Outros Recursos

[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x416)

