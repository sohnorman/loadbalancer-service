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

# Riferimento API
L'API (Application Programming Interface) di SoftLayer® è un'interfaccia di sviluppo che fornisce agli sviluppatori e agli amministratori di sistema
interazione diretta con il sistema di backend di SoftLayer. 
{:shortdesc}

La SLAPI (SoftLayer API) rafforza molte delle funzioni nel portale clienti, il che normalmente
significa che se è possibile un'interazione nel portale clienti, può essere eseguita anche nell'API. Poiché puoi programmaticamente interagire
con tutte le parti dell'ambiente SoftLayer nell'API, puoi utilizzarla per le attività automatiche.

L'API SoftLayer è un sistema di chiamata di procedura remota. Ogni chiamata implica l'invio di dati verso un endpoint dell'API e la
ricezione dei dati strutturati come ritorno. Il formato utilizzato per inviare e ricevere i dati con la SLAPI dipende
da quale implementazione dell'API scegli. La SLAPI al momento utilizza SOAP, XML-RPC o REST per la trasmissione dei dati. 

Per ulteriori informazioni sull'API SoftLayer, sulle API del servizio IBM Cloud Load Balancer, consulta le seguenti risorse
nella rete di sviluppo SoftLayer:
* [SoftLayer API Overview ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://sldn.softlayer.com/article/softlayer-api-overview){: new_window} 
* [Getting Started with the SoftLayer API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}

I seguenti esempi utilizzano Python con il client SOAP zeep.

## Esempio di creazione del programma di bilanciamento del carico
### Richiama l'ID del pacchetto del prodotto e il prezzo elemento
```
from zeep import Client, xsd
import sys

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL per l'API SoftLayer_Product_Package
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Package?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

lbaasPackage = None
result = client.service.getAllObjects(_soapheaders=[userAuthValue])
productPackages = result['body']['getAllObjectsReturn']
for package in productPackages:
    if package.name == 'Load Balancer As A Service (LBaaS)':
        lbaasPackage = package
        print 'LBaaS product package id: %s' % lbaasPackage.id
        break

if lbaasPackage is None:
    print 'LBaaS product package cannot be found!'
    sys.exit()

xsdObjectInitPar = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_Product_PackageInitParameters',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}id', xsd.String())
    ])
)

objectInitParValue = xsdObjectInitPar(id=lbaasPackage.id)
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

objectMaskValue = xsdObjectMask(mask='mask[id;item.description]')

result = client.service.getItemPrices(_soapheaders=[userAuthValue,objectInitParValue,objectMaskValue])
itemPrices = result['body']['getItemPricesReturn']
for itemPrice in itemPrices:
    if itemPrice.locationGroupId is None:
        print 'Item Price Id: %s' % itemPrice.id
```
{: codeblock}

### Verifica l'ordine del programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# ID sottorete privata
privateSubnetId = '<Your subnet id>'

# Dettagli ordine
# ID pacchetto richiamato dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasPackageId = 805
# ID prezzo elemento dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasItemPrices = [{'id':199447}, {'id':199467}, {'id':205839}, {'id':205907}]
name = 'MyLoadBalancer'
subnets = [{'id': privateSubnetId}]
protocolConfigurations = [{
    'frontendProtocol':'HTTP',
    'frontendPort':80,
    'backendProtocol':'HTTP',
    'backendPort':8080,
    'loadBalancingMethod':'ROUNDROBIN',
    'maxConn':1000
}]

# WSDL per l'API SoftLayer_Product_Order
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Obbligatorio da quando LBaaS è un servizio orario
    useSystemPublicIpPool=True  # Facoltativo - Valore predefinito di "True" per assegnare gli
                                # IP pubblici del programma di bilanciamento del carico da un pool di sistema IBM,
                                # altrimenti "False" dalla VLAN pubblica
                                # nel tuo account
)

# Effettua la chiamata SLAPI all'API SoftLayer_Product_Order::verifyOrder
try:
    result = client.service.verifyOrder(
        _soapheaders=[userAuthValue],
        orderData=orderDataValue
    )   

    print 'The order is valid!'

except Fault as exp:
    print 'The order is INVALID!\r\n>>> %s' % exp
