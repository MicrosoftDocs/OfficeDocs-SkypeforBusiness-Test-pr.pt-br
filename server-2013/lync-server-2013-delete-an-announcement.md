---
title: Excluir um Comunicado
TOCTitle: Excluir um Comunicado
ms:assetid: 26ea7149-4470-4c22-9bab-8a4065aca44e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687998(v=OCS.15)
ms:contentKeyID: 49886142
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um Comunicado

 

_**Tópico modificado em:** 2012-11-01_

Use o seguinte procedimento para excluir um anúncio que é usado para chamadas de números não atribuídos.

## Para excluir um anúncio

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Lista todos os anúncios em sua organização. Na linha de comando, execute:
    
        Get-CsAnnouncement

4.  Na lista resultante, localize o anúncio que deseja excluir e copie o GUID. Na linha de comando, execute:
    
        Remove-CsAnnouncement -Identity "<Service:service ID/guid>" 
    
    Por exemplo:
    
        Remove-CsAnnouncement -Identity "ApplicationServer:Redmond.contoso.com/1951f734-c80f-4fb2-965d-51807c792b90"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Para obter detalhes sobre mais opções, consulte <a href="get-csannouncement.md">Get-CsAnnouncement</a> e <a href="remove-csannouncement.md">Remove-CsAnnouncement</a>.</td>
    </tr>
    </tbody>
    </table>


## Consulte Também

#### Tarefas

[Criar um comunicado no Lync Server 2013](lync-server-2013-create-an-announcement.md)  

#### Outros Recursos

[Remove-CsAnnouncement](remove-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)

