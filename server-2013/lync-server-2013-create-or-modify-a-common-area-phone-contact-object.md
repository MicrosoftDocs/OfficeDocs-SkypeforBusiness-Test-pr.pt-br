---
title: Criar ou modificar o objeto de contato de um telefone de área comum
TOCTitle: Criar ou modificar o objeto de contato de um telefone de área comum
ms:assetid: eec33ad1-e4f2-49b2-91d6-d5a9d2e1714b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994083(v=OCS.15)
ms:contentKeyID: 52057761
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar o objeto de contato de um telefone de área comum

 

_**Tópico modificado em:** 2013-02-20_

Para criar objetos de contato do Serviços de Domínio Active Directory para todos os seus telefones de área comum, use o cmdlet **New-CsCommonAreaPhone**. Este cmdlet pode criar novos objetos de contato a serem usados com telefones de área comum ou pode associar os objetos de contato existentes a um novo telefone de área comum. Para modificar as propriedades dos objetos de contatos associados a telefones de área comum, use o cmdlet **Set-CsCommonAreaPhone**. Parâmetros opcionais do **Set-CsCommonAreaPhone** permitem que você altere itens, como o nome de exibição do Active Directory do contato ou o URI (Uniform Resource Identifier) da linha associado ao telefone, além de habilitar e desabilitar a conta para o uso com o Lync Server. Para obter detalhes sobre todas as modificações disponíveis, consulte a seção Parâmetros em [Set-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCommonAreaPhone). Para obter detalhes sobre os parâmetros do **New-CsCommonAreaPhone**, consulte [New-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCommonAreaPhone).

Você pode executar esses dois cmdlets a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).


## Criando um objeto de contato de um telefone de área comum

  - Para criar um novo objeto de contato de um telefone de área comum, use o cmdlet **New-CsCommonAreaPhone**. Minimamente, você deve especificar as seguintes informações ao criar um objeto de contato:
    
      - **LineUri**: o número de telefone atribuído ao telefone de área comum. Observe que você deve usar o formato E.164 ao especificar o número de telefone.
    
      - **RegistrarPool**: o FQDN (nome de domínio totalmente qualificado) do pool de registradores que hospedará o objeto de contato.
    
      - **OU**: nome diferenciado do contêiner do Active Directory onde o objeto de contato será criado.
    
    Recomendamos também que você forneça um nome de exibição do Serviços de Domínio Active Directory. Caso contrário, você precisará usar um GUID (identificador exclusivo) para especificar a identidade do telefone. Por exemplo:
    
        New-CsCommonAreaPhone -LineUri "tel:+12065551219" -RegistrarPool "atl-cs-001.litwareinc.com" -OU "OU=Phones,dc=litwareinc,dc=com" -DisplayName "Lobby"

## Modificando um objeto de contato de um telefone de área comum

  - Para modificar as propriedades de um objeto de contato de um telefone de área comum existente, use o cmdlet **Set-CsCommonAreaPhone**. Por exemplo, este comando configura o endereço SIP do telefone de área comum com o lobby DisplayName:
    
        Set-CsCommonAreaPhone -Identity "Lobby" -SipAddress "sip:lobby@litwareinc.com"

Para obter detalhes, consulte os tópicos da Ajuda parar os cmdlets [New-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCommonAreaPhone) e [Set-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCommonAreaPhone).

