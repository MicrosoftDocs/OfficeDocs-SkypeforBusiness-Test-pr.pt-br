---
title: Configurando um nó inspetor para usar a autenticação de credencial
TOCTitle: Configurando um nó inspetor para usar a autenticação de credencial
ms:assetid: 032e33f3-9483-42e6-a33c-347eb6779597
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204632(v=OCS.15)
ms:contentKeyID: 49305697
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando um nó inspetor para usar a autenticação de credencial

 

_**Tópico modificado em:** 2012-10-20_

Se seu computador no nó do inspetor estiver fora da rede de perímetro, será necessário seguir um procedimento um pouco diferente para configurar o nó do inspetor a fim de executar transações sintéticas. Especificamente, não crie um pool de aplicativos confiáveis e um aplicativo confiável, e é necessário instalar um certificado que permita ao nó do inspetor enviar alertas a um computador dentro da rede de perímetro. Isso significa que será necessário completar duas tarefas separadas:

  - Atualize a associação no grupo Administradores locais somente leitura RTC do computador

  - Instale os arquivos de configuração do nó do inspetor

## Atualizando a associação no grupo Administradores locais somente leitura RTC

Se seu nó de inspetor estiver fora da rede de perímetro, será necessário adicionar a conta Serviço de Rede ao grupo Administradores locais somente leitura RTC no computador no nó do inspetor. Para fazer isso, complete o seguinte procedimento no nó do inspetor:

1.  Clique em **Iniciar**, clique com o botão direito do mouse em **Computador** e clique em **Gerenciar**.

2.  No Gerenciador de Servidor, expanda **Configuração**, expanda **Usuários e Grupos Locais** e clique em **Grupos**.

3.  No painel Grupos, clique duas vezes em **Administradores locais somente leitura RTC**.

4.  Na caixa de diálogo **Propriedades de Administradores Locais Somente Leitura RTC**, clique em **Adicionar**.

5.  Na caixa de diálogo **Selecionar Usuários, Computadores, Contas de Serviço ou Grupos**, clique em **Locais**

6.  Na caixa de diálogo **Locais**, selecione o nome do computador no nó de inspetor e clique em **OK**.

7.  Na caixa **Digite os nomes de objeto a serem selecionados**, digite **Serviço de Rede** e clique em **OK**.

8.  Na caixa de diálogo **Propriedades de Administradores Locais Somente Leitura RTC**, clique em **OK** e feche o **Gerenciador de Servidor**.

Reinicie o computador no nó do inspetor.

## Instalando os Arquivos de Configuração no Nó do Inspetor

Após a reinicialização do computador no nó de inspetor, sua próxima etapa será executar o arquivo Watchernode.msi. Para executar esse arquivo, abra o Shell de Gerenciamento do Lync Server 2013 clicando em **Iniciar**, em **Todos os Programas**, em **Lync Server 2013** e clicando em **Shell de Gerenciamento do Lync Server**. No Shell de Gerenciamento do Lync Server, digite o seguinte comando e pressione ENTER (tenha certeza e especifique o caminho real até sua cópia de Watchernode.msi):

    C:\Tools\Watchernode.msi Authentication=Negotiate

> [!NOTE]  
> Conforme indicado anteriormente, Watchernode.msi também pode ser executado a partir de uma janela de comando. Para abrir uma janela de comando, clique em <strong>Iniciar</strong>, clique com o botão direito do mouse em <strong>Prompt de Comando</strong> e clique em <strong>Executar como administrador</strong>. Quando a janela de comando for aberta, digite o mesmo comando exibido anteriormente.

O modo Negociar é usado sempre que o nó de inspetor não podem ser configurado como um pool de aplicativos confiável. Nesse modo, os administradores precisarão gerenciar as senhas do usuário de teste no nó de inspetor.

