---
title: Configurando o Repositório de Contatos Pessoais nos Computadores Cliente
TOCTitle: Configurando o Repositório de Contatos Pessoais nos Computadores Cliente
ms:assetid: ec69a6cb-07f2-4057-9544-55035f83eeae
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721922(v=OCS.15)
ms:contentKeyID: 49886464
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Repositório de Contatos Pessoais nos Computadores Cliente

 

_**Tópico modificado em:** 2016-12-08_

Se você estiver integrando o Microsoft Lync Server 2013 e o Microsoft Exchange Server 2013, será recomendável configurar o repositório de contatos pessoais nos computadores cliente executando o Microsoft Lync 2010. Em particular, você deve configurar o Lync para usar o Exchange como o repositório de contatos pessoais e, ao mesmo tempo, verifique se os usuários não podem substituir essa decisão. Isso pode ser feito com a criação e a configuração de um valor de Registro em cada computador cliente.

Observe que isso não é necessário nos computadores executando o Lync 2013.

Para configurar esse valor em um único computador, execute os seguinte procedimento:

1.  No computador do cliente, clique em **Iniciar**, então, clique em **Executar**.

2.  Na caixa de diálogo **Executar**, digite regedit, então, pressione ENTER.

3.  No Editor de Registro, expanda **HKEY\_LOCAL\_MACHINE**, expanda **Software**, expanda **Policies**, expanda **Microsoft** e expanda **Communicator**.

4.  Clique com o botão direito do mouse em **Communicator**, aponte para **Novo** e clique no **Valor DWORD (32 bits)**.

5.  Depois do novo valor ser criado, digite **PersonalContactStoreOverride** e pressione ENTER para renomear o valor.

6.  Verifique se o valor de PersonalContactStoreOverride está definido para 0 e feche o Editor do Registro.

Se precisar fazer esta mesma alteração em vários computadores, você pode criar um objeto personalizado de Política de Grupo. Para obter detalhes, consulte a documentação da Política de Grupo em [http://go.microsoft.com/fwlink/?linkid=268543\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268543%26clcid=0x416).

