---
title: 'Lync Server 2013: Habilitando usuários para E9-1-1'
TOCTitle: Habilitando usuários para E9-1-1
ms:assetid: 3cc64f5b-492e-4c47-9713-3c376f2aad02
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425892(v=OCS.15)
ms:contentKeyID: 49306448
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando usuários para E9-1-1 no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-06_

Durante o registro de cliente, o Lync Server usa uma política de local para configurar as propriedades de E9-1-1 de usuários habilitados para Enterprise Voice. Esta política contém as configurações que definem como o E9-1-1 é implementado. Por exemplo, a política de localização contém informações como a cadeia de caracteres de discagem de emergência e se um usuário precisa ou não digitar manualmente um local, caso o Serviço de Informações de Local não forneça um. Para obter uma definição completa de uma política de local, consulte [Definindo a política de local para Lync Server 2013](lync-server-2013-defining-the-location-policy.md).

O Lync Server pode atribuir uma política de local a clientes com base em uma sub-rede ou usuários com base em uma política global, por site ou por usuário. Para ajudar a decidir como você habilitará usuários, primeiro responda as perguntas a seguir.

  - **Você planeja habilitar todos os usuários ou limitar o suporte a áreas geográficas específicas da empresa?**  
    Você pode atribuir um local para todos os usuários em sua empresa usando uma política de local global. No entanto, ao atribuir uma política de local a um site de rede do Lync Server e ao adicionar sub-redes ao site, você pode limitar o suporte E9-1-1 a locais selecionados dentro da empresa e especificar o comportamento do roteamento E9-1-1 por site.

<!-- end list -->

  - **Você planeja habilitar usuários individuais por meio de uma política de usuário?**  
    Você pode atribuir políticas de local diretamente a usuários específicos ou a objetos de contato telefônico de área comum se deseja personalizar seu suporte do E9-1-1.

<!-- end list -->

  - **Quando clientes usam perfil móvel fora da rede ou conectam a partir de uma sub-rede indefinida, os clientes ainda devem ser habilitados para E9-1-1?**  
    Se os usuários recebem uma política de local global, por site ou por usuário, pode ser solicitado que eles insiram manualmente um local para o cliente se o cliente não está localizado em uma sub-rede definida ou se nenhum local foi encontrado pelo Serviço de Informações de Local. Para obter detalhes, consulte [Definindo a experiência do usuário para aquisição manual de local no Lync Server 2013](lync-server-2013-defining-the-user-experience-for-manually-acquiring-a-location.md).

