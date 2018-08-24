---
title: 'Lync Server 2013: Instalar o repositório de Configuração Local'
TOCTitle: Instalar o repositório de Configuração Local
ms:assetid: b563030d-d338-411f-9611-28d5eb4b3238
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412874(v=OCS.15)
ms:contentKeyID: 49307857
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalar o repositório de Configuração Local no Lync Server 2013

 

_**Tópico modificado em:** 2014-06-27_

Antes de seguir os passos, certifique-se de estar registrado no servidor com uma conta de usuário do domínio que seja administrador local e membro do grupo RTCUniversalReadOnlyAdmin.

Para que possa fazer qualquer coisa com o Assistente de Implantação do Lync Server, precisamos do armazenamento de Configuração Local que existe no servidor. O armazenamento de Configuração Local é cópia somente leitura do Repositório de Gerenciamento Central, que foi criado após a instalação local do SQL Server Express. O próprio Repositório de Gerenciamento Central foi adicionado ao banco de dados SQL Server instalado existente no banco de dados com base em Servidor Standard Edition ou SQL Server Express.

> [!IMPORTANT]  
> Se você não tiver executado a configuração do Lync Server 2013 no servidor anteriormente, será solicitado uma unidade e um caminho para instalar o Lync Server 2013. Isso permitirá a você instalar em uma unidade diferente da unidade do sistema, caso a sua organização necessite, ou caso você tenha problemas de espaço. Somente é possível alterar o caminho do local de instalação para os arquivos do Lync Server na caixa de diálogo Configuração para uma nova unidade disponível. Se você instalar os arquivos de Configuração nesse caminho, incluindo o OCSCore.msi, o restante dos arquivos do Lync Server 2013 será implantado nessa unidade também.

## Para instalar o repositório Configuração Local

1.  A partir da mídia de instalação, navegue até \\setup\\amd64\\Setup.exe, e clique em **OK**.

2.  Se você receber uma solicitação para instalar o Microsoft Visual C++ 2012 Redistributable, clique em **Sim**.

3.  Na página **Lync Server 2013 Local de instalação** , clique em **OK** .

4.  Na página **Contrato de Licença de Usuário Final**, revise os termos da licença, selecione **Aceito os termos do contrato de licença**, e clique em **OK** para continuar.

5.  Na página Assistente de Implantação, clique em **Instalar ou Atualizar o Sistema do Lync Server** .

6.  Na página **Lync Server 2013**, ao lado de **Etapa 1: instalar repositório de configuração local** , clique em **Executar** .

7.  Na página **Instalar Configurações de Armazenamento Local** , verifique se a opção **Recuperar diretamente do repositório de Gerenciamento Central** está selecionada, e clique em **Próximo** .

8.  Quando a instalação da configuração do servidor local estiver concluída, será necessário clicar em **Concluir**.

