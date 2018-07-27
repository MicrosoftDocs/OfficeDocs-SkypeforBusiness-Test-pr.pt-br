---
title: Migrar grupos de resposta
TOCTitle: Migrar grupos de resposta
ms:assetid: 43741ae7-c871-4573-b660-f2f5febc0856
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204854(v=OCS.15)
ms:contentKeyID: 49306556
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar grupos de resposta

 

_**Tópico modificado em:** 2013-09-23_

Depois que seus usuários são movidos para pools Lync Server 2013, você pode migrar os grupos de resposta. Migrar grupos de resposta inclui copiar grupos de agente, fila, fluxos de trabalho, arquivos de áudio e objetos de contato Grupo de Resposta de implantações de legado para o pool Lync Server 2013. Após migrar seus grupos de resposta de legado, as chamadas par aos grupos de resposta são manipulados pelo Aplicativo Grupo de Resposta no pool Lync Server 2013. Chamadas para grupos de resposta não são mais manipulados por pools de legado.

> [!NOTE]  
> Apesar de ser possível migrar grupos de resposta antes de mover todos os usuários para o pool Lync Server 2013, recomendamos que você mova os usuários primeiro. Particularmente, os usuários que são agentes do grupo de resposta não irão ter total funcionalidade dos novos recursos até serem movidos para o pool Lync Server 2013.

Antes de migrar os grupos de resposta, você deve possuir um pool Lync Server 2013 implantado que inclua o Aplicativo Grupo de Resposta. O Aplicativo Grupo de Resposta está instalado e ativado por padrão ao implantar o Enterprise Voice. Você pode certificar-se de que o Aplicativo Grupo de Resposta está instalado executando o cmdlet **Get-CsService –ApplicationServer**.

> [!NOTE]  
> Você pode criar novos grupos de resposta Lync Server 2013 no pool Lync Server 2013 antes de migrar os grupos de resposta de legado.

Para migrar grupos de resposta de um pool de legado para o Lync Server 2013, excute o cmdlet **Move-CsRgsConfiguration**.

> [!IMPORTANT]  
> O cmdlet de migração Grupo de Resposta move a configuração Grupo de Resposta para todo o pool. Você não pode selecionar grupos específicos, filas ou grupos de trabalho para migrar.

Após migrar os grupos de resposta, você precisará utilizar cmdlets Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server para verificar se todos os grupos de agente, filas e fluxos de trabalho foram movidos com sucesso.

Ao migrar grupos de resposta, os grupos de resposta Lync Server 2010 não são removidos. Quando você gerencia grupos de resposta após a migração utilizando o Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server, você pode ver tanto os grupos de resposta Lync Server 2010 quanto os grupos de resposta Lync Server 2013. Você deve aplicar atualizações apenas aos grupos de resposta Lync Server 2013. Os grupos de resposta Lync Server 2010 são retidos apenas para propósitos de reversão.


> [!WARNING]
> Após a conclusão da migração e a criação de novos grupos de resposta, o Painel de Controle do Lync Server e o Shell de Gerenciamento do Lync Server exibirão as versões do Lync Server 2010 e do Lync Server 2013 de cada grupo de respostas. Não use Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server para remover os grupos de respostas do Lync Server 2010. Se você não remover um, o grupo de resposta correspondente criado durante a migração parará de funcionar. Os grupos de respostas do Lync Server 2010 serão removidos quando você desprogramar o pool do Lync Server 2010.



> [!IMPORTANT]  
> Recomendamos que você não remova qualquer dado da implantação anterior até que você descomissione o pool. Além disso, recomendamos fortemente que você exporte os grupos de resposta imediatamente após migrá-lo. Se um grupo de resposta Lync Server 2010 precisar ser removido, você pode então restaurar os grupos de resposta do backup para obter grupos de resposta Lync Server 2013 em execução novamente.

Lync Server 2013apresenta um novo recurso Grupo de Resposta chamado **Tipo de fluxo de trabalho** . O **Tipo de fluxo de trabalho** pode ser **Gerenciado** ou **Não gerenciado** . Todos os grupos de resposta são migrados com o **Tipo de fluxo de trabalho** definido para **Não gerenciado** e com uma lista Gerenciador vazia.

ao executar o cmdlet **Move-CsRgsConfiguration**, os grupos de agente, filas, fluxos de trabalho e arquivos de áudio permanecem no pool de legado para propósitos de reversão. Caso você precise fazer uma reversão para o pool de legado, entretanto, você precisará executar o cmdlet **Move-CsApplicationEndpoint** para mover objetos de contato de volta para o pool de legado.

O procedimento a seguir para migrar configurações Grupo de Resposta presume que você possui uma relação um-para-um entre os pools de legado e os pools Lync Server 2013. Se você planeja consolidar ou separar pools durante a migração e implantação, será necessário planejar qual pool de legado mapeia a qual pool Lync Server 2013.

## Para migrar configurações Grupo de Resposta

1.  Efetue login no computador com uma conta que é membro do grupo RTCUniversalServerAdmins ou possui direitos de administrador e permissões equivalentes.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    Por exemplo:
    
        Move-CsRgsConfiguration -Source lync-old.contoso.net -Destination lync-new.contoso.net

4.  Após migrar os grupos de resposta e agentes para o pool Lync Server 2013, o URL que os agentes utilizam para entrar e sair é um URL Lync Server 2013 e está disponível a partir do menu **Ferramentas** . Lembre os agentes de atualizar qualquer referência, como indicadores, para o novo URL.

## Para verificar a migração do Grupo de respostas usando o Painel de Controle do Lync Server

1.  Efetue login no computador com uma conta que seja membro do grupo RTCUniversalReadOnlyAdmins ou ao menos membro da função CsViewOnlyAdministrator.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  No painel de navegação à esquerda, clique em **Grupos de Resposta** .

4.  Na guia **Fluxo de trabalho** , verifique se todos os fluxos de trabalho no seu ambiente Lync Server 2010 estão incluídos na lista.

5.  Clique na guia **Fila** e verifique se todas as filas no seu ambiente Lync Server 2010 estão incluídas na lista.

6.  Clique na guia **Grupo** e verifique se todos os grupos de agente no seu ambiente Lync Server 2010 estão incluídos na lista.

## Para verificar a migração do Grupo de Resposta utilizando Shell de Gerenciamento do Lync Server

1.  Efetue login no computador com uma conta que seja membro do grupo RTCUniversalReadOnlyAdmins ou ao menos membro da função CsViewOnlyAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.
    
    Para detalhes sobre os cmdlets a seguir, execute:
    
        Get-Help <cmdlet name> -Detailed

3.  Execute:
    
        Get-CsRgsAgentGroup

4.  Verifique se todos os grupos de agente no seu ambiente Lync Server 2010 estão incluídos na lista.

5.  Execute:
    
        Get-CsRgsQueue

6.  Verifique se todas as filas no seu ambiente Lync Server 2010 estão incluídos na lista.

7.  Execute:
    
        Get-CsRgsWorkflow

8.  Verifique se todos os fluxos de trabalho no seu ambiente Lync Server 2010 estão incluídos na lista.

