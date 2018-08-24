---
title: 'Lync Server 2013: Planejamento de linhas de telefone privadas'
TOCTitle: Planejamento de linhas de telefone privadas
ms:assetid: 9cc4f9e1-7b7a-4699-bd05-f16669ef2d21
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412728(v=OCS.15)
ms:contentKeyID: 49307597
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de linhas de telefone privadas com Lync Server 2013

 

_**Tópico modificado em:** 2013-02-11_

O  Lync Server 2013 apresenta a capacidade de oferecer aos usuários uma segunda linha telefônica privada, além da linha telefônica principal. Linhas telefônicas privadas são frequentemente atribuídas a executivos e a outras pessoas que desejam um número de telefone não esteja listado e através do qual podem ser diretamente contatados.

Linhas telefônicas privadas só podem ser configuradas com o Shell de Gerenciamento do Lync Server. Não é possível configurar linhas telefônicas privadas com o Painel de Controle do Lync Server. Estas linhas devem ser configuradas somente em implantações do Lync Server e não em implantações mistas.

## Características das linhas telefônicas privadas

Embora o conceito de uma linha telefônica privada, secundária, seja fundamentalmente simples, é importante compreender as características das linhas privadas e as formas em que são similares e diferentes das linhas telefônicas principais dos usuários.

## Características gerais das linhas telefônicas privadas

  - Um usuário pode ter somente uma linha telefônica privada.

  - Um usuário com uma linha telefônica privada só possui uma caixa postal e recebe notificações de chamadas perdidas em um único endereço de e-mail.

  - Um usuário com uma linha telefônica privada não possui um segundo endereço SIP e uma linha telefônica privada secundária não dá a ele uma segunda presença na rede (como uma segunda identidade no sistema de mensagens instantâneas).

  - Linhas telefônicas privadas estão disponíveis somente para implantações locais. Não estão disponíveis com implantações hospedadas do Lync Server.

## Como linhas telefônicas privadas diferem de linhas telefônicas principais

  - Os números de telefone para linhas telefônicas privadas não aparecem nos diretórios telefônicos ou listas de Contatos derivados dos Serviços de Domínio do Active Directory.

  - Nenhum dos recursos a seguir está disponível com uma linha telefônica privada: encaminhamento de chamadas, chamada de equipe, delegação, toque de equipe, recebimento de chamadas de grupo e aplicativo Grupo de Resposta.

  - Chamadas para uma linha telefônica privada possuem um toque especial e a notificação do sistema para as chamadas diz ao usuário que a chamada de entrada está em sua linha privada.

  - Chamadas para a linha telefônica privada sempre tocam. Elas não seguem as regras "não incomodar".

  - Linhas telefônicas privadas são somente de entrada e não podem ser usadas para fazer chamadas de saída. Quando um usuário com uma linha telefônica privada faz uma ligação, a chamada é originada na linha telefônica principal e não oculta do receptor da chamada o nome ou o número de telefone principal do usuário.

## Como linhas telefônicas privadas são similares a linhas telefônicas principais

  - Chamadas não atendidas para uma linha telefônica privada são roteadas para a mesma caixa postal da linha telefônica principal (se a caixa postal estiver habilitada).

  - O estacionamento e o recebimento de chamadas funcionam com linhas telefônicas privadas exatamente da mesma forma como na linha telefônica principal do usuário.

  - Quando o toque simultâneo está habilitado na linha telefônica principal de um usuário, também está habilitado na linha telefônica privada.

  - O número de telefone para uma linha telefônica privada é gravado no registro de detalhes de chamada da mesma maneira que o número de telefone para a linha telefônica principal de um usuário, mas com uma indicação de que é um número telefônico privado.

  - Depois que o usuário atende uma chamada na linha telefônica privada, ela é tratada da mesma forma como se estivesse na linha telefônica principal. Por exemplo, se um usuário que recebe uma ligação em uma linha telefônica privada, encaminhar a chamada ou convidar outros para uma chamada em conferência, o nome do usuário aparecerá no Lync 2013 e o número do telefone para a linha telefônica principal do usuário aparece no ID do chamador.

  - Um usuário pode desviar uma chamada (redirecionar para outro destino, como um telefone celular ou residencial, antes de atender) a partir da linha telefônica privada da mesma maneira como o faria com uma linha telefônica principal.
    
    > [!NOTE]  
    > Quando uma chamada para uma linha privada é roteada para um número de telefone alternativo, o número para a linha telefônica privada é disponibilizado para o número de telefone alternativo e pode ser exibido nos logs para aquele número.    
    > [!NOTE]  
    > Chamadas a partir de uma conferência para a linha telefônica privada não terão uma indicação de <em>linha privada</em> na notificação do sistema de entrada.

## Como administrar linhas telefônicas privadas

Além dos aspectos técnicos da criação e gerenciamento de linhas telefônicas privadas, você precisará estabelecer procedimentos administrativos para elas. Isso inclui determinar políticas para quem na organização está elegível para uma linha privada, criar e manter listas de pessoas e suas linhas telefônicas, possivelmente criar um diretório de telefonia privada para executivos, providenciar o treinamento dos usuários e tarefas relacionadas.

> [!NOTE]  
> A linha telefônica privada é armazenada no Active Directory como um atributo msRTCSIP-PrivateLine no objeto do usuário. Por padrão, qualquer membro do grupo Usuários Autenticados tem acesso de leitura a este atributo.

## Como atribuir números de telefone

Contas para novos usuários que precisam de linhas telefônicas privadas são criadas da mesma maneira como as contas sem linhas telefônicas privadas, usando o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server.

Use o cmdlet **Set-CsUser** no Shell de Gerenciamento do Lync Server para atribuir um número de telefone a uma linha telefônica privada para um usuário, por exemplo, **Set-CsUser -Identity "sip:joe@contoso.com" -PrivateLine "Tel:+14255551212"** .

Números de telefone para linhas telefônicas privadas podem ter entre 3 e 15 números de comprimento e devem ser precedidos pelo prefixo "TEL:". Podem ter qualquer código de área e qualquer código de país/região, desde que sua organização tenha discagem interna direta para aquele código de área e código de país/região.

Para detalhes sobre cmdlets e o Shell de Gerenciamento do Lync Server, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Linhas telefônicas privadas em implantações mistas

Linhas telefônicas privadas devem ser configuradas somente para implantações do Lync Server. Em uma implantação em que existem ambos os servidores do Lync Server e Office Communications Server 2007 ou Office Communications Server 2007 R2, quando um usuário da versão anterior tentar fazer uma chamada para uma linha telefônica privada, o roteamento da chamada falhará porque o servidor não conseguirá executar uma pesquisa de número reversa em uma linha telefônica privada.

