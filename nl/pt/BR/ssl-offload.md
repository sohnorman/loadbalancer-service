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

# Transferência de SSL

Para todas as conexões HTTPS recebidas, o serviço de balanceador de carga finaliza a conexão SSL e estabelece a comunicação HTTP de texto sem formatação com o servidor de backend. Os servidores de backend são, desse modo, transferidos da execução de handshakes SSL intensivos da CPU e de tarefas de criptografia/decriptografia, para que possam usar todos os ciclos de CPU para processar o tráfego de aplicativo. É necessário um certificado SSL para que o balanceador de carga execute tarefas de transferência de SSL. É possível usar um certificado SSL preexistente ou comprar um novo e gerenciá-lo por meio do [Armazenamento de certificados do Bluemix/Softlayer](https://control.softlayer.com/security/sslcerts). 

**NOTA:** o serviço de balanceador de carga suporta TLS versão 1.2 com transferência de SSL. Ele não suporta SSLv3 em razão de suas vulnerabilidades. A lista de cifras SSL não pode ser customizada neste momento. 
