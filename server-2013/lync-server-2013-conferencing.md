---
title: 'Lync Server 2013: Conferência'
TOCTitle: Conferência
ms:assetid: 6129b7e0-9abd-488e-a54e-86094eb9df7a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg417161(v=OCS.15)
ms:contentKeyID: 49306878
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conferência no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-11_

Com a conferência unificada no Lync Server 2013, os usuários podem colaborar, compartilhar informações e coordenar esforços em tempo real. Todos os seus usuários podem usar a gama completa de ferramentas de reunião, reuniões agendadas e colaboração espontânea. Os recursos de conferência de voz e vídeo podem ser usados de qualquer local com uma conexão com a Internet, e os usuários que estiverem longe de um computador podem participar de conferências de áudio por um telefone PSTN (rede telefônica pública comutada).

As ferramentas de reunião integradas ao Outlook permitem que os organizadores agendem uma reunião ou iniciem uma conferência improvisada com um único clique e também facilita muito o ingresso dos participantes. Um cliente Web amplia os recursos de conferência avançados para participantes que não executam a versão de área de trabalho do Lync.

## Conferência de áudio e vídeo

O Lync Server fornece uma experiência de usuário conhecida aos usuários dos serviços de ponte de áudio tradicionais, incluindo os serviços de discagem PSTN com comandos de controle de chamada de discagem por tom. Ao mesmo tempo, ele incorpora avançados recursos de agendamento, ingresso e gerenciamento disponíveis apenas em uma plataforma integrada de comunicações unificadas.

Com um único clique, os usuários podem agendar uma reunião do Outlook. Os detalhes, como horário, local e participantes, seguem o modelo conhecido do Outlook. Além disso, as informações específicas da chamada em conferência, como número de discagem, IDs de reunião e lembretes de PIN (número de identificação pessoal), são preenchidas automaticamente.

Para ajudar a garantir que somente pessoas autorizadas participem de uma chamada, o Lync Server fornece vários níveis de autenticação para os participantes. Os usuários que ingressam usando o Lync já são autenticados pelos Serviços de Domínio Active Directory e não precisam inserir um PIN, uma senha ou uma ID de reunião.

O Lync simplifica a experiência do usuário de videoconferência, incorporando vídeo ao cliente unificado para que o agendamento de uma reunião com vídeo ou a transição espontânea para vídeo seja direta e fácil.

O Lync Server facilita a adição de vídeo a uma chamada telefônica padrão com apenas um clique. Quando há vários participantes em uma conferência ou chamada de vídeo, cada usuário pode ver o vídeo de até cinco outros usuários simultaneamente, ou o apresentador pode escolher somente uma fonte de vídeo para ser visualizada por todos.

Vídeo em alta definição (resolução 1270 x 720; taxa de proporção 16:9) e vídeo VGA (resolução 640 x 480; taxa de proporção 4:3) têm suporte para chamadas ponto a ponto entre usuários que executam o Lync em computadores de alta tecnologia. A resolução visualizada por cada participante de uma mesma conversa pode variar dependendo dos recursos de vídeo do hardware de cada usuário.

Os administradores de TI podem definir políticas para restringir ou desabilitar o vídeo em alta definição ou VGA nos clientes, dependendo da capacidade do computador, da largura de banda e da presença de uma câmera capaz de fornecer a resolução necessária. Essas políticas são aplicadas por meio do provisionamento em banda.

## Webconferência

O Lync Server integra recursos de compartilhamento de conferência, como área de trabalho, aplicativos, anexos, quadro de comunicações, votações e PowerPoint, ao cliente simplificado do Lync. Junto com a conferência de áudio e vídeo, o resultado é uma sessão colaborativa, altamente envolvente e fácil de manipular.

Para melhorar a experiência geral de usuários que conduzem ou visualizam apresentações do PowerPoint, o Lync Server 2013 emprega o Office Web Apps para manipular as apresentações do PowerPoint. Os usuários podem compartilhar uma imagem ou copiar e colar texto usando um quadro de comunicações na reunião do Lync. Os apresentadores podem conduzir votações na reunião do Lync para solicitar a opinião dos participantes.

O compartilhamento de área de trabalho permite que os apresentadores transmitam qualquer elemento visual, aplicativo, página da Web, documento, software ou parte de suas áreas de trabalho para participantes remotos em tempo real, diretamente do Lync. Os participantes podem acompanhar os movimentos do mouse e a digitação do teclado. Os apresentadores podem optar por compartilhar a tela inteira ou apenas uma parte. Ao compartilhar suas áreas de trabalho, os apresentadores podem envolver os participantes com demonstrações interativas de produtos ou software de qualquer local.

O compartilhamento de aplicativos permite que os apresentadores compartilhem o controle de software em suas áreas de trabalho sem perder os comentários de participantes ou perguntas de texto. Os apresentadores também podem delegar o controle do aplicativo para os participantes da reunião.

## Conferência discada

Para usuários que não estão usando um PC, há vários métodos para ingressar em uma chamada em conferência do Lync Server. Um usuário PSTN pode discar um número de acesso, acessar a ponte de reunião e digitar a ID da reunião. Para obter reuniões mais seguras, também é possível solicitar que o usuário insira seu PIN para ser autenticado no Active Directory. O Lync Server também oferece suporte a dispositivos do Lync Phone Edition, que são dispositivos autônomos de telefonia IP fornecidos por parceiros da Microsoft.

