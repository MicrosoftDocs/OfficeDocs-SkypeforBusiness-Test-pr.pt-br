---
title: 'Lync Server 2013: Definir configurações de reroteamento de caixa postal'
TOCTitle: Definir configurações de reroteamento de caixa postal
ms:assetid: 7ab6be28-eabb-4a79-a796-648887d71b83
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398606(v=OCS.15)
ms:contentKeyID: 49307205
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir configurações de reroteamento de caixa postal no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

Aparelho de Filial Persistente e Servidor de Filial Persistente poderão oferecer capacidade de persistência de caixa postal para usuários de filiais durante o tempo de interrupção da WAN se o Unificação de Mensagens (UM) do Exchange estiver instalado no local central e se um AA (Atendedor Automático) de Mensagens do UM do Exchange estiver implantado. Recomendamos que o seu administrador do Exchange configure o AA para aceitar somente mensagens, o que desabilitará outra funcionalidade genérica, como a transferência para um usuário ou a transferência para uma telefonista. Como alternativa, você poderia usar um AA genérico ou um AA personalizado para rotear a chamada.

Para obter detalhes, consulte a seção Preparando para a Sustentabilidade da Caixa Postal no [Requisitos de resiliência do site da filial para Lync Server 2013](lync-server-2013-branch-site-resiliency-requirements.md) na documentação de planejamento.

## Para configurar a sustentabilidade da caixa postal

1.  Peça ao administrador do Exchange para configurar o AA somente para aceitar mensagens (no Shell do Exchange, use o seguinte cmdlet: **Set-UMAutoAttendant \<AA name\> -CallSomeoneEnabled $false**. O parâmetro que especifica que se permita deixar mensagens ( *SendVoiceMsgEnabled*) é verdadeiro por padrão.

2.  No Shell de Gerenciamento do Lync Server, use o cmdlet **New-CSVoiceMailReroutingConfiguration** para definir o número de telefone do AA como o UM do Exchange número de telefone do Atendedor Automático na configuração de redirecionamento da caixa postal Aparelho de Filial Persistente ou Servidor de Filial Persistente.
    
    > [!NOTE]  
    > Se você precisar modificar a configuração do roteamento da caixa postal posteriormente, use o cmdlet <strong>Set-CsVoiceMailReRoutingConfiguration</strong>. Para obter detalhes, sobre <strong>New-</strong> e <strong>Set-CSVoiceMailReroutingConfiguration</strong>, nos tópicos da Ajuda do Shell.

3.  Defina o número de acesso do assinante UM do Exchange que corresponde ao plano de discagem da filial do usuário UM do Exchange como o número de acesso do assinante UM do Exchange na configuração de roteamento da caixa postal do Aparelho de Filial Persistente ou Servidor de Filial Persistente.
    
    > [!NOTE]  
    > Configure o plano de discagem UM do Exchange de usuários para que haja apenas um plano de discagem associado a todos os usuários de filiais que precisam acessar a funcionalidade Obter caixa postal durante uma interrupção da WAN.

**Próxima etapa** para Aparelho de Filial Persistente ou Servidor de Filial Persistente: [Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor no Lync Server 2013](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md).

