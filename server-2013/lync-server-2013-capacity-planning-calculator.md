---
title: Usando a Calculadora de planejamento de capacidade do Lync Server 2013
TOCTitle: Usando a Calculadora de planejamento de capacidade do Lync Server 2013
ms:assetid: e86c1f05-1393-408a-9549-6001572ec50d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362852(v=OCS.15)
ms:contentKeyID: 56270483
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando a Calculadora de planejamento de capacidade do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A calculadora de planejamento de capacidade do Microsoft® Lync™ Server 2013 está disponível para o download em <http://www.microsoft.com/en-us/download/details.aspx?id=36828>. É projetada para ajudar a determinar as exigências do servidor com base nos números de usuários e modalidades de comunicação permitidas em sua organização. Você digita o perfil de sua organização e a calculadora fornece recomendações que ajudam a planejar sua topologia.

As recomendações criadas pela calculadora são para o planejamento apenas. Uma simulação de carga real é requerida para assegurar que o Lync Server 2013 seja provisionado adequadamente. Para realizar um teste de ênfase com uma carga simulada, use o [Lync Server 2013 Stress and Performance Tool](http://go.microsoft.com/fwlink/?linkid=282724).

Após ter determinado o perfil do usuário e as modalidades que você deseja permitir para seus usuários, será hora de usar a calculadora para planejar o número de servidores, memória e largura de banda necessários. Esta versão de calculadora não fornece orientação para as exigências de E/S do disco.

Essa calculadora completa o [Microsoft Lync Server](http://go.microsoft.com/fwlink/?linkid=282725) e o [Microsoft Lync Server](lync-server-2013-planning.md). Use a calculadora após ter revisto o guia e criado uma topologia recomendada usando a Ferramenta de planejamento.

Você poderá aproveitar grande parte da calculadora se tiver informações precisas e detalhadas sobre seu perfil do usuário específico. Por exemplo, a porcentagem dos usuários de voz, chamadas médias por usuário e por hora, duração da chamada e porcentagem dos usuários simultâneos em conferências podem fazer uma diferença enorme nas exigências do servidor. A precisão das recomendações criadas pela calculadora depende da precisão das informações fornecidas.

## Usando a capacidade da calculadora

A calculadora é uma planilha do Microsoft Excel®. As células laranjas são para sua entrada. Os valores padrão são fornecidos (80.000 usuários em um pool com 12 servidores de front-ent), mas você pode mudá-los segundo as necessidades de sua organização.

O modelo de uso contém as seguintes seções. Para calcular as exigências de sua capacidade, digite os dados como descrito:

**Mensagem instantânea e presença**

  - Em 'Número de usuários', digite o número de usuários que estarão conectados simultaneamente. Esse número normalmente é 80% do número total de usuários provisionados. Na maioria das situações, 100% de seus usuários simultâneos estarão ativados para MI e a presença, O padrão é 80.000.

  - 'Número médio de contatos', na lista 'Contatos' indica o número de contatos que estamos usando para validar as exigências de seu sistema. Esse número não muda.

**Enterprise Voice**

  - Em 'Usuários permitidos para o Enterprise Voice', digite a porcentagem de seus usuários que têm permissão para o Enterprise Voice. O padrão é 60%.

  - Em 'Número médio de chamadas por usuário e por hora (pico)', digite o número de chamadas por hora que você espera que o usuário médio participe durante as horas de pico da carga. O padrão é 4.

  - Em 'Porcentagem de chamadas que usam o desvio de mídia', digite a porcentagem de chamadas feitas por seus usuários que desviarão o Servidor de Mediação. O padrão é 65%.

  - Em 'Porcentagem de usuários por voz envolvidos nas chamadas UC-PSTN', digite a porcentagem de chamadas de sua organização que são chamadas telefônicas UC-PSTN. O padrão é 60%

  - Em 'Porcentagem de usuários de voz envolvidos nas chamadas UC-UC', mostra a porcentagem de usuários que são ativados para o Enterprise Voice e que serão ativados apenas para as chamadas UC-UC. Esse número é calculado com base no que você digita para a 'Porcentagem de usuários de voz ativados para as chamadas UC-PSTN.

**Conferência**

  - Em 'Porcentagem de usuários em conferências simultâneas', digite a porcentagem de usuários que estarão participando simultaneamente em conferências. O padrão é 5%.

  - Em 'Porcentagem de conferências com MI de grupo apenas (sem voz)', digite a porcentagem de conferências cujas conferências envolverão apenas a mensagem instantânea; ou seja, isso não inclui um componente de áudio. O padrão é 10%

  - Em 'Porcentagem de usuários usando conferência discada', digite a porcentagem de participantes simultâneos nas conferências que usarão a conferência discada. O padrão é 15%.

  - Em 'Porcentagem de conferências usando voz', digite a porcentagem de conferências que incluirão um componente de áudio.
    
      - Se 20% das conferências de voz incluírem também um vídeo normal, marque a caixa de seleção Incluir vídeo (sem Multi View).
    
      - Se 20% de suas conferências incluírem o vídeo Multi View, marque a caixa de seleção Incluir Multi View.
    
      - Se 50% de suas conferências de voz incluírem o compartilhamento de aplicativos, marque a caixa de seleção Incluir compartilhamento de aplicativos.
    
      - Se 20% de suas conferências de voz incluírem uploads de dados, como as apresentações do Microsoft PowerPoint®, marque a caixa de seleção Incluir conferência da Web.

**Mobilidade**

  - Em 'Porcentagem de usuários ativados para Mobilidade', digite a porcentagem de seus usuários que estarão ativados para conectar o Lync Server usando dispositivos móveis. O padrão é 40%.

Quando você tiver digitado todas as informações necessárias, a calculadora de capacidade estimará as exigências. As células amarelas mostram os valores calculados para as exigências da CPU, memória e largura de banda com base nos testes realizados nos laboratórios de desempenho do Lync Server 2013. Os números são fornecidos como uma diretriz e nem toda variação é testada e validada. Os seguintes valores são calculados:

  - CPU de front-end: a porcentagem de uso da CPU se a carga inteira estava sendo lidada por um servidor de front-end com as mesmas especificações do servidor que foi usado no teste da Microsoft.

  - Rede em Mbps: as exigências da largura de banda em megabits por segundo (Mbps) para a carga de trabalho correspondente.

  - Memória em GB: a memória requerida em gigabytes (GB) para a carga de trabalho correspodente.

As células verdes mostram as recomendações para o modelo de uso inserido.

  - Servidores de front-end totais: o número de servidores físicos requeridos é baseado nos servidores dedicados que executam o Lync Server 2013 com um processador dual, núcleo hex, com 2.260 megaciclos.

  - Note que é recomendado ativar o hyperthreading e foi comprovado que melhora o desempenho para os servidores que suportam áudio/vídeo.

  - Servidores de borda: o número de Servidores de borda requeridos, com base em 30% de todos os usuários simultâneos comunicando-se por meio dos Servidores de borda. Essa porcentagem não pode ser alterada na calculadora.

  - Armazenamento de serviços de Arquivamento/Registro de detalhes da camada/Qualidade da experiência: o número de armazenamentos requeridos para os recursos de Arquivamento ou Monitoramento, se estiverem ativados em sua organização.

  - Servidor requerido do banco de dados de back-end (pools requeridos): o número de servidores do banco de dados de back-end requeridos para suportar a carga de trabalho selecionada.

E mais, na linha próxima de 'Servidores de front-end totais, mais informações são fornecidas sobre a carga em seus servidores e rede para todas as cargas de trabalho planejadas e combinadas.

  - Carga média da CPU: o uso médio da CPU por servidor de front-end server.

  - Rede em Mbps: a alocação da largura de banda requerida para suportar o modelo de uso fornecido.

  - Memória em GB: a memória, em gigabytes, requerida para cada servidor de front-end server.

## Adjustando para seus processadores

Todos os valores de uso da CPU supõem que cada servidor tem um processador dual, núcleo hex com 2.26 GHz, pelo menos 32 GB de memória, 8 ou mais drives de disco rídigo com 10.000 RPM e pelo menos 72 GB de espaço em disco livre.

Se seus servidores tiverem processadores diferentes, você poderá ajustar os valores para corresponderem ao seu hardware.

