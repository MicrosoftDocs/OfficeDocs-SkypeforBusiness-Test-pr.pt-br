---
title: Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado
TOCTitle: Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado
ms:assetid: 6aa17ae3-764e-4986-a900-85a3cdb8c1fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688083(v=OCS.15)
ms:contentKeyID: 49886251
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Microsoft Lync Server 2013 para usar o repositório de contato unificado

 

_**Tópico modificado em:** 2014-02-07_

O repositório unificado de contatos permite que os usuários mantenham uma única lista de contatos e tenham acesso a eles em vários aplicativos, incluindo o Microsoft Lync 2013, o Microsoft Outlook 2013 e o Microsoft Outlook Web App 2013. Quando você habilita o repositório unificado de contatos para um usuário, os contatos desse usuário não são armazenados no Microsoft Lync Server 2013 e depois recuperados com o uso do protocolo SIP. Em vez disso, os contatos são armazenados no Microsoft Exchange Server 2013 e são recuperados com o uso dos Serviços Web do Exchange.

> [!NOTE]  
> Tecnicamente, as informações de contato são armazenadas em um par de pastas localizadas na caixa de correio do Exchange 2013 do usuário. Os contatos em si são armazenados em uma pasta chamada Lync Contacts, que é visível para os usuários finais. Os metadados sobre os contatos são armazenados em uma subpasta que não é visível para os usuários finais.

## Habilitando o repositório unificado de contatos para um usuário

Se você já configurou a autenticação servidor a servidor entre o Lync Server 2013 e o Exchange 2013, automaticamente já habilitou o uso do repositório unificado de contatos e nenhuma configuração de servidor adicional será necessária. No entanto, será necessária configuração adicional da conta do usuário para transferir os contatos de um usuário para o repositório unificado de contatos. Por padrão, os contatos do usuário são mantidos no Lync Server e não no repositório unificado de contatos.

O acesso ao repositório unificado de contatos é gerenciado pelo uso de políticas de serviços de usuário do Lync Server. As políticas de serviços de usuário têm uma única propriedade (UcsAllowed), que é usada para determinar o local onde os contatos de um usuário são armazenados. Se um usuário for gerenciado por uma política de serviços de usuário em que UcsAllowed foi definida como True ($True), os contatos do usuário serão armazenados no repositório unificado de conatos. Se o usuário for gerenciado por uma política de serviços de usuário em que UcsAllowed foi definida como False ($False), seus contatos serão armazenados no Lync Server.

Quando você instala o Lync Server 2013, uma política de serviços de usuário único (configurada no escopo global) é instalada também. O valor de UcsAllowed nessa política é definido como True, o que significa que, por padrão, os contatos do usuário serão colocados no repositório unificado de contatos (presumindo que ele tenha sido implantado e configurado). Se você quiser migrar todos os seus contatos de usuário para o repositório unificado de contatos,não será necessário fazer nada.

Se você preferir não migrar todos os contatos para o repositório unificado de contatos, desabilite esse repositório para todos os usuários configurando a propriedade UcsAllowed na política global como False:

    Set-CsUserServicesPolicy -Identity global -UcsAllowed $False

Depois que desabilitar o repositório unificado de contatos na política global, você poderá criar uma política por usuário que permita a utilização desse repositório; isso permitirá que alguns usuários mantenham seus contatos no repositório unificado de contatos, enquanto outros usuários continuam mantendo seus contatos no Lync Server. É possível criar uma política de serviços de usuário por usuário utilizando um comando como este:

    New-CsUserServicesPolicy -Identity "AllowUnifiedContactStore" -UcsAllowed $True

Depois que você tiver criado a nova política, precisará atribuí-la aos usuários que deverão ter acesso ao repositório unificado de contatos. As políticas por usuário podem ser atribuídas aos usuários com o uso de comandos semelhantes ao seguinte:

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "AllowUnifiedContactStore"

Depois que a política for atribuída, o Lync Server começará a migrar os contatos do usuário para o repositório unificado de contatos. Após a conclusão da migração, os contatos do usuário estarão armazenados no Exchange em vez do Lync Server. Se o usuário estiver conectado ao Lync 2013 no momento da conclusão da migração, uma caixa de mensagem será exibida solicitando que ele se desconecte do Lync e depois faça logon novamente para finalizar o processo. Os usuários que não tiverem recebido essa política por usuário não terão seus contatos migrados para o repositório unificado de contatos. Isso ocorre porque esses usuários estão sendo gerenciados pela política global e o uso desse repositório foi desabilitado na política global.

Você pode confirmar se os contatos do usuário foram migrados com êxito para o repositório unificado de contatos executando o cmdlet [Test-CsUnifiedContactStore](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUnifiedContactStore) a partir do Shell de Gerenciamento do Lync Server:

    Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"

