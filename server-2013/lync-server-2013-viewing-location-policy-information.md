---
title: Visualizando informações de política de local
TOCTitle: Visualizando informações de política de local
ms:assetid: 14e41bcb-ea0a-49c2-99b3-1f61fc34416d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520954(v=OCS.15)
ms:contentKeyID: 49305975
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizando informações de política de local

 

_**Tópico modificado em:** 2012-11-01_

No Lync Server 2013, você pode usar a política de local para aplicar configurações relacionadas à funcionalidade do 9-1-1 Avançado (E9-1-1) e às configurações de local de usuários ou contatos. A política de local determina se o usuário está habilitado para o E9-1-1 e, se estiver, qual vai ser o comportamento de uma chamada de emergência. Por exemplo, é possível usar a política de local para definir o número que constitui uma chamada de emergência (911 nos Estados Unidos), se a segurança da empresa deve ser automaticamente notificada e como a chamada é roteada.

Você pode configurar as políticas de local a partir do grupo **Configuração de rede** no Painel de Controle do Lync Server 2013. Em Painel de Controle do Lync Server você pode visualizar, criar, modificar ou excluir políticas de local. Para detalhes sobre criar ou modificar políticas de local, consulte [Criar ou modificar uma política de local](lync-server-2013-creating-or-modifying-a-location-policy.md).

## Para visualizar informações sobre uma política de local

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração de rede** e clique em **Política de local**.

4.  Na página **Política de local**, selecione a política de local que você quer modificar.

5.  No menu **Editar**, clique em **Mostrar detalhes**.
    
    > [!NOTE]  
    > Você pode visulizar informações apenas de uma política de local por vez.

Uma política única, chamada de Global, existe por padrão e não pode ser excluída ou renomeada. Porém, você pode modificar a política Global. Essa política será aplicada a todos os usuários e contatos, a não ser que você crie políticas de sites ou políticas por usuário. As políticas por usuário devem ser aplicadas a usuários específicos.

## Consulte Também

#### Tarefas

[Criar ou modificar uma política de local](lync-server-2013-creating-or-modifying-a-location-policy.md)  
[Criar políticas de localização no Lync Server 2013](lync-server-2013-create-location-policies.md)  
[Criar ou modificar um site da rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md)  

#### Outros Recursos

[New-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsLocationPolicy)  
[Set-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsLocationPolicy)  
[Remove-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsLocationPolicy)  
[Get-CsLocationPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsLocationPolicy)

