---
title: 'Lync Server 2013: Re-ativar servidor após o Assistente de Configuração de Segurança fechar portas no IIS'
TOCTitle: Re-ativar servidor após o Assistente de Configuração de Segurança fechar portas no IIS
ms:assetid: cb8e17cf-f8c1-4099-b63b-c242d656c26a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398851(v=OCS.15)
ms:contentKeyID: 49308125
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Re-ativar servidor após o Assistente de Configuração de Segurança fechar portas no IIS

 

_**Tópico modificado em:** 2012-10-01_

Algumas funções do Lync Server 2013 executam o Serviços Web na porta 4443 do IIS (Serviços de Informações da Internet). A execução do Assistente de Implantação do Lync Server, de Bootstrapper.exe ou o uso do cmdlet **Enable-CsComputer** cria uma exceção no firewall e abre a porta. Se você então executar o Assistente de Configuração de Segurança do Windows Server 2008 R2 (ou outros scripts de segurança), a porta 4443 será bloqueada, e os clientes externos não conseguirão contatar o Serviços Web. Para reabrir a porta, você pode modificar a exceção do firewall diretamente ou reativar o servidor.

## Para reativar o servidor usando o Assistente de Implantação

1.  Na página Assistente de Implantação do Lync Server, clique em **Executar** ao lado de **Etapa 2: Instalar ou Remover Componentes do Lync Server** .

2.  Na página **Instalar componentes do Lync Server** , clique em **Avançar** .

3.  Na página **Executando Comandos** , quando o status da tarefa é exibido como concluído, clique em **Concluir** .
    
    > [!NOTE]  
    > Também é possível usar bootstrapper.exe ou <strong>Enable-CsComputer</strong> para reativar o servidor.
