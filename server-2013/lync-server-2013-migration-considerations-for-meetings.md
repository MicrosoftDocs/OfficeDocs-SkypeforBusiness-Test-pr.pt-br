---
title: Considerações sobre migração para reuniões
TOCTitle: Considerações sobre migração para reuniões
ms:assetid: a9807d58-99a3-4cff-b4c6-74950d106a2b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412800(v=OCS.15)
ms:contentKeyID: 61160126
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Considerações sobre migração para reuniões

 

_**Tópico modificado em:** 2014-02-10_

Os seguintes tópicos são discutidos nesta seção:

  - Alterações em reuniões no Microsoft Lync Server 2013

  - Migrando usuários com base em suas necessidades de conferência

  - Migrando reuniões existentes e conteúdo de reunião

  - Experiência do usuário durante a migração do Lync Server 2010

  - Experiência do usuário durante a migração do Office Communications Server 2007 R2

  - Compatibilidade do Microsoft Lync 2013 com reuniões em versões anteriores de servidor

## Alterações em reuniões no Lync Server 2013

Recursos do **Lync Server 2013. O**   Lync Server 2013 fornece novos recursos de conferência que ficam disponíveis para os usuários depois que suas contas são movidas para o Lync Server 2013 e eles entram com o cliente do Lync 2013. Os novos recursos são destacados em [Novos recursos de conferência no Lync Server 2013](lync-server-2013-new-conferencing-features.md) e [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

**URL da reunião.**   Assim como no Lync Server 2010, todas as reuniões recém-agendadas no Lync Server 2013 têm um prefixo de URL de https:// e as reuniões existentes são migradas junto com as contas de usuário. No entanto, o Lync Server 2013 não oferece suporte à chamada de conferência do Office Communications Server 2007 R2 (prefixo de URL conf://) ou conferência na Web (prefixo de URL meet://). Consulte “Migrando reuniões do Office Communications Server 2007 R2” posteriormente neste tópico para obter mais informações.

**Suporte ao cliente.**   Diferentemente do Lync Server 2010, o Lync Server 2013 não oferece suporte aos clientes do Office Communicator para conferência. Não é possível usar os seguintes clientes para ingressar em reuniões agendadas por meio do Suplemento de Reunião Online para Lync 2013:

  - Office Communicator 2007 R2

  - Microsoft Office Communications Server 2007 R2 Attendant

  - Office Communicator 2007

  - Office Live Meeting 2007

Durante a migração, os usuários do Office Communicator 2007 R2 deverão usar o Lync Web App 2013 para ingressar em reuniões do Lync Server 2013 até seus clientes serem atualizados. Observe que os usuários do Office Communicator 2007 R2 podem continuar usando o cliente existente em relação ao Lync Server 2013 para recursos de presença e mensagens instantâneas, mas não há suporte aos recursos de conferência.


## Migrando usuários com base em suas necessidades de conferência

**Organizadores de reuniões frequentes.**   Considere migrar os organizadores de reuniões frequentes no início do processo para que eles possam tirar proveito dos novos recursos do Lync Server 2013 e do Lync 2013 destacados em [Novos recursos de conferência no Lync Server 2013](lync-server-2013-new-conferencing-features.md) e em [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

**Usuários do Live Meeting.**   Se você estiver migrando do Office Communications Server 2007 R2 e houver usuários que precisarem de recursos de conferência na Web específicos do Live Meeting — em particular o suporte para reuniões grandes e salões — haverá as seguintes opções:

  - Oriente os organizadores a usarem o serviço Live Meeting, se disponível na sua organização.

  - Deixe os organizadores hospedados na versão anterior do Office Communications Server, para que eles possam continuar agendando conferências na Web do Live Meeting baseadas em servidor.

## Migrando reuniões existentes e conteúdo de reunião

## Migrando reuniões do Lync Server 2010

Quando você move um usuário do Lync Server 2010 para o Lync Server 2013, as seguintes informações são movidas com a conta de usuário:

  - Reuniões já agendadas pelo usuário. Incluem diretórios e dados de conferência.

  - O PIN (número de identificação pessoal) do usuário. O PIN atual do usuário continuará funcionando até expirar ou até o usuário selecionar um novo PIN.

No entanto, as seguintes informações de conta do usuário não são movidas para o novo servidor:

  - Conteúdo de reunião, por exemplo, apresentações do PowerPoint, conteúdo de quadro branco e dados de sondagem

Para mover o conteúdo que foi compartilhado nas reuniões, use o parâmetro MoveMeetingContent do cmdlet Move-CsUser. Para obter detalhes sobre como usar esse cmdlet, consulte [Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsUser) na documentação de cmdlets do Lync Server 2013.

## Migrando reuniões do Office Communications Server 2007 R2

As reuniões do Office Communications Server 2007 R2 são chamadas de conferência (prefixo de URL conf://) ou conferências da Web (prefixo de URL meet://). O Lync Server 2013 não oferece suporte a essas conferências conf:// e meet:// anteriores e elas não foram migradas junto com a conta de usuário. Após a migração, você deve instruir os usuários a atualizarem os links de qualquer reunião online que tenham agendado. Eles poderão fazer isso depois de instalar o cliente do Lync 2013 abrindo um convite de reunião programada — que atualiza a URL de reunião — e o reenvio do convite aos participantes.

## Experiência do usuário durante a migração do Lync Server 2010

Esta seção apresenta um resumo da experiência de conferência dos usuários durante a migração do Lync 2010. Para obter mais detalhes sobre como os clientes do Lync Server 2013 podem coexistir e interagir com as versões anteriores de cliente e servidor, consulte [Interoperabilidade do Cliente no Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md).

## Ingressando em reuniões do Lync Server 2010 com um cliente do Lync 2013

Durante a migração do Lync Server 2010, pode haver um período de coexistência quando os usuários ingressam em reuniões do Lync Server 2010 com um cliente do Lync 2013. Esses usuários têm acesso aos recursos de cliente do Lync 2013 com as seguintes exceções:

  - Nas opções de gerenciamento de **Participantes**, que podem ser acessadas apontando-se para o ícone de pessoas na janela de reunião, a opção **Sem Mensagens Instantâneas na Reunião** não funciona.

  - O Modo de Exibição da Galeria não funciona em videoconferências. O usuário visualiza apenas o orador ativo, em vez de todos os oradores. Na lista de opções **Selecionar um Layout**, o **Modo de Exibição de Galeria** está indisponível

  - Por padrão, a lista de participantes é exibida nas videoconferências.

  - As opções de gerenciamento de participantes **Bloquear Destaque de Vídeo** e **Fixar na Galeria** não estão disponíveis quando você clica com o botão direito do mouse na lista de participantes.

## Experiência do usuário durante a migração do Office Communications Server 2007 R2

Esta seção apresenta um resumo da experiência de conferência dos usuários durante a migração do Office Communications Server 2007 R2, antes e depois da instalação do Lync 2013. Para obter mais detalhes sobre como os clientes do Lync Server 2013 podem coexistir e interagir com as versões anteriores de cliente e servidor, consulte [Interoperabilidade do Cliente no Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md).

## Após a migração de conta de usuário, antes da instalação do Lync 2013

Depois que um usuário é migrado para o servidor do Lync Server 2013, mas antes da instalação de novos clientes, os usuários do Office Communicator 2007 R2 podem continuar utilizando seu cliente existente no Lync Server 2013 para recursos de presença e mensagens instantâneas, mas não há suporte para os recursos de conferência.

## Após a migração da conta de usuário, após a instalação do Lync 2013

Quando um usuário migrado instala o Lync 2013, o Suplemento de Reunião Online do Lync 2013 é instalado também. Isso tem os seguintes efeitos:

  - Todas as reuniões agendadas seguintes usam o novo formato de reunião, que utiliza um endereço https://, em vez do endereço legado do Live Meeting meet://.

  - Em uma implantação gerenciada de TI do Lync 2013, o administrador tem a opção de desinstalar o Suplemento de Conferência do Microsoft Office Outlook, que é usado para agendar reuniões de servidor do Live Meeting e baseadas em serviço. No entanto, talvez haja usuários que precisem continuar agendando reuniões de serviço do Live Meeting. Nesse caso, é possível permitir a coexistência de ambos os suplementos.

## Reuniões com organizações federadas que usam clientes anteriores

Os usuários em organizações federadas que estiverem usando o Microsoft Office Communicator 2007 não poderão ingressar em reuniões do Lync Server 2013 na sua organização se essas reuniões estiverem bloqueadas pelo organizador. Você precisa reagendar essas reuniões no Lync Server 2013 de modo que quando os participantes federados ingressarem na reunião usando a nova URL de reunião https://, eles possam usar o Lync Web App.

