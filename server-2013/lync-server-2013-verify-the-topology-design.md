---
title: 'Lync Server 2013: Verificar o design de topologia'
TOCTitle: Verificar o design de topologia
ms:assetid: c1b61814-239e-4101-aab0-de3db1d8793c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412951(v=OCS.15)
ms:contentKeyID: 49308010
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar o design de topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-01-02_

O Construtor de Topologias verifica automaticamente a topologia. Qualquer erro na topologia é identificado como um erro de validação, indicado pelo ícone de erro de validação ao lado da função de servidor. É importante também verificar se a topologia representa de forma correta a topologia da sua implantação.

## Para verificar a topologia antes de publicação

1.  Verifique se todas as URLs simples estão configuradas corretamente.

2.  Confirme se o servidor baseado em SQL Server está online e disponível para o computador no qual o Construtor de Topologias está instalado, incluindo quaisquer regras de firewall necessárias.

3.  Confirme se o compartilhamento de arquivos está disponível e tem as permissões adequadas definidas.

4.  Confirme se as funções de servidor corretas que atendem aos requisitos de implantação estão definidas na topologia.

5.  Verifique se existem servidores no Serviços de Domínio Active Directory. Isso acontecerá automaticamente se você tiver ingressado os servidores no domínio.

Após a verificação da topologia e se não houver erros de validação, você deverá estar pronto para publicar a topologia. Se houver erros de validação, será necessário corrigi-los antes de publicar a topologia. Para obter detalhes sobre como publicar sua topologia, consulte [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md).

