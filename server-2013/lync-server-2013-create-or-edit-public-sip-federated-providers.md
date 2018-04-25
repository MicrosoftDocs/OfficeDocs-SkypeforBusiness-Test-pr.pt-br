---
title: 'Lync Server 2013: Criar ou editar fornecedores SIP públicos federados'
TOCTitle: Criar ou editar fornecedores SIP públicos federados
ms:assetid: 5321598c-1ab1-40e3-b739-4b2e6d0a3a3b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398349(v=OCS.15)
ms:contentKeyID: 49306714
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou editar fornecedores SIP públicos federados no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

A conectividade a redes públicas de mensagens instantâneas permite que os usuários de sua organização usem esse tipo de mensagem para se comunicar com usuários de serviços de IM fornecidos por provedores de serviços públicos de mensagens instantâneas, inclusive a rede do Windows Live, Yahoo e AOL.

O Lync Server 2013 possui configurações de provedor público para mensagens instantâneas do America Online, Windows Live e Yahoo\!. Cada provedor público é configurado com um nome de domínio totalmente qualificado do servidor de borda do provedor e o nível de verificação padrão **Permitir que os usuários se comuniquem somente com pessoas na lista de Contatos deles que utilizem esse provedor**.

Como uma configuração padrão, nenhum provedor público está habilitado. Você deve concluir o contrato de licença e provisionar o trabalho antes de habilitar os provedores públicos. É possível habilitar o provedor antes de concluir o licenciamento e o provisionamento do trabalho. Os usuários não serão capazes de estabelecer comunicação com os contatos nesses provedores até o pré-requisito do trabalho ser concluído. Para obter detalhes sobre licenciamento e provisionamento de provedores públicos, consulte [Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md).

Use o procedimento a seguir para criar ou editar provedores públicos:

## Para criar ou editar provedores públicos

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso Acesso para Federação e Externo** e em **Provedores federados SIP**.

4.  Se for necessário criar um novo provedor público, clique em **Novo** e em **Provedor público**.

5.  Se for necessário editar uma entrada da lista de provedores públicos, selecione um provedor público, clique em **Editar** e em **Mostrar Detalhes**.

6.  Na página **Editar provedor federado SIP**, você pode digitar ou editar as seguintes configurações:
    
      - **Permitir comunicações com esse provedor**   Selecionar essa configuração permite mensagens instantâneas para os usuários desse provedor.
    
      - **Nome do provedor:**   Uma propriedade necessária, digite o nome do provedor conforme ele será refletido na lista de provedores federados SIP.
    
      - **Serviço de Borda de Acesso (FQDN):**   Uma propriedade necessária, digite o nome de domínio totalmente qualificado do Serviço de Borda de Acesso do provedor que você está configurando. Essas informações são fornecidas como um item padrão e devem somente ser alteradas se o provedor público fizer alterações no FQDN do Serviço de Borda de Acesso no provedor público.
    
      - **Nível de verificação padrão:**   A configuração padrão, **Permitir que os usuários se comuniquem com pessoas na lista de Contatos deles que utilizem esse provedor** limitará a comunicação para contatos que tiverem sido aceitos e estiverem na sua lista de contatos.
        
        Selecionar **Permitir que os usuários se comuniquem com qualquer pessoa utilize este provedor** remove as restrições que você deve ter recebido e aceitado com um convite de contato. Essa configuração não limita quem pode entrar em contato com você a partir da rede do provedor público.

7.  Quando você terminar de definir as configurações, clique em **Confirmar** para salvar ou clique em **Cancelar** para descartar suas alterações.

## Consulte Também

#### Tarefas

[Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)  
[Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

