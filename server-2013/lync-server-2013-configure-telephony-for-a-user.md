---
title: Configurar telefonia para um usuário
TOCTitle: Configurar telefonia para um usuário
ms:assetid: 4546432e-c839-4517-a2c5-bc0d4d8c6a03
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520988(v=OCS.15)
ms:contentKeyID: 49306552
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar telefonia para um usuário

 

_**Tópico modificado em:** 2012-11-01_

As configurações de telefonia são algumas das configurações individuais de uma conta de usuário que podem ser definidas no Painel de Controle do Lync Server para o usuário (ou seja, se o usuário individual tiver sido habilitado para o Lync Server 2013 e a organização oferecer suporte à telefonia).

As opções de telefonia do usuário do Lync Server incluem:

  - **Áudio/vídeo desabilitado**   O usuário não pode fazer chamadas com áudio e vídeo.

  - **Somente PC-PC**   O usuário pode fazer chamadas de áudio ou vídeo somente PC-PC.

  - **Enterprise Voice**   O usuário pode usar a infraestrutura do Lync Server 2013 para rotear todas as chamadas de entrada e saídas. O usuário também pode fazer chamadas PC-PC.

  - **Controle de chamada remota**   O usuário pode usar o Lync Server 2013 para controlar um telefone de mesa e também fazer chamadas PC-PC.

Para obter detalhes sobre a configuração de telefonia para uma organização, consulte [Configurar telefonia para um usuário](lync-server-2013-configure-telephony-for-a-user.md)e [Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) na documentação de Implantação.

## Para configurar telefonia para uma conta de usuário específica

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou a primeira parte do nome para exibição, nome, sobrenome, nome da conta do SAM (Gerenciador de Contas de Segurança), endereço SIP ou URI (Uniform Resource Identifier) de linha da conta de usuário desejada e clique em **Localizar**.

5.  Na tabela, clique na conta de usuário que você deseja modificar.

6.  No menu **Editar**, clique em **Modificar**.

7.  Em **Telefonia**, faça o seguinte:
    
      - Para desabilitar as chamadas de áudio e vídeo do usuário, clique em **Áudio/vídeo desabilitado**.
    
      - Para habilitar a comunicação de áudio PC-PC do usuário, mas não o controle de chamada remota ou o Enterprise Voice, clique em **Somente PC-PC**. Especifique um valor para **URI da Linha** para o telefone que o usuário usa para comunicações de áudio PC-PC.
    
      - Para rotear chamadas de telefone do usuário usando a infraestrutura do Lync Server 2010 de acordo com a classe de política de serviço, incluindo a comunicação de áudio PC-PC, clique em **Enterprise Voice**. Em **URI da Linha**, especifique o número de telefone para Enterprise Voice. Em **Política de plano de discagem** e **Política de Voz** , especifique as políticas apropriadas para o usuário. Para especificar as regras de normalização para conversão de números de telefone discados pelo usuário no formato E.164, selecione o perfil de local apropriado no em **Política de local**.
    
      - Para habilitar o controle de chamada remota, que permite aos usuários controlar sua linha de telefone de mesa do Lync Server 2013 para fazer chamadas PC-PC e chamadas de PC para telefone, clique em **Controle de chamada remota**. Em **URI da Linha**, especifique o número de telefone para o controle de chamada remota. O usuário deve ter um telefone de mesa e a conexão PBX (central privada de comutação telefônica) para roteamento de chamada.

## Consulte Também

#### Outros Recursos

[Modificando as Propriedades da Conta do Usuário](lync-server-2013-modifying-user-account-properties.md)

