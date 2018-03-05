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

# Descarga SSL

Para todas las conexiones HTTPS entrantes, el servicio del equilibrador de carga finaliza la conexión SSL y establece una comunicación HTTP de texto sin formato con el servidor back-end. En consecuencia, se descarga a los servidores back-end de las tareas de reconocimiento SSL y cifrado/descifrado que consumen más CPU para que puedan utilizar todos los ciclos de CPU para procesar el tráfico de las aplicaciones. Se necesita un certificado SSL para que el equilibrador de carga pueda realizar tareas de descarga SSL. Puede utilizar un certificado SSL preexistente o adquirir uno y gestionarlo desde el [almacén de certificados de IBM Cloud](https://control.softlayer.com/security/sslcerts). 

**NOTA:** el servicio de equilibrador de carga soporta TLS versión 1.2 con descarga SSL. No soporta SSLv3 debido a sus vulnerabilidades. En estos momentos no se puede personalizar la lista de cifrado SSL. 
