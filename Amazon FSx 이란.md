# Amazon FSx for Windows File Server이란 ?



Amazon FSx for Windows File Server 는 완전히 기본 제공되는 Windows 파일 시스템으로 백업되는 완벽하게 관리되는 Microsoft Windows 파일 서버를 제공합니다. Amazon FSx for Windows File Server 은 엔터프라이즈 애플리케이션을 쉽게 리프트 및 전환할 수 있는 기능, 성능 및 호환성을 갖추고 있습니다. AWS 클라우드.

Amazon FSx 은 Microsoft Windows Server를 기반으로 완벽하게 관리되는 파일 스토리지를 통해 광범위한 엔터프라이즈 Windows 워크로드를 지원합니다. Amazon FSx 은 Windows 파일 시스템 기능과 네트워크상에서 파일 스토리지에 액세스할 수 있는 업계 표준 SMB(서버 메시지 블록) 프로토콜을 기본적으로 지원합니다. Amazon FSx 은 기본 Windows 호환성, 엔터프라이즈 성능 및 기능, 일관된 1밀리초 미만 대기 시간 등을 갖춘 AWS Cloud의 엔터프라이즈 애플리케이션에 최적화되어 있습니다.

Windows 개발자와 관리자가 이용 중인 Amazon FSx 상의 파일 스토리지, 코드, 애플리케이션과 도구를 이용하면 어떤 변경도 없이 작업을 계속 진행할 수 있습니다. Windows 애플리케이션 및 워크로드에 적합 Amazon FSx 비즈니스 애플리케이션, 홈 디렉토리, 웹 서비스, 컨텐츠 관리, 데이터 분석, 소프트웨어 빌드 설정 및 미디어 처리 워크로드 등이 포함됩니다.