```
{: codeblock}

### Inserisci l'ordine del programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apikey>'
# ID sottorete privata
privateSubnetId = '<Your subnet id>'

# Dettagli ordine
# ID pacchetto richiamato dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasPackageId = 805
# ID prezzo elemento dall'API SoftLayer_Product_Package
# (esempio fornito di seguito)
lbaasItemPrices = [{'id':199447}, {'id':199467}, {'id':205839}, {'id':205907}]
name = 'MyLoadBalancer'
subnets = [{'id': privateSubnetId}]
protocolConfigurations = [{
    'frontendProtocol':'HTTP',
    'frontendPort':80,
    'backendProtocol':'HTTP',
    'backendPort':8080,
    'loadBalancingMethod':'ROUNDROBIN',
    'maxConn':1000
}]

# WSDL per l'API SoftLayer_Product_Order
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Obbligatorio da quando LBaaS è un servizio orario
    useSystemPublicIpPool=True  # Facoltativo - Valore predefinito di "True" per assegnare gli
                                # IP pubblici del programma di bilanciamento del carico da un pool di sistema IBM,
                                # altrimenti "False" dalla VLAN pubblica
                                # nel tuo account
)

# Effettua la chiamata SLAPI all'API SoftLayer_Product_Order::placeOrder
try:
    result = client.service.placeOrder(
        _soapheaders=[userAuthValue],
        orderData=orderDataValue,
        saveAsQuote=False
    )   

    print 'Order has been accepted.'

except Fault as exp:
    print 'Place order failed:\r\n>>> %s' % exp
```
{: codeblock}

## Esempio di acquisizione del programma di bilanciamento del carico
### Elenca tutti i programmi di bilanciamento del carico
```
from zeep import Client

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# Prepara autenticazione per l'intestazione SOAP
userauth = {'authenticate': {'username': username, 'apiKey': apiKey}}

# Richiama tutti gli oggetti del programma di bilanciamento del carico
result = client.service.getAllObjects(_soapheaders=userauth)
loadbalancers = result['body']['getAllObjectsReturn']
for loadbalancer in loadbalancers:
    print 'UUID: %s' % loadbalancer.uuid
    print 'Name: %s' % loadbalancer.name
    print 'Address: %s' % loadbalancer.address
    print 'OperatingStatus: %s' % loadbalancer.operatingStatus
    print 'ProvisioningStatus: %s\r\n' % loadbalancer.provisioningStatus
```
{: codeblock}

### Richiama i dettagli di un programma di bilanciamento del carico specifico
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer uuid>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners, healthMonitors]')

# Richiama un oggetto del programma di bilanciamento del carico specifico (con objectMask per richiamare "listeners")
loadbalancer = client.service.getLoadBalancer(_soapheaders=[userAuthValue,objectMaskValue], uuid=uuid)
print 'Name: %s' % loadbalancer.name
print 'Address: %s' % loadbalancer.address
print 'OperatingStatus: %s' % loadbalancer.operatingStatus
print 'ProvisioningStatus: %s' % loadbalancer.provisioningStatus
print 'Listeners: %s' % loadbalancer.listeners
print 'HealthMonitors: %s\r\n' % loadbalancer.healthMonitors
```
{: codeblock}

## Esempio di aggiornamento di un programma di bilanciamento del carico
### Aggiungi un membro
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apikey>'
# UUID del programma di bilanciamento del carico da aggiornare
uuid = '<Your load balancer uuid>'
# Server di backend da aggiungere
serverInstances = [
    {
        'privateIpAddress': '10.121.220.141', #aggiorna con l'IP corretto
        'weight': 80 #weight is only applicable to Weight Round Robin listeners
    },
    {
        'privateIpAddress': '10.121.220.142'  #aggiorna con l'IP corretto
        # utilizza peso predefinito
    }   
]

# WSDL per l'API SoftLayer_Network_LBaaS_Member
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Member?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[members]')

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_Member::addLoadBalancerMember
result = client.service.addLoadBalancerMembers(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, serverInstances=serverInstances
)
print result
```
{: codeblock}

### Aggiungi un protocollo
```
from zeep import Client, xsd 

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico
uuid = '<Your load balancer UUID>'
# Nuovo protocollo da aggiungere
protocolConfigurations = [ 
    {   
        'frontendProtocol': 'TCP',
        'frontendPort': 90, 
        'backendProtocol': 'TCP',
        'backendPort': 9090,
        'loadBalancingMethod': 'WEIGHTED_RR',
        'maxConn': 2000
    }   
]

# WSDL per l'API SoftLayer_Network_LBaaS_Listener
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Listener?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD per objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners]')

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_Listener::updateLoadBalancerProtocols
result = client.service.updateLoadBalancerProtocols(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, protocolConfigurations=protocolConfigurations
)
listeners = result['listeners']
print listeners
```
{: codeblock}

## Esempio di annullamento di un programma di bilanciamento del carico
### Annulla un programma di bilanciamento del carico
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Nome utente e chiave api per la chiamata SLAPI
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID del programma di bilanciamento del carico da annullare
uuid = '<Your load balancer uuid>'

# WSDL per l'API SoftLayer_Network_LBaaS_LoadBalancer
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD per l'autenticazione
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Crea oggetti valore XSD
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Effettua la chiamata SLAPI all'API SoftLayer_Network_LBaaS_LoadBalancer::cancelLoadBalancer
try:
    result = client.service.cancelLoadBalancer(
        _soapheaders=[userAuthValue],
        uuid=uuid
    )   

    if True:
        print 'The cancellation request is accepted.'

except Fault as exp:
    print 'Failed to cancel load balancer:\r\n>>> %s' % exp
```
{: codeblock}
