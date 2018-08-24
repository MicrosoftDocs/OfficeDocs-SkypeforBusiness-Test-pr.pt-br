---
title: 'Lync Server 2013: Gerenciamento de objeto de Contato no Exchange hospedado'
TOCTitle: Gerenciamento de objeto de Contato no Exchange hospedado
ms:assetid: eead9d76-bc4f-4c1c-9779-683cb7a88410
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412978(v=OCS.15)
ms:contentKeyID: 49308523
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciamento de objeto de Contato no Exchange hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-25_

É preciso configurar um objeto de Contato para cada número de atendedor automático e número de telefone do assinante na implantação em vários locais.

Para integração com a UM do Exchange hospedada, o ocsumutil.exe não pode ser usado para gerenciar objetos de Contato, pois ele depende das configurações de UM do Exchange do Active Directory. Em uma implantação entre instalações, o Lync Server 2013 e a UM do Exchange hospedada são instalados em florestas separadas sem confiança entre eles. Por motivos de segurança, os administradores do Lync Server 2013 não têm acesso direto às configurações de UM do Exchange do Active Directory. Como resultado, o Lync Server 2013 fornece um modelo diferente para gerenciar objetos de Contato em um *espaço de endereço SIP compartilhado* acessível ao Lync Server 2013 e ao serviço UM do Exchange hospedado.

## Fluxo de trabalho de objeto de contato hospedado

Veja a seguir as etapas gerais para trabalhar com seu administrador de inquilino do Exchange hospedado para gerenciar objetos de contato:

1.  O administrador do Exchange solicita números de telefone para acesso do assinante da UM do Exchange e objetos de Contato do atendedor automático.

2.  O administrador do Lync Server 2013 cria um objeto de Contato para cada número de telefone e atribui uma política de caixa postal hospedada a cada objeto de Contato.

3.  O administrador do Lync Server 2013 fornece os números de telefone ao administrador do Exchange.

4.  O administrador do Exchange atribui os números de telefone aos planos de discagem de UM do Exchange apropriados para acesso dos atendedores automáticos e do assinante.

> [!NOTE]  
> Não há necessidade de configurar um plano de discagem do Lync Server 2013 nos objetos de Contato da mesma forma que há com as implantações em instalações.

## Configurando os objetos de contato

> [!NOTE]  
> Antes de os objetos de Contato do Lync Server 2013 poderem ser habilitados para a UM do Exchange hospedada, é preciso implantar uma política de caixa postal hospedada que se aplica a eles. A política pode ser de nível global, de site ou com um escopo por usuário, contanto que se aplique ao objeto de contato que você deseja habilitar. Para obter detalhes, consulte <a href="lync-server-2013-hosted-voice-mail-policies.md">Políticas de correio de voz hospedado no Lync Server 2013</a>.

Para configurar os objetos de Contato de acesso hospedado do atendedor automático e do assinante em uma implantação entre instalações, é necessário usar os seguintes cmdlets:

  - **New-CsExUmContact** cria um novo objeto de Contato para a UM hospedada.

  - **Set-CsExUmContact** modifica um objeto de Contato existente para a UM do Exchange hospedada.

O exemplo a seguir cria um objeto de Contato de atendedor automático:

    New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True

Este exemplo cria um novo objeto de Contato de UM do Exchange com o endereço SIP sip:exumaa1@fabrikam.com. O nome do pool onde o serviço Registrador do Lync Server 2013 está em execução é RedmondPool.litwareinc.com. A unidade organizacional do Active Directory onde essas informações serão armazenadas é OU=ExUmContacts,DC=litwareinc,DC=com. O número de telefone do objeto de Contato é 2065554567. O parâmetro opcional -AutoAttendant $True especifica que esse objeto é um objeto de Contato de atendedor automático. A configuração do parâmetro -AutoAttendant para Falso (padrão) especifica um objeto de Contato de acesso do assinante.

Para obter detalhes sobre os cmdlets New-CsExUmContact e Set-CsExUmContact, consulte a documentação do Shell de Gerenciamento do Lync Server.

