# 배포

웹 호스팅 클라우드 세 가지
### 1. [웹 호스팅](#web-hosting) 
### 2. [IaaS(infrastructure as a service)](#IaaS)
### 3. [PaaS(platform as a service)](#PaaS)
### 4. [SaaS(software as a service)](#SaaS)

_____
## web hosting
배포를 하려면 도메인이 필요하다. 이 도메인이 고정ip인데, 예전에는 고정 ip를 얻고 서버를 돌리려면 물리적인 컴퓨터가 필요했다. 하지만 가상화가 되어 웹 호스팅을 할 수 있는 클라우드 시스템이 생겨났다.

가상 머신을 임대하는 것이기 때문에 몇 대를 빌렸는지 모른다.

가상화 기술이 발전하면서 호스팅형식에서 클라우드 서비스로 동향이 바뀌었다.

____
## IaaS
infrastructure as a service

Iass는 Pass, Saas의 기반이 되는 기술이다.

서버를 운영하기 위해서는 서버 자원, IP, Network, cpu,memory,HDD 등등 인프라를 구축하기 위해 여러가지가 필요하다.

Iaas는 이러한 것들을 가상의 환경에서 쉽고 편하게 이용할 수 있게 서비스 형태로 제공한다.

예를 들어 AWS EC2,GCP,azure

쉽게 말해 가상머신의 자원을 빌리는 서비스
_____
## PaaS
Platform as a Service

서비스를 개발 할 수 있는 안정적인 환경(Platform)과 그 환경을 이용하는 응용 프로그램을 개발 할 수 있는 API까지 제공하는 형태를 Paas

이번에 실습하는 heroku,AWS lightsail

쉽게 말해 가상머신의 플렛폼(이걸 올려달라고 요청하면 알아서 올려주는 것)을 제공하는 서비스

## SaaS
Cloud환경에서 동작하는 응용프로그램을 서비스 형태로 제공하는 것을 Saas라고 합니다. 

예를들어 메일,드라이브,GOOGLE DOCS 등의 서비스를 들 수 있음

쉽게 말해 모든지 만들어져 있는 cloud
