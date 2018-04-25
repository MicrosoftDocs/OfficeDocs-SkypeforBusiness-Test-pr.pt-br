---
title: 'Lync Server 2013: Criar ou editar provedores hospedados federados SIP'
TOCTitle: Criar ou editar provedores hospedados federados SIP
ms:assetid: 0dd6dcb6-a88d-46b8-9c96-b35967309bcd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ552445(v=OCS.15)
ms:contentKeyID: 49305885
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou editar provedores hospedados federados SIP no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

A conectividade de mensagens instantâneas (IM) do provedor hospedado habilita usuários em sua organização a usar IM para se comunicar com usuários de serviços de IM fornecidos por provedores hospedados, incluindo o Microsoft Office 365 e o Lync Online.

Cada provedor hospedado é configurado com o nome de domínio totalmente qualificado do servidor de Borda do provedor e o nível de verificação padrão **Permitir que os usuários se comuniquem somente com pessoas em suas listas de Contatos que usam este provedor**.

Use o procedimento a seguir para criar ou editar provedores hospedados:

## Para criar ou editar provedores hospedados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso Acesso para Federação e Externo** e em **Provedores federados SIP**.

4.  Se for necessário criar um novo provedor hospedado, clique em **Novo** e em **Provedor hospedado**.

5.  Se for necessário editar uma entrada da lista de provedores hospedados, selecione um provedor hospedado, clique em **Editar** e em **Exibir detalhes**.

6.  Na página **Editar provedor federado SIP**, você pode digitar ou editar as seguintes configurações:
    
      - **Habilitar comunicações com este provedor**    Selecionar esta configuração habilita as comunicações com os usuários deste provedor.
    
      - **Nome do provedor:**    Uma propriedade necessária, digite o nome do provedor conforme ele será refletido na lista de provedores federados SIP.
    
      - **Serviço de Borda de Acesso (FQDN):**    Uma propriedade obrigatória, digite o nome de domínio totalmente qualificado do serviço de Borda de Acesso do provedor hospedado que estiver configurando. Esta informação deve ser fornecida pelo provedor hospedado, e só deve ser alterada se o provedor fizer uma mudança no FQDN do serviço de Borda de Acesso.
    
      - **Nível de verificação padrão:**    A configuração padrão, **Permitir que os usuários se comuniquem com pessoas na lista de Contatos deles que utilizem esse provedor** limitará a comunicação para contatos que tiverem sido aceitos e estiverem na sua lista de contatos.
        
        Selecionar **Permitir que os usuários se comuniquem com todos que usam este provedor** remove a restrição de que você deve ter recebido e aceitado o convite de um contato. Esta configuração não limita quem pode entrar em contato com você a partir da rede do provedor hospedado.

7.  Quando você terminar de definir as configurações, clique em **Confirmar** para salvar ou clique em **Cancelar** para descartar suas alterações.

## Consulte Também

#### Tarefas

[Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)  
[Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

