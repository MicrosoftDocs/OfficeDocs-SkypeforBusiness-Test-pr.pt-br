---
title: 'Lync Server 2013: Modificar as configurações de PIN de conferência discada'
TOCTitle: Modificar as configurações de PIN de conferência discada
ms:assetid: 2d110e94-ad29-4755-b17f-d8c2da9b78a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425780(v=OCS.15)
ms:contentKeyID: 49306245
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar as configurações de PIN de conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-18_

A política de PIN global define as regras para PINs de conferências de discagem no nível da floresta. Execute estas etapas para modificar a política de PIN de conferência de discagem global. Para obter detalhes sobre como criar ou modificar uma política de PIN de conferência de discagem no nível de site ou de usuário, consulte [Criar ou modificar as configurações de PIN de conferência discada no Lync Server 2013 para um site ou grupo de usuários](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md).

## Para modificar a política PIN global

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e **Política de PIN** .

4.  Na página **Política de PIN** , clique na política **Global** , em **Editar** e em **Mostrar detalhes** .

5.  Em **Editar Política de PIN** , em **Comprimento mínimo do PIN** , digite ou selecione o comprimento mínimo do PIN que você deseja permitir. O comprimento mínimo padrão é de cinco dígitos.

6.  Para poder especificar o número máximo de tentativas de logon antes que um usuário seja bloqueado, marque a caixa de seleção **Especificar o máximo de tentativas de logon** . Se você não selecionar essa opção, o número máximo de tentativas permitidas será determinado automaticamente com base no tamanho do PIN. Por padrão, o número máximo de tentativas é determinado automaticamente.

7.  Se você marcou a caixa de seleção **Especificar o máximo de tentativas de logon** , em **Máximo de tentativas de logon** , digite ou selecione o número máximo de tentativas de logon que você deseja permitir.

8.  Para fazer com que os PINs expirem, marque a caixa de seleção **Habilitar validade do PIN** . Se você não selecionar essa opção, os PINs nunca expirarão. Por padrão, os PINs nunca expiram.

9.  Se você marcou a caixa de seleção **Habilitar validade do PIN** , em **O PIN expira após (dias)** , digite ou selecione o número de dias após o qual o PIN expirará.

10. Em **Contagem do histórico de PINs** , digite o número de PINs que um usuário precisa criar antes de poder reutilizar um PIN. Por padrão, os usuários podem reutilizar seus PINs.

11. Para permitir padrões comuns de dígitos nos PINs, como números sequenciais e conjuntos repetitivos de números, marque a caixa de seleção **Permitir padrões comuns** . Se você não selecionar essa opção, somente os padrões complexos de dígitos serão permitidos. Por padrão, somente os padrões complexos de dígitos são permitidos.
    
    > [!IMPORTANT]  
    > Recomendamos que você não permita os padrões comuns.

12. Clique em **Confirmar** .

