---
title: 'Lync Server 2013: Configurar suprote para domínios externos permitidos'
TOCTitle: Configurar suprote para domínios externos permitidos
ms:assetid: 3ee6e175-986d-4c33-b03a-b9f93083dca6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425908(v=OCS.15)
ms:contentKeyID: 49306490
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar suprote para domínios externos permitidos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Se você configurou suporte para parceiros federados, você pode gerenciar quais domínios federar com a sua organização. Você configura um ou mais domínios externos específicos como domínios federados permitidos. Para fazer isso, adicione cada domínio à lista de domínios permitidos. Mesmo se a descoberta de parceiro estiver habilitada para sua organização, faça isso se o domínio for um parceiro federado que talvez precise se comunicar com mais de 1.000 usuários ou talvez precise enviar mais de 20 mensagens por segundo. Se a descoberta de parceiro não estiver habilitada para a sua organização, somente os usuários de domínios externos que você adiciona à lista de domínios permitidos podem participar em conferência e mensagens instantâneas com usuários em sua organização. Se você quiser restringir o acesso de um domínio federado a um servidor específico que executa o serviço de Borda de Acesso do parceiro federado, poderá especificar o nome de domínio do servidor que executa o serviço de Borda de Acesso para cada domínio na lista de domínios permitidos.

> [!NOTE]  
> Este procedimento descreve como configurar o suporte para domínios específicos, mas implementar suporte para usuários federados também exige que você habilite o suporte para usuários federados de sua organização, bem como configure e aplique políticas para controlar quais usuários podem colaborar com usuários federados. Para obter detalhes sobre como habilitar o suporte para usuários federados, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a>. Para obter detalhes sobre como configurar políticas para controlar a federação, consulte <a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Configurar políticas para controlar acesso de usuário federado no Lync Server 2013</a>.

## Para adicionar um domínio externo à lista de domínios permitidos

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso de Usuário Externo** e em **Domínios Federados** .

4.  Na página **Domínios Federados** , clique em **Novo** e em **Domínio permitido** .

5.  Em **Novo domínio federado** , faça o seguinte:
    
      - Em **Nome de domínio (ou FQDN)** , digite o nome do domínio do parceiro federado.
        
        > [!NOTE]  
        > Esse nome deve ser exclusivo e não pode já existir como um domínio permitido para este servidor que executa o serviço de Borda de Acesso. O nome não pode exceder 256 caracteres.<br />        Para buscar um nome de domínio de parceiro federado, efetue uma correspondência de sufixo. Por exemplo, se você digitar <strong>contoso.com</strong> , a busca retornará também o domínio <strong>it.contoso.com</strong> .<br />        Um domínio de parceiro federado não pode ser permitido e bloqueado simultaneamente. O Lync Server 2013 evita que isso aconteça, para que você não precise sincronizar suas listas.    
      - Se você quiser restringir o acesso para esse domínio federado a usuários de um servidor específico que execute o serviço de Borda de Acesso, em **Serviço de Borda de Acesso (FQDN)** , digite o FQDN do servidor do domínio federado executando o serviço de Borda de Acesso.
    
      - Se você quiser fornecer informações adicionais, em **Comentário** , digite as informações que deseja compartilhar com outros administradores de sistema sobre essa configuração.

6.  Clique em **Confirmar** .

7.  Repita as etapas 4 a 6 para cada domínio de parceiro federado que deseja permitir.

Para ativar acesso de usuário federado, você precisa também ativar o suporte para acesso de usuário federado na sua organização. Para detalhes, consulte [Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013](lync-server-2013-enable-or-disable-remote-user-access.md).

Adicionalmente, você deve configurar e aplicar a política a usuários que deseja que possam colaborar com usuários federados. Para detalhes, consulte [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md).

