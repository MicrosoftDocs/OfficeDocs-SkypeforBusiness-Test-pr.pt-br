---
title: Modificar as configurações do Registrador existente
TOCTitle: Modificar as configurações do Registrador existente
ms:assetid: a8931511-3e66-49ed-a3ec-03bcd61ce1f0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182566(v=OCS.15)
ms:contentKeyID: 49307729
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar as configurações do Registrador existente

 

_**Tópico modificado em:** 2012-11-01_

Você pode usar o Registrador para configurar protocolos de autenticação de servidor proxy. Para obter informações sobre os protocolos disponíveis, consulte [Criar configurações do Registrador](lync-server-2013-create-registrar-configuration-settings.md).

> [!NOTE]  
> É recomendável que você habilite Kerberos e NTLM quando um servidor oferecer suporte a autenticação a ambos, clientes remotos e corporativos. O Servidor de Borda e servidores internos se comunicam para garantir que somente a autenticação NTLM seja oferecida a clientes remotos. Se somente Kerberos estiver habilitada nesses servidores, eles não poderão autenticar usuários remotos. Se os usuários corporativos também se autenticarem no servidor, Kerberos será usada.

Siga estas etapas para modificar um Registrador Avançado existente.

## Para modificar um Registrador Avançado Existente

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Segurança** e em **Registrador Avançado**.

4.  Na página **Registrador Avançado**, clique em um serviço, em **Editar** e em **Exibir detalhes**.

5.  Em **Editar Configuração do Registrador Avançado**, selecione um ou mais dos itens a seguir, dependendo dos recursos dos clientes e do suporte em seu ambiente:
    
      - **Habilitar autenticação Kerberos** para que os servidores no pool tratem desafios usando a autenticação Kerberos.
    
      - **Habilitar autenticação NTLM** para que os servidores no pool tratem desafios usando NTLM.
    
      - **Habilitar autenticação de certificado** para que os servidores no pool emitam certificados para clientes.

6.  Clique em **Confirmar**.