완전 관리형 서비스인 Amazon FSx for Windows File Server는 파일 서버 및 스토리지 볼륨 설정과 프로비저닝을 위한 관리 부담이 없습니다. 또한, Amazon FSx 은 Windows 소프트웨어를 최신 상태로 유지하고 하드웨어 장애를 감지 및 해결하며 백업을 수행합니다. 또한 다음과 같은 다른 AWS 서비스와의 풍부한 통합을 제공합니다. [AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html), [Microsoft Active Directory용 AWS 디렉터리 서비스(Enterprise Edition)](https://docs.aws.amazon.com/directoryservice/latest/admin-guide/directory_microsoft_ad.html), [Amazon WorkSpaces](https://docs.aws.amazon.com/workspaces/latest/adminguide/amazon-workspaces.html), [AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html), 및 [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html).

## Amazon FSx for Windows File Server 자원: 파일 시스템, 백업 및 파일 공유

의 기본 리소스 Amazon FSx 은(는) *파일 시스템* 및 *백업*. 파일 시스템은 파일과 폴더를 저장하고 액세스하는 곳입니다. 파일 시스템은 Windows 파일 서버 및 스토리지 볼륨으로 구성되며 DNS 이름으로 액세스합니다. 파일 시스템을 생성할 때 스토리지 용량(GiB)과 처리량 용량(MB/초)을 지정합니다. 필요에 따라 이러한 속성을 수정할 수 있습니다. 자세한 내용은 [스토리지 용량 관리](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/managing-storage-capacity.html) 및 [처리량 용량 관리](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/managing-throughput-capacity.html) 단원을 참조하십시오.

Amazon FSx for Windows File Server 백업은 파일 시스템 정합성이 보장되고 내구성이 뛰어나며 증분 백업입니다. 파일 시스템 정합성을 보장하려면 Amazon FSx 에서는 Microsoft Windows 에서 VSS(볼륨 섀도우 복사 서비스)를 사용합니다. 파일 시스템을 생성할 때 자동 일일 백업이 기본적으로 설정되며, 언제든지 추가 수동 백업을 수행할 수 있습니다. 자세한 내용은 [백업 작업](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/using-backups.html) 단원을 참조하십시오.

Windows 파일 공유는 SMB를 사용하는 컴퓨팅 인스턴스에서 액세스할 수 있는 파일 시스템 내의 특정 폴더(및 해당 하위 폴더)입니다. 파일 시스템에는 이미 다음과 같은 기본 Windows 파일 공유가 포함되어 있습니다. `\share`. Windows 에서 공유 폴더 그래픽 사용자 인터페이스(GUI) 도구를 사용하여 원하는 만큼 다른 Windows 파일 공유를 만들고 관리할 수 있습니다. 자세한 정보는 [Microsoft Windows 파일 공유 사용](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/using-file-shares.html) 단원을 참조하십시오.

### 파일 공유 액세스

Amazon FSx 는 SMB 프로토콜(버전 2.0~3.1.1 지원)을 사용하는 컴퓨팅 인스턴스에서 액세스할 수 있습니다. Windows Server 2008 및 Windows 7부터 시작되는 모든 Windows 버전과 Linux 의 현재 버전에서도 공유에 액세스할 수 있습니다. 다음을 매핑할 수 있습니다. Amazon FSx 파일 공유 Amazon Elastic Compute Cloud (Amazon EC2) 인스턴스 및 Amazon WorkSpaces 인스턴스, Amazon AppStream 2.0 인스턴스 및 AWS VM의 VMware 클라우드.

다음을 사용하여 온프레미스 컴퓨팅 인스턴스에서 파일 공유에 액세스할 수 있습니다. AWS Direct Connect 또는 AWS VPN. 파일 시스템과 동일한 VPC, AWS 계정 및 AWS Region에 있는 파일 공유에 액세스하는 것 외에도, 다른 Amazon VPC, 계정 또는 지역. VPC 피어링 또는 통과 게이트웨이를 사용하여 이 작업을 수행합니다. 자세한 정보는 [지원되는 액세스 방법](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/supported-fsx-clients.html#access-methods) 단원을 참조하십시오.

## 보안 및 데이터 보호

Amazon FSx 은 데이터를 보호할 수 있도록 다양한 수준의 보안 및 규정 준수를 제공합니다. 에서 관리하는 키를 사용하여 저장된 데이터(파일 시스템 및 백업 모두)를 자동으로 암호화합니다. AWS Key Management Service (AWS KMS). 전송 중인 데이터는 SMB Kerberos 세션 키를 사용하여 자동으로 암호화됩니다. ISO, PCI-DSS 및 SOC 인증을 준수하는 것으로 평가되었으며 HIPAA에 적합합니다.

Amazon FSx 에서는 Windows ACL(액세스 제어 목록)을 사용하여 파일 및 폴더 수준에서 액세스 제어를 제공합니다. 파일 시스템 레벨에서 액세스 제어 기능을 제공합니다. Amazon Virtual Private Cloud (Amazon VPC) 보안 그룹. 또한, API 수준에서 AWS Identity and Access Management (IAM) 액세스 정책. 파일 시스템에 액세스하는 사용자는 Microsoft Active Directory로 인증됩니다. Amazon FSx 통합 AWS CloudTrail API 호출을 모니터링 및 기록하여 사용자의 Amazon FSx 자원.

또한 매일 파일 시스템의 내구성이 뛰어난 백업을 자동으로 수행하여 데이터를 보호하고 언제든지 추가 백업을 수행할 수 있습니다. 자세한 정보는 [Amazon FSx의 보안](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/security.html) 단원을 참조하십시오.

## 가용성 및 내구성

Amazon FSx for Windows File Server 은 두 가지 수준의 가용성과 내구성을 갖춘 파일 시스템을 제공합니다. 단일 AZ 파일은 구성 요소 장애를 자동으로 감지하고 해결하여 단일 가용성 영역(AZ) 내에서 고가용성을 보장합니다. 또한 다중 AZ 파일 시스템은 AWS 지역. Single-AZ 및 Multi-AZ 파일 시스템 구축에 대한 자세한 내용은 다음을 참조하십시오. [가용성 및 내구성: 단일 AZ 및 Multi-AZ 파일 시스템](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/high-availability-multiAZ.html).

## 파일 시스템 관리

다음을 관리할 수 있습니다. Amazon FSx for Windows File Server 사용자 지정 원격 관리 PowerShell 명령을 사용하거나 경우에 따라 Windows 네이티브 GUI를 사용하는 파일 시스템 관리 방법에 대해 자세히 알아보려면 Amazon FSx 파일 시스템, 참조 [파일 시스템 관리](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/administering-file-systems.html).

## 가격 및 성능 유연성

Amazon FSx for Windows File Server 는 솔리드 스테이트 드라이브(SSD) 및 하드 디스크 드라이브(HDD) 스토리지 유형 모두를 제공하여 가격과 성능의 유연성을 제공합니다. HDD 스토리지는 홈 디렉토리, 사용자 및 부서 공유, 컨텐츠 관리 시스템 등 광범위한 워크로드를 위해 설계되었습니다. SSD 스토리지는 데이터베이스, 미디어 처리 작업 부하 및 데이터 분석 응용 프로그램을 포함하여 지연 시간에 가장 민감한 최고 성능 작업 부하용으로 설계되었습니다.

함께 Amazon FSx for Windows File Server, 파일 시스템 스토리지와 처리량을 독립적으로 프로비저닝하여 비용과 성능을 적절히 조합할 수 있습니다. 변화하는 워크로드 요구 사항을 충족하도록 파일 시스템의 스토리지 및 처리량 용량을 수정하여 필요한 만큼만 비용을 지불할 수 있습니다. 자세한 정보는 [로 비용 최적화 Amazon FSx](https://docs.aws.amazon.com/ko_kr/fsx/latest/WindowsGuide/optimize-fsx-costs.html) 단원을 참조하십시오.