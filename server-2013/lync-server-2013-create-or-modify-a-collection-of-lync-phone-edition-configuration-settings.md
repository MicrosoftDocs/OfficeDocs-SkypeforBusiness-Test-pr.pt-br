---
title: Criar ou Modificar um Conjunto de Configurações de Lync Phone Edition
TOCTitle: Criar ou Modificar um Conjunto de Configurações de Lync Phone Edition
ms:assetid: 6cf714af-8f57-4a71-89ad-0a776302b2ba
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688086(v=OCS.15)
ms:contentKeyID: 49886255
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou Modificar um Conjunto de Configurações de Lync Phone Edition

 

_**Tópico modificado em:** 2013-02-23_

Ao instalar o Lync Server, você obtém um conjunto global de configurações de Lync Phone Edition. Essas configurações aplicam-se a todos os dispositivos que executam o Lync Phone Edition em sua implantação. Você pode alterar essas configurações a qualquer momento. Também é possível configurar um novo conjunto de configurações aplicáveis aos dispositivos em um site específico. As configurações de site têm prioridade sobre as configurações globais.

As configurações consistem de nome do conjunto, escopo (global ou site), configuração de segurança SIP, nível de log, nível de QoS (qualidade de serviço) de voz, configuração de bloqueio de telefone e detalhes de bloqueio de telefone, isto é, a) o tamanho do PIN (número de identificação pessoal) de desbloqueio e b) por quanto tempo o telefone deve ficar ocioso antes de bloquear.

## Para criar um conjunto de configurações do Lync Phone Edition ou editar configurações de um conjunto existente

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Configuração dos Dispositivos**.

4.  Na página **Configuração dos Dispositivos**, siga um destes procedimentos:
    
      - Para criar um novo conjunto de configurações do Lync Phone Edition, clique em **Novo**, selecione um site, clique em **OK**, revise as configurações padrão e, se desejar, faça alterações.
    
      - Para editar qualquer configuração de um conjunto existente, clique no menu **Editar**, clique em **Mostrar detalhes** e faça as alterações.
        

        > [!TIP]
        > Para voltar a usar as configurações padrão do conjunto global, clique no conjunto global, clique no menu <STRONG>Editar</STRONG>, clique em <STRONG>Excluir</STRONG> e clique em <STRONG>OK</STRONG>. Essa ação não excluirá o conjunto global, apenas irá restaurar os padrões das configurações.



5.  Clique em **Confirmar**.

## Para criar novas configurações do Lync Phone Edition usando os cmdlets do Shell de Gerenciamento do Lync Server

Você também pode criar configurações do Lync Phone Edition (somente no escopo de site) usando Shell de Gerenciamento do Lync Server e o cmdlet **New-CsUCPhoneConfiguration**. Você pode executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para criar novas configurações do Lync Phone Edition que usam valores padrão

  - Este comando cria um novo conjunto de configurações de telefone UC para o site Redmond:
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond"
    
    Como nenhum parâmetro (além de Identidade, que é obrigatório) foi especificado no comando anterior, o novo conjunto de configurações usará os valores padrão para todas as suas propriedades.

## Para alterar o valor de apenas uma propriedade ao criar novas configurações do Lync Phone Edition

  - Para criar configurações que usam valores de propriedade diferentes, basta incluir o parâmetro e valor de parâmetro adequados. Por exemplo, para criar um conjunto de configurações de telefone UC que, por padrão, exijam bloqueio do telefone, use um comando como este:
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True

## Para alterar valores de várias propriedades ao criar novas configurações do Lync Phone Edition

  - É possível modificar valores de várias propriedades incluindo vários parâmetros. Por exemplo, este comando aplica o bloqueio do telefone a também define um tamanho mínimo de PIN de oito dígitos:
    
        New-CsUCPhoneConfiguration -Identity "site:Redmond" -EnforcePhoneLock $True -MinPhonePinLength 8

Para obter detalhes, consulte [New-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsUCPhoneConfiguration).

## Consulte Também

#### Tarefas

[Excluir um conjunto existente das configurações do Lync Phone Edition](lync-server-2013-delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)  
[Configurações de segurança para o Lync Phone Edition](lync-server-2013-configure-security-settings-for-lync-phone-edition.md)  
[Aplicar Bloqueio de Telefone](lync-server-2013-enforce-phone-locking.md)

