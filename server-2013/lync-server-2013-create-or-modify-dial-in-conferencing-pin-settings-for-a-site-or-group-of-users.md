---
title: 'Lync Server 2013: Criar ou modificar as configurações de PIN de conferência discada para um site ou grupo de usuários'
TOCTitle: Criar ou modificar as configurações de PIN de conferência discada para um site ou grupo de usuários
ms:assetid: c29bab5c-2b93-48e0-ae0b-29564daaff9a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412959(v=OCS.15)
ms:contentKeyID: 49308011
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar as configurações de PIN de conferência discada no Lync Server 2013 para um site ou grupo de usuários

 

_**Tópico modificado em:** 2012-10-18_

Siga estas etapas para criar ou modificar uma política de PIN (número de identificação pessoal) de conferência discada no nível do usuário ou no nível do local. Para obter detalhes sobre como alterar a política de PIN global, consulte [Modificar as configurações de PIN de conferência discada no Lync Server 2013](lync-server-2013-modify-the-default-dial-in-conferencing-pin-settings.md).

## Para criar uma política de PIN de site ou usuário

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e **Política de PIN** .

4.  Na página **Política de PIN** , clique em **Novo** e execute uma das seguintes ações:
    
      - Para criar uma política de nível de usuário, clique em **Política de usuário** . Em **Nova Política de PIN** , em **Nome** , digite um nome que descreve a política.
    
      - Para criar uma política de nível de site, clique em **Política de site** . No campo de pesquisa **Selecionar um Site** , digite todo ou parte do nome do site para o qual você deseja criar uma política. Na lista de sites, clique no site que você deseja e clique em **OK** .

5.  No campo **Descrição** , digite uma descrição da política de PIN.

6.  No campo **Tamanho mínimo do PIN** , digite ou selecione o tamanho mínimo do PIN que você deseja permitir. O tamanho mínimo padrão é de cinco dígitos.

7.  Para poder especificar o número máximo de tentativas de logon antes que um usuário seja bloqueado, marque a caixa de seleção **Especificar o máximo de tentativas de logon** . Se você não selecionar essa opção, o número máximo de tentativas permitidas será determinado automaticamente com base no tamanho do PIN. Por padrão, o número máximo de tentativas é determinado automaticamente.

8.  Se você marcou a caixa de seleção **Especificar o máximo de tentativas de logon** , em **Máximo de tentativas de logon** , digite ou selecione o número máximo de tentativas de logon que você deseja permitir.

9.  Para fazer com que os PINs expirem, marque a caixa de seleção **Habilitar validade do PIN** . Se você não selecionar essa opção, os PINs nunca expirarão. Por padrão, os PINs nunca expiram.

10. Se você marcou a caixa de seleção **Habilitar validade do PIN** , em **O PIN expira após (dias)** , digite ou selecione o número de dias após o qual o PIN expirará.

11. Em **Contagem do histórico de PINs** , digite o número de PINs que um usuário precisa criar antes de poder reutilizar um PIN. Por padrão, os usuários podem reutilizar seus PINs.

12. Para permitir padrões comuns de dígitos nos PINs, como números sequenciais e conjuntos repetitivos de números, marque a caixa de seleção **Permitir padrões comuns** . Se você não selecionar essa opção, somente os padrões complexos de dígitos serão permitidos. Por padrão, somente os padrões complexos de dígitos são permitidos.
    
    > [!IMPORTANT]  
    > Recomendamos que você não permita os padrões comuns.

13. Clique em **Confirmar** .

## Para alterar uma política de PIN de site ou usuário

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e **Política de PIN** .

4.  Na página **Política de PIN** , clique na política de PIN que você deseja alterar, clique em **Editar** e clique em **Mostrar detalhes** .

5.  Em **Editar Política de PIN** , modifique quaisquer configurações de política (exceto o nome da política, que não pode ser modificado).

6.  Clique em **Confirmar** .

