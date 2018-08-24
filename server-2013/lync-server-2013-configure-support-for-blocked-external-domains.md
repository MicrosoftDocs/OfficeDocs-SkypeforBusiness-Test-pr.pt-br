---
title: 'Lync Server 2013: Configurar suporte para domínios externos bloqueados'
TOCTitle: Configurar suporte para domínios externos bloqueados
ms:assetid: 49103138-e1ab-42bf-91aa-57cf23bbf260
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ619176(v=OCS.15)
ms:contentKeyID: 49306609
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar suporte para domínios externos bloqueados no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Se você configurou suporte para parceiros federados, você pode gerenciar quais domínios serão bloqueados da federação com a sua organização. A lista de domínios bloqueados atuarão como uma lista de bloqueio (listando as entradas explícitas que não são permitidas) e serão aplicadas a uma descoberta de domínio federado, caso tenha essa opção ativada. Para mais detalhes, consulte [Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md).

Bloquear um ou mais domínios externos de se conectar à sua organização. Para tal, adicione o domínio à lista de domínios bloqueados.

## Para adicionar domínio externo à lista de domínios bloqueados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Acesso de usuário externo**.

4.  Clique em **Domínios federados**, clique em **Novo** e, então, em **Domínio bloqueado**.

5.  Em **Novo domínio federado**, faça o seguinte:
    
      - Em **Nome de domínio (ou FQDN)**, digite o nome do domínio de parceiro federado que deseja bloquear.
        
        > [!NOTE]  
        > O nome não pode exceder 256 caracteres de comprimento.<br />        Para buscar um nome de domínio de parceiro federado, efetue uma correspondência de sufixo. Por exemplo, se você digitar <strong>contoso.com</strong> , a busca retornará também o domínio <strong>it.contoso.com</strong>.<br />        Um domínio de parceiro federado não pode ser permitido e bloqueado simultaneamente. O Lync Server 2013 evita que isso aconteça, para que você não precise sincronizar suas listas.    
      - (Opcional) Em **Comentário**, digite a informação que deseja compartilhar com outros administradores de sistema sobre esta configuração.

6.  Clique em **Confirmar**.

7.  Repita as etapas de 4 a 6 para cada parceiro federado que deseja bloquear.

Para ativar acesso de usuário federado, você precisa também ativar o suporte para acesso de usuário federado na sua organização. Para detalhes, consulte [Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013](lync-server-2013-enable-or-disable-remote-user-access.md).

Adicionalmente, você deve configurar e aplicar a política a usuários que deseja que possam colaborar com usuários federados. Para detalhes, consulte [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md).

