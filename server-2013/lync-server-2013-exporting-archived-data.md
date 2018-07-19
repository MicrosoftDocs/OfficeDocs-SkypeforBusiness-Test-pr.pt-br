---
title: Exportando dados arquivados do Lync Server 2013
TOCTitle: Exportando dados arquivados do Lync Server 2013
ms:assetid: 09450d54-769b-4741-924b-e390664d506f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204657(v=OCS.15)
ms:contentKeyID: 49305815
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exportando dados arquivados do Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

Os dados arquivados em bancos de dados de Arquivamento não estão em um formato legível ou com possibilidade de pesquisa, mas é possível usar o cmdlet Export-CsArchivingData para extrair registros do banco de dados e salvá-los como um arquivo do Outlook Electronic Mail (EML). Para obter detalhes sobre como exportar dados arquivados, consulte [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData) na documentação Operações.

Se você habilitar a integração com o Microsoft Exchange, os dados serão arquivados em repositórios do Exchange 2013. Os dados arquivados no Exchange 2013 podem ser pesquisados e descobertos. Para obter detalhes sobre suporte para comunicações integradas para Exchange 2013 e Lync Server 2013, consulte [Suporte a Servidor Exchange e à integração com SharePoint no Lync Server 2013](lync-server-2013-exchange-and-sharepoint-integration-support.md) na documentação de Suporte. Para obter detalhes sobre como acessar dados arquivados no Exchange, consulte a documentação do Exchange 2013.

## Exportando dados de arquivamento usando os cmdlets Shell de Gerenciamento do Lync Server

Os dados de arquivamento podem ser exportados usando o cmdlet Export-CSArchivingData. Esse cmdlet podem ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

**Exportando dados de arquivamento**

  - Este comando exporta todos os dados de arquivamento gravados no banco de dados de arquivamento atl-sql-001.litwareinc.com desde 1 de junho de 2012. O arquivo de saída resultante será armazenado na pasta C:\\ArchivingExports.
    
        Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports"

**Exportando dados de arquivamento para um único usuário**

  - O comando a seguir exporta dados de arquivamento para um único usuário: kenmyer@litwareinc.com. Isso é feito incluindo o parâmetro UserUri seguido pelo endereço SIP do usuário. Por exemplo:
    
        Export-CsArchivingData -Identity "ArchivingDatabase:atl-sql-001.litwareinc.com" -StartDate 6/1/2012 -OutputFolder "C:\ArchivingExports" -UserUri "sip:kenmyer@litwareinc.com"

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData).

## Consulte Também

#### Conceitos

[Suporte a Servidor Exchange e à integração com SharePoint no Lync Server 2013](lync-server-2013-exchange-and-sharepoint-integration-support.md)  

#### Outros Recursos

[Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData)  
[Gerenciando Arquivamento do Lync Server 2013](lync-server-2013-managing-archiving.md)

