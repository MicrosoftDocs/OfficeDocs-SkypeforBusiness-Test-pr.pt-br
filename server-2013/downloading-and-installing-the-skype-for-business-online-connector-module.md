---
title: Baixar e instalar módulo do Conector do Lync Online
TOCTitle: Baixar e instalar módulo do Conector do Lync Online
ms:assetid: a0c87219-b642-4201-85d4-a85c2163d1eb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362829(v=OCS.15)
ms:contentKeyID: 56270455
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Baixar e instalar módulo do Conector do Lync Online

 

_**Tópico modificado em:** 2016-12-08_

O módulo do Conector do Skype for Business Online inclui o cmdlet **New-CsOnlineSession**, que permite criar uma sessão remota do Windows PowerShell que se conecta ao Skype for Business Online. Este módulo, que é suportado apenas em computadores de 64 bits (consulte [Configurando o Computador Gerenciamento do Lync Online](configuring-your-computer-for-skype-for-business-online-management.md) para obter mais informações), pode ser baixado no Central de Download da Microsoft no [http://go.microsoft.com/fwlink/?LinkId=294688](http://go.microsoft.com/fwlink/?linkid=294688). Baixe o arquivo LyncOnlinePowershell.exe e conclua o seguinte procedimento:

1.  Clique duas vezes no arquivo **LyncOnlinePowershell.exe**.

2.  No assistente de configuração do PowerShell de inquilino do Skype for Business Online, na página **Microsoft Software License Terms**, selecione **I accept the terms in the License Agreement** e clique em **Install**. Se a caixa de diálogo **User Account Control** aparecer, clique em **Yes** para continuar a instalação.

3.  Na página **Completed the Microsoft Lync Online, Tenant PowerShell Setup**, clique em **Finish**.

O programa de instalação copia o módulo do Conector do Skype for Business Online (e o cmdlet **New-CsOnlineSession**) para seu computador local. Para acessar o módulo, inicie uma sessão do Windows PowerShell sob as credenciais de administrador e execute o seguinte comando:

    Import-Module LyncOnlineConnector

Se não quiser digitar o comando toda vez que você iniciar o Windows PowerShell, pode adicionar o comando ao seu perfil do Windows PowerShell. Para isso, digite o seguinte comando no prompt Windows PowerShell e pressione ENTER:

    notepad.exe $profile

Quando o Bloco de notas aparecer, adicione a seguinte linha na parte inferior dos comandos que já estão no perfil (se houver):

    Import-Module LyncOnlineConnector

Salve o arquivo. A próxima vez que você iniciar o Windows PowerShell, o módulo do Conector do Skype for Business Online será automaticamente importado. Esteja ciente de que receberá uma mensagem de erro e o módulo não será carregado, se você não estiver executando o Windows PowerShell com as credenciais de administrador.

Além de instalar o módulo do Conector do Skype for Business Online, o LyncOnlinePowershell.exe também instala dois componentes adicionais: o pacote .NET Framework 4.5 e o Microsoft Visual C++ 2012 Redistributable (x64) (versão 11.0.50727). O .NET Framework 4.5 fornece a infraestrutura utilizada para construção e execução de aplicativos .NET, incluindo Windows PowerShell. O pacote Visual C++ Redistributable instala componentes do tempo de execução do Visual C++ para computadores que não têm o Microsoft Visual Studio 2012 instalado.

## Consulte Também

#### Conceitos

[Configurando o Computador Gerenciamento do Lync Online](configuring-your-computer-for-skype-for-business-online-management.md)

