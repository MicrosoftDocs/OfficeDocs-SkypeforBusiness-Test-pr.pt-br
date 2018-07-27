---
title: Gerenciando a QoS (Qualidade de Serviço) no Lync Server 2013
TOCTitle: Gerenciando a QoS (Qualidade de Serviço) no Lync Server 2013
ms:assetid: ab1051c3-8380-4d72-86df-37a61b1e4a41
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg405409(v=OCS.15)
ms:contentKeyID: 49307777
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando a QoS (Qualidade de Serviço) no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A Qualidade de Serviço (QoS) é uma tecnologia de rede usada em algumas organizações para ajudar a fornecer a melhor experiência ao usuário final para comunicações de áudio e vídeo. a QoS é usada mais frequentemente em rede com largura de banda limitada: com uma grande número de pacotes de rede para uma quantidade relativamente pequena de largura de banda disponível, a Qualidade de Serviço fornece aos administradores uma maneira de atribuírem prioridades mais altas a pacotes que carregam dados de áudio e vídeo. Ao conceder uma prioridade mais alta a esses pacotes, as comunicações de áudio e vídeo têm uma probabilidade maior de serem concluídas mais rápido e com menos interrupções do que as sessões de rede envolvendo itens como transferências de arquivos, navegação da Web ou backups de bancos de dados. Isso ocorre porque os pacotes de rede usados para transferências de arquivos ou backups de bancos de dados recebem uma atribuição de prioridade de "melhor esforço".

> [!NOTE]  
> Como regra geral, a Qualidade de Serviço se aplica somente a sessões de comunicação em sua rede interna. Ao implementar a QoS, você configure seus servidores e roteadores para suportar a marcação de pacotes; no entanto, você configura esses dispositivos para suportar a marcação de pacotes de forma específica. Não é possível considerar que a Qualidade de Serviço será suportada na Internet ou em outras redes. Mesmo se a Qualidade de Serviço for suportada em outras redes, não há garantia de que a QoS será configurada de forma igual a que você configurou o serviço em sua rede.

O Microsoft Lync Server 2013 não requer a Qualidade de Serviço; se você não usa a QoS, não é necessário instalar o serviço antes de instalar o Lync Server 2013. Se você notar uma quantidade considerável de perda de pacotes em sua rede, a maneira recomendada de aliviar esse problema é adicionar mais largura de banda. Se não for possível adicionar mais largura de banda, então pode ser necessário implementar a Qualidade de Serviço.

O Lync Server 2013 oferece suporte integral à Qualidade de Serviço: isso significa que as organizações que já estão usando a QoS podem integrar facilmente o Lync Server em sua infraestrutura de rede existente. Para fazer isso, você precisa executar as seguintes tarefas:

  - [Habilitando QoS para dispositivos não baseado no Windows](lync-server-2013-enabling-qos-for-devices-that-are-not-based-on-windows.md). Por padrão, a QoS está desativada para computadores e outros dispositivos (como iPhones) que executam outros sistemas operacionais. Embora seja possível usar o Lync Server para ativar e desativar a Qualidade de Serviço em dispositivos, normalmente não é possível usar o produto para modificar os códigos de DSCP usados pelos dispositivos.

  - [Configurando intervalos de portas para seus servidores de medicação, aplicativos e sua conferência](lync-server-2013-configuring-port-ranges-for-your-conferencing-application-and-mediation-servers.md). É necessário reservar um conjunto exclusivo de portas para tipos de pacotes diferentes, como áudio e vídeo. Com o Lync Server 2013 você não ativa ou desativa a Qualidade de Serviço ao definir o valor como Verdadeiro ou Falso. Em vez disso, você ativa a Qualidade de Serviço configurando intervalos de porta e, em seguida, criando e aplicando a Política de grupo. Se decidir posteriormente não usar a QoS, você pode “desativar” a Qualidade de Serviço removendo os objetos de Política de grupo apropriados.

  - [Configurando intervalos de portas para seus servidores de borda](lync-server-2013-configuring-port-ranges-for-your-edge-servers.md). Embora não seja necessário, você pode configurar seus servidores de borda para usar os mesmos intervalos de porta que os outros servidores.

  - [Configurando intervalos de portas para seus clientes Microsoft Lync](lync-server-2013-configuring-port-ranges-for-your-microsoft-lync-clients.md). Esses intervalos de porta se aplicam somente a computadores cliente e normalmente não são os mesmos que os intervalos de porta configurados em seus servidores.

  - [Configurando uma política de Qualidade de Serviço no Lync Server 2013 para seus servidores de Conferência, de Aplicativo e de Mediação](lync-server-2013-configuring-a-quality-of-service-policy-for-your-conferencing-application-and-mediation-servers.md). Essas políticas determinam os códigos DSCP que são aplicados a tipos de pacotes diferentes.

  - [Configurando uma política de Qualidade de Serviço (QoS) para seus servidores de borda A/V](lync-server-2013-configuring-a-quality-of-service-policy-for-your-a-v-edge-servers.md). Isso deve ser executado somente para o lado interno de seus servidores de borda. Isso ocorre pois a Qualidade do Serviço foi projetada para uso em sua rede interna e não na Internet.

  - [Configurando as Políticas de Qualidade de Serviço (QoS) para Clientes Executando no Windows Server 7 ou Windows 8](lync-server-2013-configuring-quality-of-service-policies-for-clients-running-on-windows-7-or-windows-8.md). Observe que o Microsoft Lync Server 2013 não oferece suporte a QoS para outros sistemas operacionais Windows, como Windows Vista ou Windows XP.

  - [Configurando a Qualidade de Serviço (QoS) nos Dispositivos Lync Phone Edition da Microsoft](lync-server-2013-configuring-quality-of-service-on-microsoft-lync-phone-edition-devices.md). Por padrão, a QoS está ativada para dispositivos Lync Phone Edition. No entanto, pode ser necessário alterar o valor padrão de DSCP para garantir que todos os pacotes de áudio em sua organização usem o mesmo código de DSCP.

> [!NOTE]  
> Se estiver utilizando o Microsoft Windows Server 2012 ou o Windows Server 2012 R2, você pode se interessar no novo conjunto de cmdlets do Windows PowerShell disponível para gerenciamento de Qualidade de Serviço nessa plataforma. Para obter mais informações, consulte Qualidade da Rede de Cmdlets de Serviço no Windows PowerShell em <a href="http://go.microsoft.com/fwlink/p/?linkid=285379">http://go.microsoft.com/fwlink/p/?LinkId=285379</a>.
