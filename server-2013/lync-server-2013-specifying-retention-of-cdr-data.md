---
title: Especificar a retenção de dados de CDR
TOCTitle: Especificar a retenção de dados de CDR
ms:assetid: c0fd6056-87bc-4136-902a-f1b37cd3a1ca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182581(v=OCS.15)
ms:contentKeyID: 49307987
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Especificar a retenção de dados de CDR

 

_**Tópico modificado em:** 2013-02-23_

Por padrão, os dados de CDR (registro de detalhes das chamadas) são purgados após 60 dias. É possível usar as configurações da página **Registro de Detalhes das Chamadas** para manter os dados por um período maior ou menor. Se você desabilitar o CDR, os dados que foram capturados antes da desabilitação do CDR também poderão ser purgados.

> [!NOTE]  
> Você deve configurar o CDR e a QoE (Qualidade da Experiência) para reter os dados durante o mesmo número de dias. Cada chamada nos CDRs (relatórios de detalhes de chamada), disponível na página da web de Relatórios do Monitoring Serve, inclui informações de CDR e QoE. Se a duração da limpeza de CDR e QoE for diferente, algumas chamadas poderão incluir apenas dados de CDR, enquanto outras poderão incluir apenas dados de QoE.

Use o procedimento a seguir para definir as configurações de limpeza de dados de CDR.

## Para especificar a retenção de dados de CDR

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Monitoramento e Arquivamento** e clique em **Registro de Detalhes de Chamada**.

4.  Na página **Registro de Detalhes de Chamada**, clique no site apropriado na tabela, clique em **Editar** e em **Mostrar Detalhes**.

5.  Para ativar a limpeza, selecione **Habilitar limpeza CDRs**.

6.  Em **Manter CDRs por um período máximo (dias):** selecione o número máximo de dias que os registros de detalhes de chamada devem ser retidos.

7.  Em **Manter dados de relatório de erros por um período máximo de (dias):** selecione o número máximo de dias que os relatórios de erros devem ser retidos.

8.  Clique em **Confirmar**.

## Para especificar a retenção CDR pelos cmdlets do Shell de Gerenciamento do Lync Server

É possível criar configurações de retenção CDR usando o Windows PowerShell e o cmdlet Set-CsCdrConfiguration. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para especificar a retenção de CDR para um local específico

  - Este comando habilita a exclusão de dados CDR para o local Redmond e configura o local para manter os dados CDR e os dados do relatório de erro por 20 dias.
    
        Set-CsCdrConfiguration -Identity "site:Redmond" -EnablePurging -KeepCallDetailForDays 20 -KeepErrorReportForDays 20

## Para especificar a retenção CDR para vários locais

  - Este comando configura a retenção CDR para todas as definições de configuração CDR em uso em uma organização.
    
        Get-CsCdrConfiguration | Set-CsCdrConfiguration-EnablePurging -KeepCallDetailForDays 20 -KeepErrorReportForDays 20

Para obter mais informações, consulte o tópico de ajuda do cmdlet do [Set-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCdrConfiguration).

## Consulte Também

#### Outros Recursos

[CDR (Gravação de Detalhes das Chamadas) no Lync Server 2013](lync-server-2013-call-detail-recording-cdr.md)

