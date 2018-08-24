---
title: 'Lync Server 2013: Segurança de dados de emparelhamento do pool Front End'
TOCTitle: Segurança de dados de emparelhamento do pool Front End
ms:assetid: edb852b8-ea86-4948-b756-60fe6ee876d2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721930(v=OCS.15)
ms:contentKeyID: 49886468
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Segurança de dados de emparelhamento do pool Front End no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Serviço de Backup é um mecanismo de replicação de dados introduzido no Lync Server 2013 que transfere os dados dos usuários e o conteúdo das conferências entre dois Pools de Front-Ends pareados de forma contínua entre dois data centers para fins de recuperação de desastres. Os dados dos usuários contêm as SIP URIs dos usuários, bem como listas de contatos e configurações. O conteúdo das conferências inclui uploads de Microsoft PowerPoint 2010, bem como os quadros interativos usados nas conferências. Do pool de origem, os dados dos usuários e o conteúdo das conferências são exportados do armazenamento local, compactados, transferidos para o Pool de destino, onde são descompactados e importados ao armazenamento local. O Serviço de Backup pressupõe que o link de comunicação entre os dois data centers está dentro da rede da empresa, protegida da Internet. Ele não criptografa os dados transferidos entre os dois data centers, nem está encapsulado de forma nativa em um protocolo protegido, como HTTPS. Portanto, o ataque de "intrusos" de pessoal interno na rede da empresa é possível.

## Avaliação dos riscos à segurança

Qualquer empresa que implanta o Lync Server 2013 em vários data centers e usa o recurso de recuperação de desastres deve garantir que o tráfico entre os data centers esteja protegido pela Intranet da empresa. As empresas que se preocupam com proteção interna contra ataques devem proteger os links de comunicação entre os data centers.

A presunção de que os data centers de uma empresa estão protegidos atrás da Intranet da empresa é padrão. Há muitos outros tipos de dados empresariais sensíveis transferidos entre esses data centers. A infraestrutura de TI da empresa corre grande perigo se esses links entre os data centers não forem protegidos.

Embora exista o risco de ataques de "intrusos" na rede da empresa, ele é relativamente limitado em comparação a expor o tráfego à Internet. Especificamente, os dados dos usuários expostos pelo Serviço de Backup (como SIP URIs) estão geralmente disponíveis para todos os funcionários da empresa através de outros meios como o Catálogo de Endereços Global do Exchange ou outro software de diretório. Portanto, o foco deve estar em proteger a WAN entre os dois data centers quando o Serviço de Backup é usado para copiar dados entre dois Pools emparelhados.

## Mitigação dos riscos à segurança

Há diferentes formas de se melhorar a segurança de tráfego do Serviço de Backup, que variam de restringir o acesso aos data centers a proteger o transporte da WAN entre os dois data centers. Na maioria dos casos, as empresas que implantam o Lync Server 2013 já devem ter a estrutura de segurança necessária. Para as empresas que buscam orientação, a Microsoft fornece a solução como exemplo de como construir uma infraestrutura de TI segura. Entretanto, isso não quer dizer que esta é a única solução, nem que é a melhor solução para o Lync Server. Recomendamos aos clientes empresariais escolher a solução que melhor se adéqua a suas necessidades específicas, com base em suas infraestruturas e requisitos de TI. O exemplo da solução da Microsoft emprega IPSec e Política de Grupo para isolamento do servidor e do domínio. Para obter mais informações, consulte [http://go.microsoft.com/fwlink/p/?LinkId=268544](http://go.microsoft.com/fwlink/p/?linkid=268544). Caso tenha dúvidas ou comentários, entre em contato através de secwish@microsoft.com.

Outra solução possível é usar o IPSec apenas para ajudar a proteger os dados enviados pelo próprio Serviço de Backup. Se você escolher este método, deverá configurar as regras do IPSec para o protocolo SMB nos seguintes servidores, quando Pool A e Pool B estiverem emparelhados Pools de Front-Ends.

  - O Serviço SMB (TCP/445) de cada Servidor Front-End no Pool A para o Repositório de Arquivos usado pelo Pool B.

  - O Serviço SMB (TCP/445) de cada Servidor Front-End no Pool B para o Repositório de Arquivos usado pelo Pool A.


> [!WARNING]  
> IPsec não deve ser usado para substituir a segurança a nível de aplicativos, como SSL/TLS. Uma vantagem de usar o IPsec é que ele pode fornecer segurança ao tráfego da rede dos aplicativos existentes sem ter que alterá-los. As empresas que desejam proteger o transporte entre os dois data centers devem consultar seus respectivos fornecedores de hardware de rede em relação à maneira de configurar conexões WAN seguras usando o equipamento do fornecedor.


