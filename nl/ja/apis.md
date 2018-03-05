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

# API リファレンス
SoftLayer® アプリケーション・プログラミング・インターフェース (API) は、開発者やシステム管理者が SoftLayer のバックエンド・システムを直接操作できるようにする開発用インターフェースです。 
{:shortdesc}

SoftLayer API (SLAPI) により、カスタマー・ポータルの多くの機能が使用可能になります。つまり、通常、カスタマー・ポータルでの操作が可能であれば、API でも実行することができます。 API 内で SoftLayer 環境のすべての部分をプログラマチックに操作できるので、API を使用してタスクを自動化することができます。

SoftLayer API はリモート・プロシージャー・コール・システムです。 各呼び出しでは、API エンドポイントにデータが送信され、それに対して構造化データを受信します。 SLAPI を使用したデータの送受信に使用される形式は、選択した API の実装方法によって異なります。 SLAPI は現在、データ伝送に SOAP、XML-RPC、または REST を使用しています。 

SoftLayer API、IBM Cloud Load Balancer サービス API については、SoftLayer Development Network にある以下の資料を参照してください。
* [SoftLayer API Overview ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://sldn.softlayer.com/article/softlayer-api-overview){: new_window} 
* [Getting Started with the SoftLayer API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/article/getting-started){: new_window}
* [SoftLayer_Product_Package API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/reference/services/SoftLayer_Product_Package){: new_window}
* [SoftLayer_Network_LBaaS_LoadBalancer API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_LoadBalancer){: new_window}
* [SoftLayer_Network_LBaaS_Listener API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Listener){: new_window}
* [SoftLayer_Network_LBaaS_Member API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_Member){: new_window}
* [SoftLayer_Network_LBaaS_HealthMonitor API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://sldn.softlayer.com/reference/services/SoftLayer_Network_LBaaS_HealthMonitor){: new_window}

以下の例は、Zeep SOAP クライアントで Python を使用しています。

## ロード・バランサーの作成例
### 製品パッケージ ID と品目の価格の取得
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

### ロード・バランサーの注文の確認
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

### ロード・バランサーの注文を出す
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

## ロード・バランサーの取得例
### すべてのロード・バランサーのリスト
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

### 特定のロード・バランサーの詳細の取得
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

## ロード・バランサーの更新例
### メンバーの追加
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

### プロトコルの追加
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

## ロード・バランサーのキャンセル例
### ロード・バランサーのキャンセル
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
