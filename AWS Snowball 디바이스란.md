# AWS Snowball 디바이스란?

> AWS Snowball 서비스는 

> **물리적 스토리지 디바이스를 사용**하여 

> 인터넷보다 빠른 속도로 

> Amazon Simple Storage Service(Amazon S3)와 

> 온사이트 데이터 스토리지 위치 간에 

> **대량 데이터**를 전송한다. 

* AWS Snowball으로 작업하면 시간과 비용을 절약할 수 있다.  

* Snowball은 작업을 생성하고 데이터를 추적하고 완료까지 전 과정의 작업 상태를 추적하는 데 사용할 수 있는 강력한 인터페이스를 제공한다..

* Snowball 디바이스는 AWS Key Management Service(AWS KMS)로 보호되는 물리적으로 견고한 디바이스이다.
* 이 디바이스는 전송 중 데이터를 안전하게 보호한다.
*  지역 운송업체는 Amazon S3와 온사이트 데이터 스토리지 위치 간에 Snowball을 전송한다.
*  디바이스를 사용할 수 있는 AWS 리전 목록은 Snowball [AWS Snowball의 ](https://docs.aws.amazon.com/general/latest/gr/rande.html#snowball_region)*단원을 참조오.AWS General Reference*



---

**참고**

**Snowball의 용도는 대량 데이터를 전송하는 것**입니다. 온프레미스 데이터 센터와 Amazon S3 간에 <u>**10TB 미만의 데이터를 전송하려는 경우에는 Snowball이 경제적인 방법이 아닐 수 있습니다**.</u>

---



## Snowball 기능

Snowball 디바이스를 사용하는 AWS Snowball에는 다음과 같은 기능이 있습니다.

- 80TB 및 50TB 모델은 미국 리전에서 사용할 수 있으며, 50TB 모델은 기타 모든 AWS 리전에서 사용
- 강화된 보안은 미사용 데이터와 물리적으로 전송 중인 데이터를 보호
- 하드웨어 디바이스를 직접 구입하거나 유지 관리할 필요가 없다.
- AWS Snow 패밀리 관리 콘솔을 통해 또는 작업 관리 API를 사용하여 프로그래밍 방식으로 작업을 관리가능.
- **온프레미스 데이터 센터와 Snowball 간에 로컬 데이터를 전송할 수 있다**. 
  - 다운로드 가능한 독립 실행형 클라이언트인 Snowball 클라이언트를 통해 이러한 전송을 수행할 수 있다. 또는 다운로드 가능한 Snowball용 Amazon S3 어댑터와 함께 Amazon S3 REST API 호출을 사용하여 프로그래밍 방식으로 전송할 수 있다. 자세한 내용은 [Snowball을 사용한 데이터 전송](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/using-device.html#snowball-data-transfer) 항목을 참조.
- Snowball은 자체 운송 컨테이너를 가지고 있으며, Snowball을 배송할 준비가 완료되면 E Ink 디스플레이가 변경되어 배송 라벨을 표시. 자세한 내용은 [AWS Snowball에 대한 배송 고려 사항](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/shipping.html) 항목을 참조.

를 사용할 수 있는 AWS 리전 목록은 Snowball 어플라이언스[의 ](https://docs.aws.amazon.com/general/latest/gr/rande.html#snowball_region)AWS Snowball*을 참조.AWS General Reference*





**참고**

Snowball은 국제 배송 또는 미국 이외의 AWS 리전 간 배송을 지원하지 않습니다. 배송 제한에 대한 자세한 내용은 [리전 기반 배송 제한](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/shipping.html#shipwithinregion) 단원을 참조하십시오.





## AWS Snowball 사용을 위한 사전 조건

Snowball을 사용하여 Amazon S3에 데이터를 전송하기 전에 다음을 수행해야 합니다.

- IAM(AWS Identity and Access Management)에서 AWS 계정 및 관리자 사용자를 생성합니다. 자세한 내용은 [Snowball에 대한 IAM 사용자 생성](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/auth-access-control.html#create-iam-user) 항목을 참조하십시오.
- 데이터를 가져오는 경우 다음을 수행합니다.
  - 전송하려는 파일 및 폴더의 이름을 Amazon S3에 대한 [객체 키 명명 지침](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html#object-key-guidelines)에 따라 지정했는지 확인합니다. 이름이 이러한 지침을 충족하지 않는 파일 또는 폴더는 Amazon S3으로 가져오지 않습니다.
  - Amazon S3으로 가져오려는 데이터를 계획합니다. 자세한 내용은 [페타바이트 데이터를 효율적으로 전송하는 방법](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/transfer-petabytes.html) 항목을 참조하십시오.
- 데이터를 내보내는 경우 다음을 수행합니다.
  - 작업을 생성할 때 내보낼 데이터를 이해합니다. 자세한 내용은 [내보내기 범위 사용](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/ranges.html) 항목을 참조하십시오.
  - 파일 이름에 콜론(`:`)이 있는 파일의 경우 이러한 파일을 가져올 내보내기 작업을 생성하기 전에 Amazon S3에서 파일 이름을 변경합니다. 파일 이름에 콜론이 있는 파일은 Microsoft Windows Server로의 내보내기가 실패합니다.

## 도구 및 인터페이스

Snowball은 AWS Snow 패밀리 관리 콘솔과 작업 관리 API를 사용하여 작업을 생성하고 관리합니다. Snowball 디바이스에서 로컬로 데이터를 전송하려면 Snowball 클라이언트 또는 Snowball용 Amazon S3 어댑터을 사용하십시오. 자세한 사용 방법은 다음 항목을 참조하십시오.

- [AWS Snow 패밀리 관리 콘솔 사용](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/using-console.html)
- [AWS Snowball 디바이스 사용](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/using-device.html)
- [Snowball을 사용한 데이터 전송](https://docs.aws.amazon.com/ko_kr/snowball/latest/ug/using-device.html#snowball-data-transfer)

또한 AWS Snowball에 대한 작업 관리 API에 대해 알아보는 것이 좋습니다. 자세한 내용은 [AWS Snowball API 참조](https://docs.aws.amazon.com/snowball/latest/api-reference/api-reference.html) 항목을 참조하십시오.

## AWS Snowball 관련 서비스

이 안내서의 내용은 Amazon S3 사용자를 대상으로 합니다.