---
title: Validar endereços
TOCTitle: Validar endereços
ms:assetid: aae557c9-e6f5-4d23-8af1-1d4cd7968c54
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412808(v=OCS.15)
ms:contentKeyID: 49307756
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Validar endereços

 

_**Tópico modificado em:** 2012-09-17_

Antes de publicar o banco de dados local, você deverá validar novas localizações em relação ao MSAG (Master Street Address Guide) mantido pelo seu tronco SIP ou pelo provedor de serviços de rede telefônica pública comutada (PSTN) E9-1-1.

Para detalhes sobre provedores de serviços de E9-1-1 do tronco SIP, consulte [Selecionando um fornecedor de serviço E9-1-1 para Lync Server 2013](lync-server-2013-choosing-an-e9-1-1-service-provider.md).

Para obter detalhes sobre como validar endereços, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - **Get-CsLisServiceProvider**

  - **Set-CsLisServiceProvider**

  - **Remove-CsLisServiceProvider**

  - **Get-CsLisCivicAddress**

  - **Test-CsLisCivicAddress**

## Para validar endereços localizados no banco de dados de localização

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute os cmdlets a seguir para configurar a conexão com o provedor de serviços de emergência.
    
        $pwd = Read-Host -AsSecureString <password>
        Set-CsLisServiceProvider -ServiceProviderName Provider1 -ValidationServiceUrl <URL provided by provider> -CertFileName <location of certificate provided by provider> -Password $pwd

3.  Execute o cmdlet a seguir para validar os endereços no banco de dados de localização.
    
        Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus
    
    Você também pode usar o cmdlet **Test-CsLisCivicAddress** para validar endereços individuais.

