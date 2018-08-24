---
title: Criar uma nova política de PIN
TOCTitle: Criar uma nova política de PIN
ms:assetid: 8bdf0478-fe9f-4371-93ff-db39381a25db
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182547(v=OCS.15)
ms:contentKeyID: 49307409
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma nova política de PIN

 

_**Tópico modificado em:** 2012-06-19_

Você pode usar a página **Política de PIN** para oferecer autenticação de PIN (número de identificação pessoal) para usuários que estejam se conectando ao Lync 2013 com telefones IP. Para usar a autenticação de PIN, verifique se a opção **Habilitar Autenticação de PIN** está selecionada nas configurações do Serviço Web. Para obter detalhes, consulte [Modificar configurações de Web Service existentes](lync-server-2013-modify-existing-web-service-configuration-settings.md).

Siga estas etapas para criar uma política de PIN de nível de usuário ou de nível de site.

## Para criar uma política de PIN de usuário ou de site

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Segurança** e em **Política de PIN**.

4.  Na página **Política de PIN**, clique em **Novo** e execute um dos seguintes procedimentos:
    
      - Para criar uma política de nível de usuário, clique em **Política de usuário**. Em **Nova Política de PIN**, em **Nome**, digite um nome que descreva a política.
    
      - Para criar uma política de nível de site, clique em **Política de site**. No campo de pesquisa **Selecione um Site**, digite todo ou parte do nome do site para o qual deseja criar uma política. Na lista resultante de sites, clique naquele que deseja e em **OK**.

5.  No campo **Descrição**, digite uma descrição para a política de PIN.

6.  No campo **Tamanho mínimo do PIN**, digite ou selecione o tamanho mínimo do PIN que você deseja permitir. O tamanho mínimo padrão é 5 dígitos.

7.  Para especificar o número máximo de tentativas de logon antes que o usuário seja bloqueado, selecione a opção **Especificar o máximo de tentativas de logon**. Se esta opção não for selecionada, o número máximo de tentativas permitido é automaticamente determinado com base no tamanho do PIN. Por padrão, o número máximo de tentativas é automaticamente determinado.

8.  Se você selecionou a opção **Especificar o máximo de tentativas de logon**, em **Máximo de tentativas de logon**, digite ou selecione o número máximo de tentativas de logon que deseja permitir.

9.  Para que o PIN expire, selecione a opção **Habilitar validade do PIN**. Se esta opção não for selecionada, PINs nunca expirarão. Por padrão, PINs nunca expiram.

10. Se você selecionou a opção **Habilitar validade do PIN**, em **O PIN vence depois de (dias)**, digite ou selecione o número de dias depois dos quais os PINs expirarão.

11. Em **Contagem do histórico de PINs**, digite o número de PINs que um usuário deve criar antes de reutilizar um PIN. Por padrão, os usuários podem reutilizar seus PINs.

12. Para permitir padrões comuns de dígitos em PINs, como números sequenciais e conjuntos repetitivos de números, selecione a opção **Permitir padrões comuns**. Se esta opção não for selecionada, somente padrões complexos de dígitos são permitidos. Por padrão, somente padrões complexos de PINs são permitidos.
    
    > [!IMPORTANT]  
    > É recomendável não permitir padrões comuns.

13. Clique em **Confirmar**.

