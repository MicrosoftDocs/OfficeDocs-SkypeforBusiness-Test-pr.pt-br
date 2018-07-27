---
title: Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente
TOCTitle: Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente
ms:assetid: 5b4d3db1-6eba-4932-b49c-f60bcf9488f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615442(v=OCS.15)
ms:contentKeyID: 49306825
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente

 

_**Tópico modificado em:** 2012-10-06_

Os tópicos desta seção o guiarão durante o processo de migração do Lync Server 2010, Chat de Grupo ou do Office Communications Server 2007 R2Chat de Grupo para o Lync Server 2013, Servidor de Chat Persistente. Se você deseja que sua implantação do Lync Server 2013, Servidor de Chat Persistente coexista com uma implantação do Lync Server 2010, Chat de Grupo ou do Office Communications Server 2007 R2Chat de Grupo, este guia também inclui algumas informações básicas sobre a operação nesse ambiente misto. Este guia concentra-se principalmente na migração de dados do Servidor de Chat Persistente. Para usuários migrando de versões antigas do Lync Server para o Lync Server 2013, consulte [Migração do Lync Server 2010 para o Lync Server 2013](migration-from-lync-server-2010-to-lync-server-2013.md) e [Migração do Office Communications Server 2007 R2 para Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md).

> [!IMPORTANT]  
> Este tópico pressupõe que você já tenha instalado o Lync Server 2013 em coexistência com o Lync Server 2010 ou o Office Communications Server 2007 R2.

> [!IMPORTANT]  
> Este documento descreve as etapas geralmente necessárias para realizar cada fase da migração. Ele não aborda todas as topologias de implantação antigas nem todos os cenários de migração possíveis. Portanto, você talvez não precise realizar todas as etapas descritas ou talvez precise realizar etapas adicionais, dependendo da sua implantação. Este guia também oferece exemplos de etapas de verificação. Essas etapas de verificação são oferecidas para ajudá-lo a entender o que é necessário procurar para garantir que cada fase seja concluída com êxito conforme você progredir na sua implantação. Você pode personalizar essas etapas de verificação de acordo com seu processo de migração específico.

Este guia oferece informações específicas para atualizar sua implantação existente. Explica como alterar sua topologia existente. Este guia não aborda a implementação de novos recursos. Quando um procedimento detalhado é documentado em outro local, este guia orienta você para o documento ou seção adequado.

Este documento define os termos conforme especificados na lista a seguir.

  - *migração*   
    A transferência de sua implantação de uma versão anterior do Servidor de Chat Persistente, anteriormente conhecido como Servidor de Chat de Grupo, para o Lync Server 2013, Servidor de Chat Persistente.

<!-- end list -->

  - *atualização*   
    Instalar uma versão mais nova do software em um servidor ou computador cliente.

<!-- end list -->

  - *coexistência*   
    O ambiente temporário que existe durante a migração, quando algumas funcionalidades podem ter sido migradas para o Lync Server 2013, Servidor de Chat Persistente e outras funcionalidades permanecem em uma versão anterior do Servidor de Chat de Grupo.

O Servidor de Chat Persistente é uma extensão da infraestrutura do Lync Server 2013. Dependendo da sua topologia, você pode migrar o Lync Server 2010, Chat de Grupo ou o Office Communications Server 2007 R2Chat de Grupo para o Lync Server 2013Servidor de Chat Persistente. Para obter detalhes sobre as topologias disponíveis e os requisitos técnicos e de software para a migração do Servidor de Chat de Grupo, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de planejamento.

Se a sua organização precisar de suporte a conformidade, agora ele é automaticamente instalado com cada Servidor de Chat Persistente. Não há mais necessidade de um servidor separado para conformidade.

> [!IMPORTANT]  
> O Servidor de Chat Persistente deve estar instalado em um sistema de arquivo NTFS para ajudar a forçar a segurança do sistema de arquivos. O FAT32 não é um sistema de arquivos suportado para o Servidor de Chat Persistente.<br />Se a sua organização precisar de suporte a conformidade, agora ele é automaticamente instalado com cada Servidor de Chat Persistente. Não há mais necessidade de um servidor separado para conformidade. Para obter mais detalhes sobre as mudanças no Lync Server 2013Servidor de Chat Persistente, consulte <a href="lync-server-2013-new-persistent-chat-server-features.md">Novos recursos do Servidor de Chat Persistente no Lync Server 2013</a> na documentação de introdução.

## Nesta seção

  - [Cenário de migração padrão - nível alto](standard-migration-scenario-high-level.md)

  - [Processo de migração - detalhes](migration-process-details.md)

  - [Considerações de coexistência](coexistence-considerations.md)

