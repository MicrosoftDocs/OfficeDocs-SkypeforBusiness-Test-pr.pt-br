---
title: 'Lync Server 2013: Adquirindo um local'
TOCTitle: Adquirindo um local
ms:assetid: 9bf069aa-d240-4d95-be3a-e795537f8e70
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205110(v=OCS.15)
ms:contentKeyID: 49307604
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adquirindo um local no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-06_

Em uma implantação E9-1-1 do Lync Server 2013, cada Lync conectado internamente ou cliente do Lync Phone Edition adquire ativamente seu próprio local. Após o registro SIP, o cliente fornece todas as informações de conectividade de rede que ele sabe sobre si mesmo em uma solicitação local ao Serviço de Informações de Local, que é um serviço web apoiado por um banco de dados SQL Server replicado. Cada pool de site central tem um Serviço de Informações de Local, que usa as informações de rede para consultar um local correspondente em seus registros. Se houver uma correspondência, o Serviço de Informações de Local retorna um local ao cliente. Caso contrário, o usuário pode ser solicitado a inserir o local manualmente (dependendo das configurações de política de local). Os dados do local são transmitidos de volta ao cliente em um formato XML padronizado IETF (Internet Engineering Task Force) chamado Presence Information Data Format Location Object (PIDF-LO).

O cliente do Lync Server inclui os dados PIDF-LO como parte de uma chamada de emergência, e esses dados são usados pelo provedor de serviço E9-1-1 para determinar o PSAP apropriado e rotear a chamada a esse PSAP junto com o ESQK correto, que permite que o despachador PSAP obtenha o local do chamador.

O diagrama a seguir mostra como um cliente do Lync Server adquire um local (exceto para o método de local baseado em endereço MAC do cliente terceirizado):

![Diagrama de Como o cliente adquire um local](images/JJ205110.4438f5fc-f1b2-444b-8565-09035363ed43(OCS.15).jpg "Diagrama de Como o cliente adquire um local")

Para um cliente adquirir um local, as seguintes etapas devem ser executadas:

1.  O administrador preenche o banco de dados do Serviço de Informações de Local com o wiremap de rede (tabelas que mapeiam vários tipos de endereços de rede aos ERLs (Emergency Response Locations) correspondentes).

2.  Se você usar um provedor de serviço E9-1-1 do tronco SIP, o administrador validará as partes de endereço cívico do ERLs em comparação com um banco de dados de Guia principal de endereços de ruas (MSAG) mantido pelo provedor do serviço E9-1-1. Se você usar um gateway ELIN, o administrador garante que a operadora de PSTN fará o upload dos ELINs para o banco de dados de Identificação de local automática (ALI).

3.  Durante o registro ou sempre que a alteração de rede ocorrer, um cliente conectado internamente enviará uma solicitação de local que contém os endereços de rede descobertos do cliente para o Serviço de Informações de Local.

4.  O Serviço de Informações de Local consulta seus registros publicados em busca de um local e, se um resultado por encontrado, retorna o ERL ao cliente em formato PIDF-LO.

