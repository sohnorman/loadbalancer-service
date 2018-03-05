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

# Référence d'API
L'interface de programmation SoftLayer® permet aux développeurs et aux administrateurs système d'interagir directement avec le système backend de SoftLayer. 
{:shortdesc}

L'interface de programmation SoftLayer (SLAPI) offre un grand nombre de fonctionnalités du portail client, ce qui signifie généralement que si une interaction est disponible dans le portail client, elle peut également être exécutée dans l'interface. Puisque vous pouvez interagir à l'aide d'un programme avec toutes les portions de l'environnement SoftLayer au sein de l'API, vous pouvez utiliser l'API pour automatiser les tâches.

L'interface de programmation SoftLayer est un système à appel de procédure distante. Chaque appel implique l'envoi de données vers un noeud final d'API et la réception de données structurées en retour. Le format utilisé pour l'envoi et la réception de données à l'aide de SLAPI dépend de l'implémentation que vous avez choisie. L'interface SLAPI utilise actuellement SOAP, XML-RPC ou REST pour la transmission de données. 

Pour plus d'informations sur l'API SoftLayer et les API du service d'équilibreur de charge IBM Cloud, voir les ressources suivantes dans le réseau de développement SoftLayer :
* [SoftLayer API Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://sldn.softlayer.com/article/softlayer-api-overview){: new_window} 
* [Getting Started with the SoftLayer API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}

Les exemples ci-dessous utilisent un client SOAP en Python avec Zeep.

## Exemple de création d'un équilibreur de charge
### Récupération de l'ID du package produit et du prix de l'article
```
from zeep import Client, xsd
import sys

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL for SoftLayer_Product_Package API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Package?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])
)

# Create XSD value objects
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

### Vérification de la commande de l'équilibreur de charge
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# Private subnet id
privateSubnetId = '<Your subnet id>'

# Order details
# Package id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasPackageId = 805
# ItemPrice id retrieved from SoftLayer_Product_Package API
# (example provided above)
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

# WSDL for SoftLayer_Product_Order API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Required since LBaaS is an hourly service
    useSystemPublicIpPool=True  # Optional - Default is "True" to allocate load
                                # balancer public IPs from an IBM system pool,
                                # otherwise "False" from the public VLAN
                                # under your account
)

# Make SLAPI call to SoftLayer_Product_Order::verifyOrder API
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

### Commande de l'équilibreur de charge
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apikey>'
# Private subnet id
privateSubnetId = '<Your subnet id>'

# Order details
# Package id retrieved from SoftLayer_Product_Package API
# (example provided above)
lbaasPackageId = 805 
# ItemPrice id retrieved from SoftLayer_Product_Package API
# (example provided above)
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

# WSDL for SoftLayer_Product_Order API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Product_Order?wsdl'
client = Client(wsdl)
orderDataType = client.get_type(
    'ns0:SoftLayer_Container_Product_Order_Network_LoadBalancer_AsAService'
)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
orderDataValue = orderDataType(
    name=name, packageId=lbaasPackageId, prices=lbaasItemPrices,
    subnets=subnets, protocolConfigurations=protocolConfigurations,
    useHourlyPricing=True,      # Required since LBaaS is an hourly service
    useSystemPublicIpPool=True  # Optional - Default is "True" to allocate load
                                # balancer public IPs from an IBM system pool,
                                # otherwise "False" from the public VLAN
                                # under your account
)

# Make SLAPI call to SoftLayer_Product_Order::placeOrder API
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

## Exemple d'obtention d'équilibreurs de charge
### Recensement de tous les équilibreurs de charge
```
from zeep import Client

# Username and apikey SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3.1/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# Prepare auth for SOAP header
userauth = {'authenticate': {'username': username, 'apiKey': apiKey}}

# Retrieve all load balancer objects
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

### Obtention des détails relatifs à un équilibreur de charge spécifique
```
from zeep import Client, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the load balancer
uuid = '<Your load balancer uuid>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners, healthMonitors]')

# Retrieve a specific load balancer object (with objectMask to retrieve "listeners")
loadbalancer = client.service.getLoadBalancer(_soapheaders=[userAuthValue,objectMaskValue], uuid=uuid)
print 'Name: %s' % loadbalancer.name
print 'Address: %s' % loadbalancer.address
print 'OperatingStatus: %s' % loadbalancer.operatingStatus
print 'ProvisioningStatus: %s' % loadbalancer.provisioningStatus
print 'Listeners: %s' % loadbalancer.listeners
print 'HealthMonitors: %s\r\n' % loadbalancer.healthMonitors
```
{: codeblock}

## Exemple de mise à jour d'un équilibreur de charge
### Ajout d'un membre
```
from zeep import Client, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apikey>'
# UUID of load balancer to be updated
uuid = '<Your load balancer uuid>'
# Backend servers to be added
serverInstances = [ 
    {
        'privateIpAddress': '10.121.220.141', #update with the correct IP
        'weight': 80 #weight is only applicable to Weight Round Robin listeners
    },  
    {
        'privateIpAddress': '10.121.220.142'  #update with the correct IP
        # use default weight
    }   
]

# WSDL for SoftLayer_Network_LBaaS_Member API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Member?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[members]')

# Make SLAPI call to SoftLayer_Network_LBaaS_Member::addLoadBalancerMember API
result = client.service.addLoadBalancerMembers(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, serverInstances=serverInstances
)
print result
```
{: codeblock}

### Ajout d'un protocole
```
from zeep import Client, xsd 

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of load balancer
uuid = '<Your load balancer UUID>'
# New protocol to add
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

# WSDL for SoftLayer_Network_LBaaS_Listener API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_Listener?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# XSD for objectMask
xsdObjectMask = xsd.Element(
    '{http://api.service.softlayer.com/soap/v3/}SoftLayer_ObjectMask',
    xsd.ComplexType([
        xsd.Element('{http://api.service.softlayer.com/soap/v3/}mask', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)
objectMaskValue = xsdObjectMask(mask='mask[listeners]')

# Make SLAPI call to SoftLayer_Network_LBaaS_Listener::updateLoadBalancerProtocols API
result = client.service.updateLoadBalancerProtocols(
    _soapheaders=[userAuthValue, objectMaskValue],
    loadBalancerUuid=uuid, protocolConfigurations=protocolConfigurations
)
listeners = result['listeners']
print listeners
```
{: codeblock}

## Exemple d'annulation d'un équilibreur de charge
### Annulation d'un équilibreur de charge
```
from zeep import Client, xsd 
from zeep.exceptions import Fault

# Username and apikey for SLAPI call
username = '<Your username>'
apiKey = '<Your apiKey>'
# UUID of the load balancer to be cancelled
uuid = '<Your load balancer uuid>'

# WSDL for SoftLayer_Network_LBaaS_LoadBalancer API
wsdl = 'https://api.softlayer.com/soap/v3/SoftLayer_Network_LBaaS_LoadBalancer?wsdl'
client = Client(wsdl)

# XSD for authentication
xsdUserAuth = xsd.Element(
    '{http://api.softlayer.com/soap/v3/}authenticate',
    xsd.ComplexType([
        xsd.Element('{http://api.softlayer.com/soap/v3/}username', xsd.String()),
        xsd.Element('{http://api.softlayer.com/soap/v3/}apiKey', xsd.String())
    ])  
)

# Create XSD value objects
userAuthValue = xsdUserAuth(username=username, apiKey=apiKey)

# Make SLAPI call to SoftLayer_Network_LBaaS_LoadBalancer::cancelLoadBalancer API
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
