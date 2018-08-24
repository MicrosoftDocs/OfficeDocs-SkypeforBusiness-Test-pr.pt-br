---
title: Mover os usuários restantes para o Lync Server 2013
TOCTitle: Mover os usuários restantes para o Lync Server 2013
ms:assetid: 0eb990f0-f720-47a7-aaee-437fbd4c4c33
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687968(v=OCS.15)
ms:contentKeyID: 49886100
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover os usuários restantes para o Lync Server 2013

 

_**Tópico modificado em:** 2012-09-26_

É possível mover os usuários para a nova implantação do Lync Server 2013 usando o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server. Você deve cumprir alguns requisitos para assegurar uma transição suave para o Lync Server 2013. Para obter detalhes sobre os pré-requisitos para concluir os procedimentos deste tópico, consulte [Configurar clientes para migração](configure-clients-for-migration_1.md). Para obter informações sobre as etapas detalhadas de movimentação de usuários, consulte [Fase 6: Mover usuários ao pool piloto](phase-6-move-users-to-the-pilot-pool.md).

> [!IMPORTANT]  
> Não é possível usar o snap-in Usuários e Computadores do Active Directory ou as ferramentas administrativas do Microsoft Office Communications Server 2007 R2 para mover usuários de seu ambiente herdado para o Lync Server 2013.

> [!IMPORTANT]  
> O cmdlet <strong>Move-CsLegacyUser</strong> exige que os nomes de usuários sejam formados adequadamente e não tenham espaços à esquerda ou direita. Você não pode mover uma conta de usuário usando o cmdlet <strong>Move-CsLegacyUser</strong> se ele tiver espaços à esquerda ou direita.

Quando você mover um usuário para um pool do Lync Server 2013, os dados do usuário são movidos para o banco de dados back-end associado ao novo pool.

> [!IMPORTANT]  
> Isso inclui as reuniões ativas criadas pelo usuário herdado. Por exemplo, se um usuário antigo configurou uma conferência <strong>minha reunião</strong> , ela ainda estará disponível no novo pool do Lync Server 2013. Os detalhes para acessá-la ainda serão as mesmas <strong>URL e ID da conferência</strong> . A única diferença é que agora a conferência será hospedada no pool do Lync Server 2013 e não no pool do Office Communications Server 2007 R2.

> [!NOTE]  
> A hospedagem de usuários no Lync Server 2013 não exige a implantação de clientes atualizados ao mesmo tempo. A nova funcionalidade estará disponível aos usuários somente após a atualização para o novo software cliente.

## Tarefa pós-migração

1.  Depois de mover os usuários, verifique a política de conferência atribuída a eles.

2.  Para garantir que as reuniões organizadas pelos usuários hospedados no Lync Server 2013 funcionem perfeitamente com os usuários federados hospedados no Office Communications Server 2007 R2, a política de conferência atribuída aos usuários migrados deve permitir participantes anônimos.

3.  As diretivas de conferência que permitem participantes anônimos devem **Permitir que participantes convidem usuários anônimos** selecionados no Painel de Controle do Lync Server 2013 e que tenha **AllowAnonymousParticipantsInMeetings** definido como **True** na saída do cmdlet **Get-CsConferencingPolicy** no Shell de Gerenciamento do Lync Server.

4.  Para obter detalhes sobre a configuração da diretiva de conferência usando o Shell de Gerenciamento do Lync Server, consulte [Set-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsConferencingPolicy) na documentação do Shell de Gerenciamento do Lync Server.

