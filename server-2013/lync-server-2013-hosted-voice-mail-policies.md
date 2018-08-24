---
title: 'Lync Server 2013: Políticas de correio de voz hospedado'
TOCTitle: Políticas de correio de voz hospedado
ms:assetid: d62a35ed-cbe2-4f06-86b4-e192c18435c1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398932(v=OCS.15)
ms:contentKeyID: 49308245
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Políticas de correio de voz hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Uma *política de caixa postal hospedada* fornece informações ao aplicativo ExUM Routing do Lync Server 2013 sobre o local para onde rotear chamadas dos usuários cujas caixas postais estão localizadas em um serviço do Exchange hospedado.

> [!NOTE]  
> As políticas de caixa postal hospedadas são necessárias somente para a integração do Lync Server 2013 com o UM do Exchange hospedada. Elas não são necessárias para integração com UM do Exchange local.

## Escopo da política de caixa postal hospedada

O escopo da política de caixa postal hospedada determina o nível hierárquico no qual a política é aplicada. É possível configurar as políticas de caixa postal hospedadas com os seguintes níveis de escopo:

  - A política *global* pode afetar potencialmente todos os usuários na implantação do Lync Server 2013. Se um usuário for habilitado para acesso à UM do Exchange hospedada e não tiver recebido uma política por usuário, e se uma política de site não tiver sido atribuída ao site do usuário, a política global será aplicada. A política global é instalada com o Lync Server 2013. É possível modificá-la para atender a suas necessidades, mas não é possível renomeá-la ou excluí-la.

  - Uma política de *site* pode afetar todos os usuários hospedados no site para o qual a política foi definida. Se um usuário for configurado para receber acesso à UM do Exchange hospedada e não tiver recebido uma política por usuário, a política de site será aplicada.

  - Uma política *por usuário* pode afetar somente usuários ou grupos individuais. Para aplicar uma política por usuário, você precisa atribuir explicitamente a política a usuários individuais, grupos e objetos de contato.

> [!NOTE]  
> Na maioria dos casos, somente a política de caixa postal hospedada é necessário. É possível modificar com frequência a política global a fim de atender a todas as suas necessidades. Se você implantar múltiplas políticas de caixa postal hospedadas, todas essas políticas terão um escopo por usuário.

## Atributos de política de caixa postal hospedada

Uma política de caixa postal define dois atributos que o aplicativo ExUM Routing do Lync Server 2013 insere no URI de solicitação de uma mensagem INVITE enviada à implementação da UM do Exchange hospedada:

  - **Destino :** o FQDN (Nome de domínio totalmente qualificado) do serviço UM do Exchange hospedado. Esse valor é usado pelo Servidor de Borda local do Lync Server para roteamento.
    
    > [!NOTE]  
    > O FQDN para Exchange Online é exap.um.outlook.com.

  - **Organização :** o FQDN do inquilino no serviço de UM do Exchange hospedada que hospeda as caixas postais de seu usuário do Lync Server 2013. Uma política de caixa postal pode conter várias organizações. Se mais de uma organização for incluída na política, esse atributo deverá ser uma lista separada por vírgula dos inquilinos do Exchange Server que hospedam as caixas postais de seu usuário do Lync Server 2013.

> [!NOTE]  
> O administrador de inquilino de seu serviço de UM do Exchange hospedada fornecerá os valores necessários para suas configurações de Destino e Organização. Para configurar sua política, você precisa executar o cmdlet New-CsHostedVoicemailPolicy ou usar o cmdlet Set-CsHostedVoicemailPolicy para modificar um que exista (por exemplo, a política global).

Para obter detalhes sobre como gerenciar políticas de caixa postal hospedadas, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - New-CsHostedVoicemailPolicy

  - Set-CsHostedVoicemailPolicy

  - Get-CsHostedVoicemailPolicy

## Atribuição da política de caixa postal por usuário

Se sua política de caixa postal hospedada for definida com escopo por usuário, será necessária atribuí-la explicitamente. É possível executar o cmdlet Grant-CsHostedVoicemailPolicy a fim de atribuir a política a usuários ou grupos individuais.

Para obter detalhes sobre como atribuir ou remover uma política de caixa postal hospedada por usuário, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - Grant-CsHostedVoicemailPolicy

  - Remove-CsHostedVoicemailPolicy

