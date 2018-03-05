---

copyright:
  years: 2017
lastupdated: "2017-11-02"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Perguntas mais frequentes

Esta seção contém respostas para algumas perguntas mais frequentes sobre o IBM Cloud Load Balancer Service.

## Quantas opções de balanceamento de carga estão disponíveis no {{site.data.keyword.BluSoftlayer_notm}}?

Para uma comparação detalhada de ofertas IBM Load Balancer, consulte [Explorar balanceadores de carga](https://dev-console.bluemix.net/docs/infrastructure/loadbalancer-service/explore-load-balancers.html#explore-load-balancers).

## Posso usar um nome DNS diferente para meu balanceador de carga?

Embora o nome DNS designado automaticamente para o balanceador de carga não seja customizável, é possível incluir um registro CNAME (Nome Canônico) que aponta seu nome DNS preferencial para o nome DNS do balanceador de carga designado automaticamente. Por exemplo, seu número da conta é 123456, seu balanceador de carga é implementado no data center "dal09" e seu nome é "myapp", o nome DNS do balanceador de carga designado automaticamente é "myapp-123456-dal09.lb.bluemix.net". Seu nome DNS preferencial é "www.myapp.com". É possível incluir um registro CNAME (por meio do provedor de DNS que você usa para gerenciar myapp.com) apontando "www.myapp.com" para o nome DNS do balanceador de carga "myapp-12345-dal09.lb.bluemix.net".

## Qual é o número máximo de portas virtuais que podem ser definidas com o meu serviço de balanceador de carga?

Ao tentar criar um novo serviço de balanceador de carga, será possível definir até duas portas virtuais. É possível definir portas virtuais adicionais após a criação do serviço. O número máximo de portas virtuais permitidas é 10. 

## Qual é o número máximo de instâncias de cálculo que podem ser associadas ao balanceador de carga?

50.

## Posso criar um balanceador de carga privado somente interno que possa ser acessado apenas por clientes internos?  

Não no momento. O serviço hospedado no balanceador de carga do IBM Cloud receberá um nome completo do domínio acessível por meio da Internet pública. 

## Quais são as configurações padrão e os valores permitidos para os vários parâmetros de verificação de funcionamento?

As configurações padrão e os valores permitidos são listados abaixo:

* **Intervalo de verificação de funcionamento:** o padrão é 5 segundos, o intervalo é de 2 a 60 segundos
* **Tempo limite de resposta de verificação de funcionamento:** o padrão é 2 segundos, o intervalo é de 1 a 59 segundos
* **Máximo de novas tentativas:** o padrão são 2 novas tentativas, o intervalo é de 1 a 10 novas tentativas

**Nota:** o valor do tempo limite de resposta de verificação de funcionamento deve sempre ser menor que o valor do intervalo de verificação de funcionamento. 

## Posso usar instâncias de cálculo que residam em data centers remotos com esse serviço? 

Recomenda-se que o serviço de balanceador de carga e as instâncias de cálculo residam localmente no mesmo data center. A interface gráfica (GUI) do serviço de balanceador de carga não mostrará as instâncias de cálculo de outros data centers remotos. No entanto, a GUI incluirá instâncias de cálculo de outros data centers na mesma cidade (por exemplo, data centers cujos nomes compartilham as primeiras três letras, como DALxx). Todavia, é possível usar a interface de API para incluir instâncias de cálculo de qualquer data center remoto. 

## Qual versão do TLS é suportada com transferência de SSL? Quais cifras são suportadas?

O Cloud Load Balancer Service suporta o TLS 1.2 com finalização de SSL. 

A lista a seguir detalha as cifras suportadas (listadas em ordem de precedência):  

* ECDHE-RSA-AES256-GCM-SHA384 
* ECDHE-RSA-AES256-SHA384 
* DHE-RSA-AES256-GCM-SHA384 
* DHE-RSA-AES256-SHA256 
* AES256-GCM-SHA384 
* AES256-SHA256 
* ECDHE-RSA-AES128-GCM-SHA256 
* ECDHE-RSA-AES128-SHA256 
* DHE-RSA-AES128-GCM-SHA256 
* DHE-RSA-AES128-SHA256 
* AES128-GCM-SHA256 
* AES128-SHA256 

## Posso customizar minha lista de cifras SSL?

Não no momento.

## Qual é o número máximo de instâncias do serviço Load Balancer que posso criar dentro de minha conta? 

Atualmente, é possível criar até 20 instâncias de serviço. Se precisar de mais instâncias, entre em contato com o Suporte IBM. 

## O Load Balancer as a Service pode ser usado com o VMWare? 

Os endereços privados móveis do SoftLayer designados pelas máquinas virtuais VMware podem ser especificados como servidores de backend para o balanceador de carga. Esse recurso está disponível atualmente apenas por meio da API, não da UI da Web (GUI). Os IPs privados móveis incluídos por meio da API aparecerão como "Desconhecido" na GUI, pois eles não são designados pelo SoftLayer. Observe que esse tipo de configuração pode ser usado com outros hypervisors, como Xen e KVM também.

Os endereços não SoftLayer designados pelas máquinas virtuais VMware (como com redes VMware NSX) não podem ser incluídos diretamente como servidores de
backend no balanceador de carga. No entanto, dependendo de sua configuração, pode ser possível configurar um intermediário, tal como um gateway NSX, que tenha um endereço privado do SoftLayer como o servidor de backend para o balanceador de carga (com os servidores reais sendo VMs conectadas às redes gerenciadas pelo VMware NSX).

## Se eu optar por usar uma VLAN pública sob minha conta para implementar meu balanceador de carga e tiver um firewall implementado em minha VLAN pública, quais configurações serão necessárias em meu firewall para trabalhar com meu serviço de balanceador de carga?

A porta TCP 56501 é usada para gerenciamento. Assegure-se de que o tráfego para essa porta, bem como para as portas de seu aplicativo, não seja bloqueado por seu firewall, caso contrário, o fornecimento do balanceador de carga falhará.

