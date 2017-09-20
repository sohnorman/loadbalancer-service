---

copyright:
  years: 2017
lastupdated: "2017-08-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Perguntas mais frequentes

Esta seção contém respostas para algumas perguntas mais frequentes sobre o serviço IBM Bluemix Load Balancer.

## Qual é o número máximo de portas virtuais que podem ser definidas com o meu serviço de balanceador de carga?

Ao tentar criar um novo serviço de balanceador de carga, será possível definir até duas portas virtuais. É possível definir portas virtuais adicionais após a criação do serviço. O número máximo de portas virtuais permitidas é 10. 

## Qual é o número máximo de instâncias de cálculo que podem ser associadas ao balanceador de carga?

50.

## Posso criar um balanceador de carga privado somente interno que possa ser acessado apenas por clientes internos?  

Não no momento. Será designado um nome completo de domínio ao serviço hospedado no balanceador de carga do IBM Bluemix, acessível na Internet pública. 

## Quais são as configurações padrão e os valores permitidos para os vários parâmetros de verificação de funcionamento?

As configurações padrão e os valores permitidos são listados abaixo:

* **Intervalo de verificação de funcionamento:** o padrão é 5 segundos, o intervalo é de 2 a 60 segundos
* **Tempo limite de resposta de verificação de funcionamento:** o padrão é 2 segundos, o intervalo é de 1 a 59 segundos
* **Máximo de novas tentativas:** o padrão são 2 novas tentativas, o intervalo é de 1 a 10 novas tentativas

**Nota:** o valor do tempo limite de resposta de verificação de funcionamento deve sempre ser menor que o valor do intervalo de verificação de funcionamento. 

## Posso usar instâncias de cálculo que residam em data centers remotos com esse serviço? 

Recomenda-se que o serviço de balanceador de carga e as instâncias de cálculo residam localmente no mesmo data center. A interface gráfica (GUI) do serviço de balanceador de carga não mostrará as instâncias de cálculo de outros data centers remotos. No entanto, a GUI incluirá instâncias de cálculo de outros data centers na mesma cidade (por exemplo, data centers cujos nomes compartilhem as primeiras três letras, como `DALxx`). Todavia, é possível usar a interface de API para incluir instâncias de cálculo de qualquer data center remoto. 

## Qual versão do TLS é suportada com transferência de SSL? Quais cifras são suportadas?

O Bluemix Load Balancer Service suporta o TLS 1.2 com finalização de SSL. 

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


