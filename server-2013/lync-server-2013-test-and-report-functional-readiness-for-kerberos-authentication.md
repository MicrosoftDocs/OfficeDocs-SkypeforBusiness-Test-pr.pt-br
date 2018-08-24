---
title: "Lync Server 2013: Testar e relatar prontidão funcional p/ autentic. Kerberos"
TOCTitle: Testar e relatar prontidão funcional para autenticação Kerberos
ms:assetid: d52c39e5-747d-4f29-88aa-30fd6f26b99c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398925(v=OCS.15)
ms:contentKeyID: 49308235
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Testar e relatar prontidão funcional para autenticação Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2012-01-16_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

É possível usar o cmdlet **Test-CsKerberosAccountAssignment**  Windows PowerShell para testar e informar a prontidão funcional de uma atribuição de site para autenticação Kerberos. Esse comando consulta o site especificado no parâmetro Identity necessário. O parâmetro Report opcional faz com que o cmdlet grave um relatório HTML em C:\\Logs no computador no qual o comando é executado. O parâmetro Verbose opcional mostra as informações de atividade na tela.

## Para testar e relatar a prontidão funcional da autenticação Kerberos de um site

1.  Como membro do grupo RTCUniversalServerAdmins, faça logon em um computador no domínio executando o Lync Server 2013 ou no computador onde as ferramentas administrativas estão instaladas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute o seguinte comando:
    
        Test-CsKerberosAccountAssignment -Identity "site:SiteName" -Report "c:\logs\FileName.htm" -Verbose
    
    Por exemplo:
    
        Test-CsKerberosAccountAssignment -Identity "site:Redmond" -Report "c:\logs\KerberosReport.htm" -Verbose

