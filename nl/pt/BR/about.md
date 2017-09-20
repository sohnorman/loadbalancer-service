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

# About

O serviço IBM Bluemix Load Balancer ajuda os clientes a melhorarem a disponibilidade de seus aplicativos críticos aos negócios, distribuindo o tráfego entre múltiplas instâncias do servidor de aplicativos e encaminhando o tráfego para instâncias funcionais apenas.

## Visão geral de recursos
O serviço IBM Bluemix Load Balancer oferece os recursos a seguir:

* Balanceador de carga público (voltado à Internet)
	* Serviço publicamente acessível por meio de seu nome completo do domínio
	* Instâncias do servidor de backend em sub-redes privadas
* Balanceamento de carga básico
	* Distribuição de tráfego com base em informações da porta do aplicativo da camada 4
	* Suporte para os aplicativos baseados em HTTP, HTTPS e TCP 
	* Variedade de métodos de balanceamento de carga, como round-robin (RR), round-robin ponderado e menos conexões
	* Balanceamento de carga entre o servidor virtual e as instâncias de cálculo bare metal que residem localmente no data center
* Verificações de funcionamento do servidor
	* Monitoramento periódico de funcionamento do servidor para assegurar que o tráfego seja encaminhado apenas para servidores funcionais 
	* Verificações de funcionamento da camada 4 para portas TCP e verificações de funcionamento da camada 7 para a porta HTTP 
* Transferência de SSL
	* Finalização de tráfego SSL (HTTPS) recebido com comunicação HTTP de texto sem formatação com servidores de backend
* Gerenciamento de tráfego avançado
	* Permanência do cliente (persistência de sessão)
	* Máximo de conexões por porta virtual
* Fácil gerenciamento usando a interface gráfica intuitiva e a API
* Confiabilidade integrada 
* Definição de preço por utilização 
