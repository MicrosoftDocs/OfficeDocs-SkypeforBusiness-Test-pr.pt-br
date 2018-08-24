---
title: Get-CsService para gerenciamento de catálogo de endereços
TOCTitle: Get-CsService para gerenciamento de catálogo de endereços
ms:assetid: 373b717d-5efa-4c36-a899-a23a5bd922b4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429698(v=OCS.15)
ms:contentKeyID: 49306381
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsService para gerenciamento de catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros dos grupos a seguir estão autorizados a executar o cmdlet Get-CsService localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsService"}

O Get-CsService é valioso para recuperar e exibir a configuração atual do Serviços Web. definido para sua infraestrutura. Definindo o nome de domínio completamente qualificado (FQDN) do pool e o parâmetro WebServer, o cmdlet retorna os serviços baseados na web oferecidos pelo seu servidor, incluindo o manipulador da Agenda e os URIs de expansão da lista de distribuição.

Por exemplo:

    Get-CsService -PoolFqdn "fe01.contoso.net" -WebServer

Esse cmdlet retorna o seguinte:

Identity : WebServer:pool01.contoso.net

FileStore : FileStore:dc01.contoso.net

UserServer : UserServer:pool01.contoso.net

PrimaryHttpPort : 80

PrimaryHttpsPort : 443

ExternalHttpPort : 8080

ExternalHttpsPort : 4443

PublishedPrimaryHttpPort : 80

PublishedPrimaryHttpsPort : 443

PublishedExternalHttpPort : 80

PublishedExternalHttpsPort : 443

ReachPrimaryPsomServerPort : 8060

ReachExternalPsomServerPort : 8061

AppSharingPortStart : 49152

AppSharingPortCount : 16383

LIServiceInternalUri : https://internalweb.contoso.net/locationinformation/liservice.svc

ABHandlerInternalUri : https://internalweb.contoso.net/abs/handler

ABHandlerExternalUri : https://csweb.contoso.com/abs/handler

DLExpansionInternalUri : https://internalweb.contoso.net/groupexpansion/service.svc

DLExpansionExternalUri : https://csweb.contoso.com/groupexpansion/service.svc

CAHandlerInternalUri : https://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CAHandlerInternalAnonUri : http://internalweb.contoso.net/CertProv/CertProvisioningService.svc

CollabContentInternalUri : https://internalweb.contoso.net/CollabContent

CollabContentExternalUri : https://csweb.contoso.com/CollabContent

CAHandlerExternalUri : https://csweb.contoso.com/CertProv/CertProvisioningService.svc

DeviceUpdateDownloadInternalUri : https://internalweb.contoso.net/RequestHandler/ucdevice.upx

DeviceUpdateDownloadExternalUri : https://csweb.contoso.com/RequestHandlerExt/ucdevice.upx

DeviceUpdateStoreInternalUri : http://internalweb.contoso.net/RequestHandler/Files

DeviceUpdateStoreExternalUri : https://csweb.contoso.com/RequestHandlerExt/Files

RgsAgentServiceInternalUri : https://internalweb.contoso.net/RgsClients/AgentService.svc

RgsAgentServiceExternalUri : https://csweb.contoso.com/RgsClients/AgentService.svc

MeetExternalUri : https://csweb.contoso.com/Meet

DialinExternalUri : https://csweb.contoso.com/Dialin

CscpInternalUri : https://internalweb.contoso.net/Cscp

ReachExternalUri : https://csweb.contoso.com/Reach

ReachInternalUri : https://internalweb.contoso.net/Reach

WebTicketExternalUri : https://csweb.contoso.com/WebTicket/WebTicketService.svc

WebTicketInternalUri : https://internalweb.contoso.net/WebTicket/WebTicketService.svc

ExternalFqdn : csweb.contoso.com

InternalFqdn : internalweb.contoso.net

DependentServiceList : {Registrar:pool01.contoso.net, ConferencingServer:pool01.contoso.net}

ServiceId : 1-WebServices-1

SiteId : Site:Redmond

PoolFqdn : pool01.contoso.net

Version : 5

Role : WebServer

Para obter uma descrição detalhada do comando completo, consulte o seguinte na principal referência de RTCCmdlets do Lync Server Windows PowerShell.

## Consulte Também

#### Outros Recursos

[Get-CsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService)

