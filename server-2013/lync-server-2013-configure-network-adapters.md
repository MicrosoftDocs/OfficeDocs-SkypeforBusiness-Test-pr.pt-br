---
title: 'Lync Server 2013: Configurar adaptadores de rede'
TOCTitle: Configurar adaptadores de rede
ms:assetid: 6519ed80-020f-47a3-851c-03dea5eac5d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429707(v=OCS.15)
ms:contentKeyID: 49306929
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar adaptadores de rede no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

Você deve atribuir um ou mais endereços IP ao adaptador de rede externo e pelo menos um endereço IP ao adaptador de rede interno.

Nos seguintes procedimentos, o servidor que executa o Forefront Threat Management Gateway (TMG) 2010 ou o Roteamento de Solicitação do Aplicativo do Servidor de Informações da Internet tem dois adaptadores de rede:

  - Um adaptador de rede público ou externo para clientes que tentam se conectar ao seu site (geralmente pela Internet).

  - Uma interface de rede privada ou interna para servidores internos que executam o Lync Server e hospedam os serviços Web.

> [!IMPORTANT]  
> De maneira semelhante aos Servidores de Borda, você define o gateway padrão somente no adaptador de rede externo. O gateway padrão será o endereço IP do roteador ou firewall externo que direciona o tráfego para a Internet. Para tráfego encaminhado do proxy reverso para o adaptador de rede interno, é necessário usar rotas estáticas persistentes (como o comando rotear no Windows Server) para todas as sub-redes que contêm servidores referenciados pelas regras de publicação na Web. A definição de uma rota persistente não faz com que o computador se torne um roteador. Se o encaminhamento de IP não estiver habilitado, o computador atuará apenas para direcionar tráfegos específicos destinados a outra rede para a interface apropriada. Em essência, isso significa configurar dois gateways - um como o padrão apontando para as redes externas e outro para o tráfego, destinado à interface interna e a um roteador ou outra rede.<br />No entanto, a criação de rotas persistentes para todas as sub-redes pode não ser necessária se os roteadores de sua rede estiverem configurados para abreviar as rotas. Crie uma rota persistente para a rede na qual o roteador está definido e use-o como gateway padrão. Se você não tiver certeza sobre como sua rede está configurada e precisar de orientação sobre quais rotas persistentes precisam ser criadas, consulte os engenheiros de rede da sua empresa.<br />O proxy reverso deve ser capaz de resolver os registros de host DNS (A) do Diretor ou Servidor Front-End interno e os FQDNs do pool de próximo salto usados nas regras de publicação na Web. Assim como nos Servidores de Borda, por motivos de segurança, recomendamos que você não configure um proxy reverso para usar um servidor DNS localizado na rede interna. Isso significa que você precisa de servidores DNS no perímetro ou precisa de entradas do arquivo HOSTS no proxy reverso que resolve cada um desses FQDNs como o endereço IP interno dos servidores.

## Para configurar as placas adaptadoras de rede no computador do proxy reverso

1.  No servidor do Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 ou Windows Server 2012 R2 sendo executado como o proxy reverso, abra **Alterar as configurações do adaptador** clicando em **Iniciar** , apontando para **Painel de Controle** , clicando em **Central de Rede e Compartilhamento** e em **Alterar as configurações do adaptador** .

2.  Clique com o botão direito do mouse na conexão de rede externa a ser usada para a interface externa e, em seguida, clique em **Propriedades** .

3.  Na página **Propriedades** , clique na guia **Rede** , clique em **Protocolo TCP/IPv4** na lista **Esta conexão utiliza os seguintes itens** e clique em **Propriedades** .

4.  Na página **Propriedades de Protocolo TCP/IP** , configure os endereços IP apropriados da sub-rede à qual o adaptador de rede está conectado.
    
    > [!NOTE]  
    > Se o proxy reverso já estiver sendo usado por outros aplicativos que usam HTTPS/TCP/443, como para a publicação do Outlook Web Access, você precisará adicionar outro endereço IP para que possa publicar os Serviços Web do Lync Server 2013 em HTTPS/TCP/443 sem interferir nas regras e nos ouvintes da Web existentes ou precisará substituir o certificado existente por um que adicione os novos nomes FQDN externos ao nome alternativo da entidade.

5.  Clique em **OK** e em **OK** novamente.

6.  Em **Conexões de Rede** , clique com o botão direito do mouse na conexão de rede interna a ser usada para a interface interna e clique em **Propriedades** .

7.  Repita as etapas 3 a 5 para configurar a conexão de rede interna.

