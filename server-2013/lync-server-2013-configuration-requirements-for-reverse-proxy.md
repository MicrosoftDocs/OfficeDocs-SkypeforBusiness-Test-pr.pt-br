---
title: Requisitos de configuração do proxy reverso no Lync Server 2013
TOCTitle: Requisitos de configuração do proxy reverso no Lync Server 2013
ms:assetid: c37d688a-28e4-4822-80cc-6add59c71052
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945651(v=OCS.15)
ms:contentKeyID: 52057721
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de configuração do proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-05_

O Lync Server 2013 impõe algumas exigências para comunicações a partir do cliente externo que são então passadas aos serviços Web externos hospedados no Diretor, Pool de diretores, Servidor Front-End ou Pool de Front-Ends. O proxy reverso também é responsável por publicar o Servidor Office Web Apps, caso você esteja oferecendo a opção de conferência a seus usuários.

> [!NOTE]  
> O Lync Server 2013 não especifica um proxy reverso em particular que você precise utilizar. O Lync Server 2013 somente define requisitos operacionais que o proxy reverso deve ser capaz de satisfazer. Tipicamente, o proxy reverso que você já tem implantado em sua infraestrutura deve ser capaz de satisfazer essas exigências.

## Requisitos de proxy reverso

As operações funcionais que o Lync Server 2013 espera que o proxy reverso realize são:

  - Usar camada de sockets de segurança (SSL) e segurança de camada de transporte (TLS) implementados com uso de certificados adquiridos a partir de uma autoridade de certificação pública para estabelecer conexão com os serviços Web externos publicados do Diretor, Pool de diretores, Servidor Front-End ou Pool de Front-Ends. O Diretor e o Servidor Front-End podem estar em um pool com carga balanceada por meio do uso de balanceadores de carga de hardware.

  - Ser capaz de publicar sites Web internos pelo uso de certificados para encriptação ou publicá-los por um meio não encriptado, se necessário.

  - Ser capaz de publicar externamente um site Web hospedado internamente, pelo uso de um nome de domínio totalmente qualificado (FQDN).

  - Ser capaz de publicar todos os conteúdos do site Web hospedado. Por padrão, você pode utilizar a diretiva **/\***, que é reconhecida pela maioria dos servidores Web como significando "Publicar todo o conteúdo presente no servidor Web." Você também pode modificar a diretiva - p. ex., **/Uwca/\***, que significa "Publicar todo o conteúdo sob o diretório virtual Ucwa."

  - Precisa ser configurável para requerer conexões de camada de sockets de segurança (SSL) e/ou segurança de camada de transporte (TLS) com clientes que requeiram conteúdo de um website publicado.

  - Precisa aceitar certificados com entradas de nomes de entidade alternativos (SAN).

  - Precisa ser capaz de permitir associação de um certificado a um ouvinte ou interface pela qual os serviços Web externos FQDN se resolverão. Configurações de ouvinte são preferíveis para interfaces. Muitos ouvintes podem ser configurados em uma única interface.

  - Precisa permitir a configuração de gerenciamento de cabeçalho do host. Com frequência, o cabeçalho do host original enviado pelo cliente que faz a requisição precisa ser passado transparentemente, em vez de ser modificado pelo proxy reverso.

  - Ponte do tráfego SSL e TLS a partir de uma porta definida externamente (por exemplo, TCP 443) para outra porta definida (por exemplo, TCP 4443). O proxy reverso pode desencriptar o pacote no recebimento e então reencriptá-lo no envio.

  - Ponte de tráfego TCP não encriptado a partir de uma porta (por exemplo, TCP 80) para outra (por exemplo, TCP 8080).

  - Permitir a configuração da autenticação de NTLM ou aceitá-la. Sem autenticação e autenticação de passagem.

