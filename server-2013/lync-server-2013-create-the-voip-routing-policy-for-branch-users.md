---
title: 'Lync Server 2013: Criar a política de roteamento VoIP para usuários de filiais'
TOCTitle: Criar a política de roteamento VoIP para usuários de filiais
ms:assetid: 10deca9f-f870-4a42-b25d-e4fc53108658
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398196(v=OCS.15)
ms:contentKeyID: 49305919
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar a política de roteamento VoIP para usuários de filiais no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-23_

É recomendável criar uma política VoIP separada para os usuários de locais de filial. Essa política deve incluir rotas para sair do gateway do Aparelho de Filial Persistente ou do gateway externo do Servidor de Filial Persistente e rotas secundárias para sair de um gateway no local central. Seja qual for o local em que o usuário está registrado, no Registrador do Aparelho de Filial Persistente ou do Servidor de Filial Persistente ou no cluster do Registrador de backup no local central, a política VoIP do usuário vai estar sempre em vigor.

## Para configurar a política de roteamento do VoIP para usuários de filiais

1.  Crie um plano de discagem no nível do usuário e designe-o aos usuários de filiais. (Consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) na Ajuda do Painel de Controle do Lync Server).

2.  Designe regras de normalização correspondendo aos hábitos de discagem dos usuários deste site. Se o usuário do Aparelho de Filial Persistente ou do Servidor de Filial Persistente falha no pool do Registrador de backup no site central, o mesmo plano de discagem ficará em vigor. (Consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) na Ajuda do Painel de Controle do Lync Server).

3.  Configure uma rota de voz egressa do gateway do Aparelho de Filial Persistente ou do gateway externo do Servidor de Filial Persistente. (Consulte [Criar um roteamento de voz no Lync Server 2013](lync-server-2013-create-a-voice-route.md) na Ajuda Painel de Controle do Lync Server).

4.  Defina uma rota de chamada de backup no gateway do Aparelho de Filial Persistente ou do Servidor de Filial Persistente para apontar para o pool do Registrador de backup (colocado com o Servidor de Mediação) no site central. (Consulte sua documentação de fornecedor do Aparelho de Filial Persistente ou do Servidor de Filial Persistente).
    
    > [!NOTE]  
    > A instalação da rota de chamada de backup ajuda a garantir que chamadas de entrada ao usuário de filial funcionarão quando o Aparelho de Filial Persistente ou o Servidor de Filial Persistente não estiver disponível (por exemplo, se estiver inoperante para manutenção). Se o Registrado e o Servidor de Mediação no Aparelho de Filial Persistente ou no Servidor de Filial Persistente não estão disponíveis, e se o usuário está registrado com o pool do Registrador de backup no site central, as chamadas de entrada ainda podem ser roteadas ao usuário.

**Próxima etapa** : [Definir configurações de reroteamento de caixa postal no Lync Server 2013](lync-server-2013-configure-voice-mail-rerouting-settings.md)

