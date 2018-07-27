---
title: 'Lync Server 2013: Configurar interfaces de rede para Servidores de Borda'
TOCTitle: Configurar interfaces de rede para Servidores de Borda
ms:assetid: b0aecdf6-4ae2-46f6-b9b6-948bfc3df11e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412847(v=OCS.15)
ms:contentKeyID: 49307811
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar interfaces de rede para Servidores de Borda no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Cada Servidor de Borda é um computador multihomed com interfaces externas e internas. As configurações de DNS do adaptador dependem da existência de servidores DNS na rede de perímetro. Se houver servidores DNS no perímetro, eles deverão ter uma zona contendo um ou mais registros A DNS para o servidor ou pool de próximo salto (ou seja, um Diretor ou um pool de Front-Ends designado) e, para consultas externas, eles farão referência a pesquisas de nome para outros servidores DNS públicos. Se não houver servidores DNS no perímetro, os Servidores de Borda usarão servidores DNS externos para resolver pesquisas de nome da Internet, e cada Servidor de Borda usará um HOST para resolver os nomes de servidor de próximo salto para endereços IP.

> [!security]  
> Por motivos de segurança, recomendamos que seus Servidores de Borda não acessem um servidor DNS localizado na rede interna.

## Para configurar interfaces com os servidores DNS na rede de perímetro

1.  Instale dois adaptadores de rede para cada Servidor de Borda, um para a interface interna e outro para a interface externa.
    
    > [!IMPORTANT]  
    > As sub-redes interna e externa não devem ser roteáveis ente si.

2.  Na interface externa, configure três endereços IP estáticos na sub-rede da rede de perímetro externa (também conhecida como DMZ, zona desmilitarizada, e sub-rede filtrada), e aponte o gateway padrão à interface interna do firewall externo. Defina as configurações DNS do adaptador para apontar para um par de servidores DNS de perímetro.
    
    > [!NOTE]  
    > É possível usar um endereço IP para essa interface, mas para fazer isso você precisa alterar as atribuições de porta para valores não padrão. Determine isso ao criar a topologia no Construtor de Topologias.

3.  Na interface interna, configure um endereço IP estático na sub-rede da rede de perímetro e não defina o gateway padrão. Defina as configurações DNS do adaptador a fim de apontar para pelo menos um servidor DNS, preferencialmente um par de servidores DNS de perímetro.

4.  Crie rotas estáticas persistentes na interface interna para todas as rotas internas nas quais os clientes, Lync Server 2013, e os servidores de UM (Mensagem unificada) do Exchange residem.

## Para configurar interfaces sem servidores DNS na rede de perímetro

1.  Instale dois adaptadores de rede para cada Servidor de Borda, um para a interface interna e outro para a interface externa.
    
    > [!IMPORTANT]  
    > As sub-redes interna e externa não devem ser roteáveis ente si.

2.  Na interface externa, configure três endereços IP estáticos na sub-rede da rede de perímetro externa. Também é possível configurar o gateway padrão na interface externa. Por exemplo, defina o roteador da Internet ou o firewall externo como o gateway padrão. Defina as configurações de DNS a fim de apontar para um servidor DNS, preferencialmente para um par de servidores DNS externos.
    
    > [!NOTE]  
    > É possível, mas não recomendado, usar um endereço IP para a interface externa. Para que isso funcione, você precisa alterar as atribuições de porta para valores não padrão e para longe da porta padrão 443 que normalmente é “amigável com firewall” para a comunicações do cliente. É possível determinar a configuração do endereço IP e as configurações de porta ao criar a topologia no Construtor de Topologias.

3.  Na interface interna, configure um endereço IP estático na sub-rede da rede de perímetro e não defina o gateway padrão. Deixe as configurações DNS do adaptador vazias.

4.  Crie rotas estáticas persistentes na interface interna de todas as redes internas na qual os clientes ou servidores do Lync executando o Lync Server 2013 residem.

5.  Edite o arquivo HOST em cada Servidor de Borda para conter um registro para o servidor de próximo salto ou IP virtual (VIP) (o registro será o Diretor, o servidor Standard Edition ou um pool Front-End configurado como o endereço de próximo salto do Servidor de Borda no Construtor de Topologias). Se você estiver usando o balanceamento de carga DNS, inclua uma linha para cada membro do pool de próximo salto.

