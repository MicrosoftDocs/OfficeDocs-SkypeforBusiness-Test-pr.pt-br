---
title: Modificar uma política de PIN existente
TOCTitle: Modificar uma política de PIN existente
ms:assetid: 517caaee-3349-4fa6-8d86-e4da3258a445
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520993(v=OCS.15)
ms:contentKeyID: 49306707
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar uma política de PIN existente

 

_**Tópico modificado em:** 2012-06-19_

Você pode usar a guia **Política de PIN** para fornecer a autenticação de PIN (número de identificação pessoal) aos usuários que estão se conectando ao Lync 2013 com Telefones IP. Para usar a autenticação de PIN, verifique se a opção **Habilitar Autenticação de PIN** está selecionada nas configurações do Serviço Web. Para obter detalhes, consulte [Modificar configurações de Web Service existentes](lync-server-2013-modify-existing-web-service-configuration-settings.md).

Siga estas etapas para modificar uma política de PIN no nível de usuário ou local.

## Para modificar uma política de PIN existente

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Política de PIN**.

4.  Na página **Política de PIN**, clique em uma política, clique em **Editar** e clique em **Mostrar detalhes**.

5.  Em **Editar Política de PIN**, em **Comprimento mínimo do PIN**, digite ou selecione o comprimento mínimo do PIN que você deseja permitir. O comprimento mínimo padrão é de cinco dígitos.

6.  Para poder especificar o número máximo de tentativas de login antes de um usuário ser bloqueado, marque a caixa de seleção **Especificar tentativas máximas de login**. Se você não selecionar esta opção, o número máximo de tentativas permitidas é determinado automaticamente com base no comprimento do PIN. Por padrão, o número máximo de tentativas é determinado automaticamente.

7.  Se você marcou a caixa de seleção **Especificar tentativas máximas de login**, em **Tentativas máximas de login**, digite ou selecione o número máximo de tentativas de login que deseja permitir.

8.  Para que os PINs expirem, marque a caixa de seleção **Habilitar expiração do PIN**. Se você não selecionar esta opção, os PINs nunca irão expirar. Por padrão, os PINs nunca expiram.

9.  Se você marcou a caixa de seleção **Habilitar expiração do PIN**, em **PIN expira após (dias)**, digite ou selecione o número de dias após os quais os PINs irão expirar.

10. Em **Conta de histórico do PIN**, digite o número de PINs que um usuário deve criar antes de poder reutilizar o PIN. Por padrão, os usuários podem reutilizar seus PINs.

11. Para permitir padrões comuns de dígitos nos PINs, como números sequenciais e conjuntos de números repetitivos, marque a caixa de seleção **Permitir padrões comuns**. Se você não selecionar esta opção, apenas padrões complexos de dígitos são permitidos. Por padrão, apenas padrões complexos de dígitos são permitidos.
    
    > [!IMPORTANT]  
    > Recomendamos que você não permita padrões comuns.

12. Clique em **Confirmar**.

