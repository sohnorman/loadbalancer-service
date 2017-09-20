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

# SSL 오프로드

모든 수신 HTTPS 연결의 경우 로드 밸런서 서비스는 SSL 연결을 종료하고 백엔드 서버와의 일반 텍스트 HTTP 통신을 확립합니다. 그러므로 백엔드 서버는 CPU가 많이 사용되는 SSL 핸드쉐이크 및 암호화/복화화 태스크를 수행하지 않도록 오프로드됩니다. SSL 인증서는 로드 밸런서가 SSL 오프로드 태스크를 수행하는 데 필요합니다. 기존 SSL 인증서를 사용하거나 새 인증서를 구입할 수 있고 [Bluemix/Softlayer 인증서 저장소](https://control.softlayer.com/security/sslcerts)를 통해 SSL 인증서를 관리할 수 있습니다. 

**참고:** 로드 밸런서 서비스는 TLS 버전 1.2 및 SSL 오프로드를 지원합니다. 취약점으로 인해 SSLv3은 지원하지 않습니다. 현재 SSL 암호 목록을 사용자 정의할 수 없습니다.  
