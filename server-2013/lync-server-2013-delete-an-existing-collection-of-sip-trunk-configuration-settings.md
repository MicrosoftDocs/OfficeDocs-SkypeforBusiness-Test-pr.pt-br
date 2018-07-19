---
title: Excluir um conjunto existente das configurações do Tronco SIP no Lync Server 2013
TOCTitle: Excluir um conjunto existente das configurações do Tronco SIP no Lync Server 2013
ms:assetid: 3b25f14d-884b-42dd-a866-460d276d3e43
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688024(v=OCS.15)
ms:contentKeyID: 49886179
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto existente das configurações do Tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

As definições da configuração do tronco SIP determinam a relação e os recursos entre um servidor de mediação e o gateway PSTN (Rede Telefônica Pública Comutada), um IP-PBX (central pública de comutação telefônica) ou um SBC (controlador de borda da sessão) no provedor de serviços. Essas configurações especificam:

  - Se o desvio de mídia deve ser habilitado nos troncos.

  - As condições nas quais os pacotes do protocolo RTCP (protocolo de controle de transporte em tempo real) são enviados.

  - Se a proteção da criptografia do protocolo SRTP é exigida ou não em cada tronco.

Quando o Microsoft Lync Server 2013 é instalado, um conjunto global de definições de configuração do tronco SIP é criado para você. Este conjunto global de configurações não pode ser excluído. No entanto, é possível usar o cmdlet Painel de Controle do Lync Server ou o [Remove-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsTrunkConfiguration) para "redefinir" as propriedades do conjunto global para seus valores padrão. Por exemplo, se a propriedade Enable3pccRefer foi definida como Verdadeira, quando o conjunto global for redefinido, a propriedade Enable3pccRefer será revertida para o valor padrão Falso.

Os administradores também podem criar definições personalizadas de configuração de tronco no escopo do site ou escopo do serviço (para um gateway PSDN individual); essas configurações padrão podem ser removidas. Ao remover essas configurações padrão, lembre-se do seguinte:

  - Se você remover as configurações do escopo do serviço, o tronco SIP gerenciado por essas configurações será gerenciado pelas configurações aplicadas ao site, caso existam. Se as configurações não existirem, esses troncos serão então gerenciados pelo conjunto global de definições de configuração do tronco.

  - Se você remover as configurações pertencentes ao escopo do site, todos os troncos SIP gerenciados por essas configurações serão então gerenciados pelo conjunto global de definições de configuração do tronco.

## Removendo definições de configuração do tronco usando o Painel de Controle do Lync Server

1.  No Painel de Controle do Lync Server, clique em **Roteamento de Voz** e, então, em **Configuração do Tronco**.

2.  Na guia **Configuração do Tronco**, selecione o conjunto de definições de configuração do tronco SIP a ser excluído, clique em **Editar** e, então, clique em **Excluir**. Para excluir vários conjuntos na mesma operação, clique no primeiro conjunto a ser excluído, mantenha pressionada a tecla Ctrl e clique em todos os outros conjuntos que deseja remover.

3.  A propriedade **Estado** do conjunto será atualizada para **Não Confirmado**. Para confirmar as alterações e excluir o conjunto, clique em **Confirmar** e, depois, clique em **Confirmar Tudo**.

4.  Na caixa de diálogo **Definições de Configuração de Voz Não Confirmadas**, clique em **OK**.

5.  Na caixa de diálogo **Painel de Controle do Microsoft Lync Server 2013**, clique em **OK**.

6.  Se mudar de ideia e decidir não excluir o conjunto, clique em **Confirmar** e, depois, em **Cancelar todas as alterações não confirmadas**. Quando a caixa de diálogo **Painel de Controle do Microsoft Lync Server 2013** for exibida, clique em **OK**.

## Removendo definições de configuração do tronco usando os cmdlets do Lync Server PowerShell

As definições de configuração do tronco também podem ser excluídas usando o Windows PowerShell e o cmdlet Remove-CsTrunkConfiguration. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Removendo um conjunto especificado de configurações

  - O seguinte comando remove as definições de configuração do tronco aplicadas ao site Redmond:
    
        Remove-CsTrunkConfiguration -Identity site:Redmond

## Removendo todos os conjuntos aplicados ao escopo do site

  - Este comando remove todas as definições de configuração do tronco aplicadas ao escopo do serviço:
    
        Get-CsTrunkConfiguration -Filter "service:*" | Remove-CsTrunkConfiguration

## Removendo todos os conjuntos em que o desvio de mídia está habilitado

  - O seguinte comando remove todas as definições de configuração do tronco em que o desvio de mídia está habilitado:
    
        Get-CsTrunkConfiguration | Where-Object {$_.EnableBypass -eq $True} | Remove-CsTrunkConfiguration

Para obter mais informações, consulte o tópico do cmdlet [Remove-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsTrunkConfiguration).

