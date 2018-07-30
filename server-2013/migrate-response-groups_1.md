---
title: Migrar grupos de resposta
TOCTitle: Migrar grupos de resposta
ms:assetid: 5c07bf4b-ad8a-4b83-b970-7d933bb7c4ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204931(v=OCS.15)
ms:contentKeyID: 49306832
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar grupos de resposta

 

_**Tópico modificado em:** 2012-10-19_

Depois que seus usuários forem transferidos para pools do Lync Server 2013, você poderá migrar seus grupos de resposta. A migração de grupos de resposta inclui a cópia de grupos de agentes, filas, fluxos de trabalho e arquivos de áudio, bem como a transferência de objetos de contato de Grupo de Resposta da implantação antiga para o pool do Lync Server 2013. Depois que você migrar seus grupos de resposta antigos, as chamadas aos grupos de resposta serão processadas pelo Aplicativo Grupo de Resposta no pool do Lync Server 2013. As chamadas aos grupos de resposta não serão mais processadas pelo pool antigo.

> [!NOTE]  
> Apesar de ser possível migrar grupos de resposta antes de mover todos os usuários para o pool Lync Server 2013, recomendamos que você mova os usuários primeiro. Particularmente, os usuários que são agentes do grupo de resposta não irão ter total funcionalidade dos novos recursos até serem movidos para o pool Lync Server 2013.

Antes de migrar os grupos de resposta, você deve possuir um pool Lync Server 2013 implantado que inclua o Aplicativo Grupo de Resposta. O Aplicativo Grupo de Resposta está instalado e ativado por padrão ao implantar o Enterprise Voice. Você pode certificar-se de que o Aplicativo Grupo de Resposta está instalado executando o cmdlet **Get-CsService–ApplicationServer**.

> [!NOTE]  
> Você pode criar novos grupos de resposta Lync Server 2013 no pool Lync Server 2013 antes de migrar os grupos de resposta de legado.

Para migrar grupos de resposta de um pool antigo para o Lync Server 2013, você deve executar o cmdlet **Move-CsRgsConfiguration**. Para poder executar o **Move-CsRgsConfiguration**, primeiro você precisa instalar o pacote de interfaces de compatibilidade com versões anteriores WMI (Instrumentação de Gerenciamento do Windows). Instale esse aplicativo executando o OCSWMIBC.msi. Você pode encontrar o OCSWMIBC.msi na pasta Setup da mídia de instalação.

> [!IMPORTANT]  
> O cmdlet de migração Grupo de Resposta move a configuração Grupo de Resposta para todo o pool. Você não pode selecionar grupos específicos, filas ou grupos de trabalho para migrar.

Depois que você migrar os grupos de resposta, precisará atualizar a URL que os agentes formais usam para entrar e sair de seus grupos de resposta e usar os cmdlets do Painel de Controle do Lync Server ou do Shell de Gerenciamento do Lync Server para verificar se todos os fluxos de trabalho, filas e grupos de agente foram transferidos com êxito.


> [!WARNING]
> Quando você migra grupos de resposta, os grupos de resposta do Office Communications Server 2007 R2 não são removidos. Não remova os grupos de resposta do Office Communications Server 2007 R2. Se você remover um grupo de resposta do Office Communications Server 2007 R2, os grupos de resposta do Lync Server 2013 pararão de funcionar.



> [!IMPORTANT]  
> Recomendamos que você não remova dados da sua implantação anterior até suspender o pool. Além disso, é altamente recomendável que você exporte os grupos de resposta imediatamente após a migração. Se um grupo de resposta do Office Communications Server 2007 R2 for removido, você poderá restaurar seus grupos de resposta do backup para fazer os grupos de resposta do Lync Server 2013 voltarem a funcionar.

