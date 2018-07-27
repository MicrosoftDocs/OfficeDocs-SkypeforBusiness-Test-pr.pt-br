---
title: 'Lync Server 2013: Editando o design'
TOCTitle: Editando o design
ms:assetid: 08f639ba-0e5f-4ae7-9191-c3d96c25b169
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558608(v=OCS.15)
ms:contentKeyID: 52057551
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Editando o design no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Após concluir as perguntas iniciais da entrevista, você poderá editar o nome de domínio totalmente qualificado (FQDN) e o endereço IP do site. Para isso, na página **Topologia Global**, clique duas vezes no site que deseja editar.

O Ferramenta de Planejamento exibe a topologia do site para o site selecionado. Na parte inferior da página do site, existem quatro guias:

![Topologia do site da ferramenta de planejamento](images/Gg558608.e6189c20-360a-42bd-ba90-11bdb5b7551b(OCS.15).jpg "Topologia do site da ferramenta de planejamento")

  - Topologia do site - A página exibida atualmente com uma visão geral visual da topologia, conforme recomendado.

  - Diagrama da rede de borda - A página do Diagrama da rede de borda é o local em que é feita a maior parte do trabalho do designer no Ferramenta de Planejamento. O diagrama exibe a configuração da rede para uma topologia recomendada do Lync Server 2013 com entradas editáveis para os endereços IP e com FQDNs para servidores, pools e balanceadores de carga de hardware e do Sistema de nomes de domínios (DNS).

  - Relatório de administração de borda - O Relatório de administração de borda contém um total de quatro relatórios:
    
    ![Página de Relatórios administrativos de borda](images/Gg558608.0019cc5e-af39-4cb9-82ce-58f6388242ff(OCS.15).jpg "Página de Relatórios administrativos de borda")  
    
      - Relatório resumido - Um relatório geral de configurações para a configuração da Rede de borda. Se você editar os valores na página **Diagrama da rede de borda** para a topologia TCP/IP e os valores do FQDN que irão ser usados na implantação atual, tais endereços e nomes serão representados aqui. De outro modo, o texto padrão aparecerá.
    
      - Relatório de certificado - O relatório de certificado listará o nome da entidade ou os nomes alternativos da entidade dos certificados que são exigidos para a topologia.
    
      - Relatório de firewall - O relatório de firewall lista as informações necessárias para configurar os firewalls de perímetro na infraestrutura. Isso inclui os endereços IP (seja de valores padrão ou editados), função do servidor, IP e porta de origem, IP e porta de destino, protocolo de transporte, protocolo de aplicativo e notas relevantes.
    
      - Relatório de DNS - O relatório de DNS lista as informações relevantes para as entradas de DNS que você deve criar. Estão incluídos o tipo de registro, o FQDN, o endereço IP e os comentários necessários para a operação apropriada.

  - Resumo do site - O resumo do site apresenta uma visão geral das seleções que foram feitas ao responder às perguntas da entrevista inicial ou ao incluir valores em **Criar Sites**. A informação de capacidade também é apresentada.
    
    > [!NOTE]  
    > As informações na página do Resumo do site são personalizadas para cada design e podem não conter todas as seções ou informações detalhadas aqui.

## Consulte Também

#### Conceitos

[Editando o diagrama de configuração de rede no Lync Server 2013](lync-server-2013-editing-the-network-configuration-diagram.md)

