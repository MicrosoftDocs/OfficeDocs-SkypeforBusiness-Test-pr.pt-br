---
title: 'Lync Server 2013: Definir um gateway de PSTN para um site de filial'
TOCTitle: Definir um gateway de PSTN para um site de filial
ms:assetid: 87be2fe2-1d56-4062-b430-439d4536414c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398689(v=OCS.15)
ms:contentKeyID: 49307374
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir um gateway de PSTN para um site de filial no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Execute este procedimento no local central, que contém pelo menos um Pool de Front-Ends ou Servidor Standard Edition.

> [!IMPORTANT]  
> Antes de executar o procedimento, as seguintes condições devem estar presentes:<ul>
> 
> <li><p>O Lync Server 2013software de comunicação deve ser definido no site central.</p></li>
> 
> 
> <li><p>O Servidor de Mediação deve ser implantado no site central.</p></li></ul>


## Para definir um gateway PSTN

1.  Clique em **Iniciar** , **Todos os programas** , **Microsoft Lync Server** e em **Construtor de topologias do Lync Server** .

2.  Na árvore do console, expanda o site central, expanda **Sites de filial do escritório** e expanda o nome do site da filial para o qual você deseja definir um gateway PSTN (rede telefônica pública comutada) e expanda **Componentes compartilhados** .

3.  Clique com o botão direito do mouse em **Gateways PSTN** e clique em **Novo gateway IP/PSTN** .

4.  Na caixa de diálogo **Definir novo gateway IP/PSTN** , clique em **FQDN ou endereço IP do gateway** e digite o FQDN ou endereço IP do gateway que você vai implantar na filial.

5.  Clique em **Porta de escuta do Gateway IP/PSTN** e aceite os valores padrão.

6.  Na lista **Protocolo de Transporte SIP** , clique no protocolo de transporte que o gateway usa e em **OK** .
    
    > [!NOTE]  
    > Por motivos de segurança, recomendamos que você use um gateway PSTN que oferece suporte à segurança de camada de transporte (TLS).


> [!TIP]
> Use o cmdlet <STRONG>Set-CsPstnGateway</STRONG> para modificar as propriedades de um gateway PSTN. Para obter mais detalhes, consulte <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsPstnGateway">Set-CsPstnGateway</A>, na Ajuda do Shell de Gerenciamento do Lync Server.



**Próxima etapa** para a resiliência do site da filial: [Configurando usuários para resiliência de site da filial no Lync Server 2013](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

## Consulte Também

#### Conceitos

[Opções de implantação do gateway PSTN no Lync Server 2013](lync-server-2013-pstn-gateway-deployment-options.md)

