---
title: Configurando a AC corporativa para a autenticação de cartão inteligente
TOCTitle: Configurando a AC corporativa para a autenticação de cartão inteligente
ms:assetid: c24e0891-e108-4cb6-9902-c6a4c8e68455
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308571(v=OCS.15)
ms:contentKeyID: 56270470
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a AC corporativa para a autenticação de cartão inteligente

 

_**Tópico modificado em:** 2016-12-08_

A seção a seguir descreve como configurar autoridade de certificação (AC) raiz corporativa para dar suporte à autenticação do cartão inteligente. Para obter informações sobre como instalar uma AC raiz corporativa, consulte Instalar uma autoridade de certificação raiz corporativa em [http://go.microsoft.com/fwlink/p/?LinkID=313364](http://go.microsoft.com/fwlink/p/?linkid=313364).

## Configuração de uma Autoridade de Certificação Raiz Corporativa para dar suporte à Autenticação de Cartão Inteligente

As seguintes etapas descrevem como configurar uma CA Raiz Corporativa para dar suporte à Autenticação de Cartão Inteligente:

1.  Faça o login no computador da AC corporativa utilizando uma conta de Administrador de Domínio.

2.  Inicie o Gerenciador de Sistema e verifique se a função de Registro da Web da Autoridade de Certificação está instalada.

3.  No menu **Ferramentas Administrativas**, abra o console de gerenciamento da **Autoridade de Certificação**.

4.  No painel de Navegação, expanda **Autoridade de Certificação**.

5.  Clique com o botão direito do mouse em **Modelos de Certificado**, selecione **Novo** e, em seguida, selecione **Modelo de Certificação para Emissão**.

6.  Selecione **Agente de Registro**, **Usuário do Cartão Inteligente** e **Logon do Cartão Inteligente**.

7.  Clique em **OK**.

8.  Clique com o botão direito em **Modelos de Certificado**.

9.  Selecione **Gerenciar**.

10. Abra as propriedades do modelo do Usuário do Cartão Inteligente.

11. Clique na guia **Segurança**.

12. Altere as permissões da seguinte forma:
    
      - Adicione contas de AD de usuários individuais com permissões para Ler/Registrar (Permitir) ou
    
      - Adicione um grupo de segurança contendo usuários do cartão inteligente com permissões para Ler/Registrar (Permitir), ou
    
      - Adicione o grupo do Usuário de Domínio com as permissões para Ler/Registrar (Permitir)