ao executar o cmdlet **Move-CsRgsConfiguration**, os grupos de agente, filas, fluxos de trabalho e arquivos de áudio permanecem no pool de legado para propósitos de reversão. Caso você precise fazer uma reversão para o pool de legado, entretanto, você precisará executar o cmdlet **Move-CsApplicationEndpoint** para mover objetos de contato de volta para o pool de legado.

> [!IMPORTANT]  
> Recomendamos que você não exclua dados de grupos de resposta do pool antigo até suspendê-lo.

O procedimento de migração de configurações do Grupo de Resposta a seguir pressupõe uma relação um-para-um entre seus pools antigos e os pools do Lync Server 2013. Se você pretende consolidar ou dividir pools durante a migração e implantação, precisará planejar qual pool antigo será mapeado para qual pool do Lync Server 2013.

## Para migrar configurações do Grupo de Resposta

1.  Localize o OCSWMIBC.msi na pasta Setup da mídia de instalação e instale-o.

2.  Efetue login no computador com uma conta que é membro do grupo RTCUniversalServerAdmins ou possui direitos de administrador e permissões equivalentes.

3.  Abra o Shell de Gerenciamento do Lync Server.

4.  Na linha de comando, digite o seguinte:
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    Por exemplo:
    
        Move-CsRgsConfiguration -Source pool01.contoso.net -Destination pool02.contoso.net

5.  Caso tenha implantado a guia Grupo de Resposta no Microsoft Office Communicator 2007 R2 em seu ambiente do Office Communications Server 2007 R2, remova a guia do arquivo tabs.xml do Office Communicator 2007 R2.
    
    > [!NOTE]  
    > Agentes formais usavam a guia Grupo de Resposta para entrar em seus grupos de resposta para poderem receber chamadas. Se você implantou a guia Grupo de Resposta, escolheu o local do arquivo tabs.xml do Office Communicator 2007 R2 quando o implantou.

6.  Forneça aos usuários a URL atualizada de que os agentes precisam para entrar e sair de seus grupos de resposta.
    
    > [!NOTE]  
    > A URL normalmente é https://webpoolFQDN/RgsClients/Tab.aspx, na qual <em>webpoolFQDN</em> é o FQDN (nome de domínio totalmente qualificado) do pool da Web associado ao pool que você migrou para o Lync Server 2013.    
    > [!NOTE]  
    > Esta etapa não é necessária depois que os usuários atualizam para o Lync 2013, pois a URL está disponível no menu <strong>Ferramentas</strong> no Lync.

## Para confirmar a migração do grupo de resposta usando o Painel de Controle do Lync Server

1.  Abra o Painel de Controle do Lync Server.

2.  No painel de navegação à esquerda, clique em **Grupos de Resposta** .

3.  Na guia **Fluxo de trabalho** , verifique se todos os fluxos de trabalho no seu ambiente Office Communications Server 2007 R2 estão incluídos na lista.

4.  Clique na guia **Fila** e verifique se todas as filas no seu ambiente Office Communications Server 2007 R2 estão incluídas na lista.

5.  Clique na guia **Grupo** e verifique se todos os grupos de agente no seu ambiente Office Communications Server 2007 R2 estão incluídos na lista.

## Para confirmar a migração do grupo de resposta usando o cmdlets

1.  Abra o Shell de Gerenciamento do Lync Server.
    
    Para detalhes sobre os cmdlets a seguir, execute:
    
        Get-Help <cmdlet name> -Detailed

2.  Na linha de comando, digite o seguinte:
    
        Get-CsRgsAgentGroup

3.  Verifique se todos os grupos de agente no seu ambiente Office Communications Server 2007 R2 estão incluídos na lista.

4.  Na linha de comando, digite o seguinte:
    
        Get-CsRgsQueue

5.  Verifique se todas as filas no seu ambiente Office Communications Server 2007 R2 estão incluídos na lista.

6.  Na linha de comando, digite o seguinte:
    
        Get-CsRgsWorkflow

7.  Verifique se todos os fluxos de trabalho no seu ambiente Office Communications Server 2007 R2 estão incluídos na lista.

