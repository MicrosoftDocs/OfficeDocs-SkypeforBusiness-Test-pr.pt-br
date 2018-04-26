---
title: Configurando o AD FS 2.0 para suporte à autenticação de cliente
TOCTitle: Configurando o AD FS 2.0 para suporte à autenticação de cliente
ms:assetid: 4d93d400-ccaa-4da8-a71b-d05d7ba79d93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308565(v=OCS.15)
ms:contentKeyID: 56270390
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o AD FS 2.0 para suporte à autenticação de cliente

 

_**Tópico modificado em:** 2016-12-08_

Há dois tipos possíveis de autenticação que podem ser configurados para permitir que o AD FS 2.0 suporte autenticações utilizando cartões inteligentes:

  - Autenticação baseada em formulário (FBA)

  - Autenticação de Cliente de Segurança na Camada de Transporte

Utilizando a autenticação baseada em formulários, você pode desenvolver uma página da Web que permite que os usuários autentiquem usando seus nomes de usuário/senhas ou usando o cartão inteligente e o PIN. Este tópico tem como foco como implementar a Autenticação de Cliente de Segurança na Camada de Transporte com o AD FS 2.0. Para obter mais informações sobre os tipos de autenticação do AD FS 2.0, consulte AD FS 2.0: como alterar o tipo de autenticação local em [http://go.microsoft.com/fwlink/p/?LinkId=313384](http://go.microsoft.com/fwlink/p/?linkid=313384).


**Para configurar o AD FS 2.0 para suportar a autenticação de cliente**

1.  Faça logon no computador do AD FS 2.0 utilizando uma conta de Administrador de Domínio.

2.  Inicie o Windows Explorer.

3.  Navegue até C:\\inetpub\\adfs\\ls

4.  Faça uma cópia de backup do arquivo web.config existente.

5.  Abra o arquivo web.config existente utilizando o Bloco de Notas.

6.  Na barra de Menu, selecione **Editar** e, em seguida, selecione **Localizar**.

7.  Procure **\<localAuthenticationTypes\>**.
    
    Observe que há quatro tipos de autenticação listados, um por linha.

8.  Mova para a linha que contém o tipo de autenticação TLSClient para o topo da lista na seção.

9.  Salve e Feche o arquivo web.config.

10. Inicie um Prompt de Comando com privilégios elevados.

11. Reinicie o IIS executando o seguinte comando:
    
        IISReset /Restart /NoForce

