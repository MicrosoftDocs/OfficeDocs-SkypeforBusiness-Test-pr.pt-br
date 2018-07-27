---
title: Visão geral do recebimento de chamadas em grupo
TOCTitle: Visão geral do recebimento de chamadas em grupo
ms:assetid: 3dc0eca8-c773-463c-96bb-9cd6afa2a840
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945623(v=OCS.15)
ms:contentKeyID: 52057586
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2013-02-12_

Atendimento de chamadas em grupo, um novo recurso nas atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013, permite que os usuários atendam chamadas em entrada destinadas a seus colegas, utilizando seus próprios telefones. Esse novo recurso aumenta a disponibilidade de linha de usuário, habilitando outros usuários a atenderem uma chamada em entrada discando um número de grupo de atendimento de chamadas. Quando o atendimento de chamadas em grupo é implantado, o número de chamadas em entrada direcionadas ao correio de voz pode ser reduzido significativamente, o que é especialmente útil para chamadas vindas de clientes localizados fora da sua organização.

O recurso de atendimento de chamadas em grupo é projetado especialmente para unidades comerciais em ambientes de escritório aberto. Chamadas em entrada não perturbam porque tocam somente no destino desejado. Outros usuários que escutam o toque, porém, mesmo assim podem atender a chamada simplesmente discando o número de grupo de atendimento de chamadas.

Em ambientes em que os usuários não estão localizados em um layout de escritório aberto ou em que os usuários que compartilham uma responsabilidade comum estão espalhados geograficamente, a chamada em equipe apresenta-se como a solução mais adequada. A diferença principal entre atendimento de chamadas em grupo e chamada em equipe é que, com atendimento de chamadas em grupo, uma chamada em entrada toca somente no destino desejado, mas qualquer um pode optar por atendê-la discando o número de grupo de atendimento de chamadas. Com chamada em equipe, a chamada toca nos telefones de todos os membros da equipe e qualquer usuário na equipe pode atender o telefone para responder à chamada. Uma diferença adicional entre atendimento de chamadas em grupo e chamada em equipe é que o atendimento de chamadas em grupo é gerenciado por um administrador, via Lync Server. Com a chamada em equipe, usuários finais gerenciam o recurso utilizando o cliente Lync. Com o atendimento de chamadas em grupo, desse modo, esse aspecto do gerenciamento de chamadas pode ser centralizado.

O atendimento de chamadas em grupo é construído no Aplicativo de Estacionamento de Chamada. Quando você implanta atendimento de chamadas em grupo, você configura a tabela de órbitas do estacionamento com intervalos separados de números de extensões que são denominados números de atendimento de chamadas em grupo. Como os números de órbita de estacionamento de chamadas, os números de grupo de atendimento de chamadas precisam ser extensões virtuais que não têm um usuário ou telefone atribuídos a elas. Cada Pool de Front-Ends em que você implanta o atendimento de chamadas em grupo pode ter um ou mais intervalos de números de atendimento de chamadas em grupo. Os intervalos de números de grupo precisam ser únicos globalmente por toda a implantação do Lync Server.

> [!NOTE]  
> Intervalos de números que são atribuídos como números de atendimento de chamadas em grupo na tabela de órbita de estacionamento de chamadas não podem ser gerenciados ou visualizados utilizando o Painel de Controle do Lync Server. O único jeito de ver todos os intervalos de números na tabela de órbita de estacionamento de chamadas é utilizar o Shell de Gerenciamento do Lync Server. De modo similar, o único modo de adicionar, modificar ou remover números de atendimento de chamadas em grupo é utilizar o Shell de Gerenciamento do Lync Server.

Após você configurar os números de grupos de atendimento de chamadas, você atribui usuários a um grupo de atendimento de chamadas. Qualquer usuário que for atribuído a um grupo de atendimento de chamadas pode ter suas chamadas atendidas por outros usuários. Quando uma chamada chega para um usuário atribuído a um grupo de atendimento de chamadas, qualquer outro usuário que perceba a chamada pode atendê-la manualmente discando o número de grupo de atendimento de chamadas. O usuário que atender a chamada não precisa ser um membro do grupo. Quando uma chamada é atendida por outro usuário, uma notificação é enviada ao número que foi chamado originalmente.

> [!NOTE]  
> Um usuário pode ser membro de somente um grupo de atendimento de chamadas.

> [!NOTE]  
> Apesar de qualquer usuário na implantação Lync Server poder responder a uma chamada para um membro de um determinado grupo de atendimento de chamadas, a pessoa respondendo a chamada precisa saber o número de grupo de atendimento de chamadas correto a discar.

Se um usuário discar um número de grupo de atendimento de chamadas para atender uma chamada quando diversos telefones no grupo estiverem tocando, o usuário atenderá a chamada que estiver tocando a mais tempo.

Configurações de toque simultâneo funcionarão para usuários habilitados para atendimento de chamadas em grupo. Ou seja, uma chamada realizada para um usuário habilitado para atendimento de chamadas em grupo tocará para todos os destinos configurados e outro usuário poderá atender a chamada. A exceção para essa regra é quando o usuário configura toque simultâneo para todos os membros da equipe.

Atendimento de chamadas em grupo não pode ser utilizado para atender aos tipos de chamadas a seguir:

  - Chamadas a uma linha privada

  - Chamadas por um contato ao qual atribuiu-se a política de privacidade Amigos e Família
    

    > [!TIP]
    > Um usuário membro de um grupo de atendimento de chamadas pode prevenir que certas chamadas sejam respondidas pelo atendimento de chamadas em grupo tornando o contato seu contato pessoal no cliente Lync. Para marcar um contato como seu contato pessoal, defina a Relação de Privacidade para o contato como Amigos e Família. Qualquer chamada em entrada de contatos com a Relação de Privacidade configurada como Amigos e Família não pode ser respondida utilizando atendimento de chamadas em grupo.



  - Porção de vídeo de chamadas de áudio/vídeo
    
    > [!NOTE]  
    > Se um usuário responde uma chamada de áudio/vídeo, ele recebe somente o áudio. Tanto a pessoa que realizou a chamada quanto a que está recebendo podem escalar a chamada para adicionar o vídeo.

  - Chamadas de toque simultâneo que são direcionada para membros da equipe de atendimento de chamadas

  - Chamadas direcionadas a um representante

  - Chamadas direcionadas a um grupo de resposta

Os tipos de usuários a seguir não podem participar de atendimento de chamadas em grupo. Ou seja, eles não podem ser incluídos em um grupo de atendimento de chamadas e não podem atender chamadas para usuários que são habilitados para utilização desse recurso.

  - Usuários que estão hospedados em uma implantação híbrida

  - Uuários que não estão hospedados em um pool Lync Server 2013 com atualizações cumulativas de fevereiro de 2013 para Lync Server 2013 em uma implantação local

Se ninguém responder uma chamada destinada a um membro de um grupo de atendimento de chamadas, ela é direcionada conforme especificado nas configurações do cliente. Ou seja, a chamada vai para correio de voz e ou é direcionada para um outro destino, conforme estiver especificado nas configurações do cliente.