Se Test-CsUnifiedContactStore for bem-sucedido, significa que os contatos do usuário sip:kenmyer@litwareinc.com foram migrados para o repositório unificado de contatos.

## Revertendo o repositório unificado de contatos

Se você precisar remover os contatos de um usuário do repositório unificado de contatos (por exemplo, se o usuário precisar ser hospedado no Microsoft Lync Server 2010 e consequentemente não puder mais usar o repositório unificado de contatos), será necessário executar dois procedimentos. Primeiro, atribua ao usuário uma nova política de serviços de usuário que proíba o armazenamento dos contatos no repositório unificado de contatos (ou seja, uma política cuja propriedade UcsAllowed seja definida como $False). Se essa política ainda não existir, você poderá criar uma usando um comando semelhante ao seguinte:

    New-CsUserServicesPolicy -Identity NoUnifiedContactStore -UcsAllowed $False

Em seguida, você pode atribuir essa nova política por usuário (NoUnifiedContactStore) usando um comando como o seguinte:

    Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName NoUnifiedContactStore

O comando anterior atribui a nova política ao usuário Ken Myer e também impede que os contatos de Ken sejam migrados para o repositório unificado de contatos.

> [!NOTE]  
> Em alguns casos, é possível obter o mesmo efeito simplesmente cancelando a atribuição da política de serviços de usuário atual do usuário. Por exemplo, suponha que Ken Myer tenha uma política de serviços de usuário por usuário que habilita o repositório unificado de contatos, mas sua política global proíbe o uso do repositório unificado de contatos. Nesse caso, você pode cancelar a atribuição da política de serviços por usuário de Ken. Quando você fizer isso, Ken será automaticamente gerenciado pela política global e deixará de ter acesso ao repositório unificado de contatos.<br />Para cancelar a atribuição de uma política por usuário atribuída anteriormente, use o mesmo comando mostrado antes, mas, desta vez, defina o parâmetro PolicyName para um valor nulo:<br />Grant-CsUserServicesPolicy –Identity &quot;Ken Myer&quot; –NomedaPolítica $Null

É importante lembrar-se da frase "impede que os contatos de Ken sejam migrados para o repositório unificado de contatos" ao trabalhar com o repositório unificado de contatos. Simplesmente atribuir uma nova política de serviços de usuário a Ken não removerá seus contatos do repositório unificado de contatos. Quando um usuário faz logon no Lync Server 2013, o sistema verifica a política de serviços de usuário do usuário para ver se seus contatos devem ser mantidos no repositório unificado de contatos. Se a resposta for sim (ou seja, se a propriedade UcsAllowed estiver definida como $True), esses contatos serão migrados para o repositório unificado de contatos (pressupondo que eles ainda não estejam no repositório unificado de contatos). Se a resposta for não, o Lync Server simplesmente ignorará os contatos do usuário e passará para a próxima tarefa. Isso significa que o Lync Server não removerá automaticamente os contatos de um usuário do repositório unificado de contatos, independentemente do valor da propriedade UcsAllowed.

Isso também significa que, após atribuir uma nova política de serviços de usuário ao usuário, você precisará executar o cmdlet [Invoke-CsUcsRollback](https://docs.microsoft.com/en-us/powershell/module/skype/Invoke-CsUcsRollback) para retirar os contatos do usuário do Exchange 2013 e recolocá-los no Lync Server 2013. Por exemplo, após atribuir uma nova política de serviços de usuário a Ken Myer, você poderá remover seus contatos do repositório unificado de contatos usando o seguinte comando:

    Invoke-CsUcsRollback -Identity "Ken Myer"

Se você alterar a política de serviços de usuário, mas não executar o cmdlet Invoke-CsUcsRollback, os contatos de Ken não serão removidos do repositório unificado de contatos. E se você executar o Invoke-CsUcsRollback, mas não alterar a política de serviços de usuário de Ken Myer? Nesse caso, os contatos de Ken serão temporariamente removidos do repositório unificado de contatos. É importante atentar ao fato de que essa remoção é temporária. Depois que os contatos de Ken forem removidos do repositório unificado de contatos, o Lync Server 2013 aguardará sete dias e verificará qual política de serviços de usuário está atribuída a Ken. Se uma política que permite o uso do repositório unificado de contatos ainda estiver atribuída a Ken, seus contatos serão automaticamente transferidos de volta para o repositório de contatos. Para remover permanentemente os contatos do repositório unificado de contatos, você precisa alterar a política de serviços de usuário e também executar o cmdlet Invoke-CsUcsRollback.

Devido ao grande número de variáveis que podem afetar a migração, é difícil estimar o tempo que será necessário antes de as contas serem totalmente migradas para o repositório unificado de contatos. No entanto, como regra geral, a migração não tem efeito imediatamente: até mesmo durante a migração de um pequeno número de contatos, isso poderá demorar 10 minutos ou mais antes da conclusão da migração.

