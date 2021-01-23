# Glacier이란? 



* Amazon S3 Glacier 및 S3 Glacier Deep Archive는 데이터 아카이빙 및 장기 백업을 위한 안전하고 내구성이 뛰어나고 매우 저렴한 Amazon S3 클라우드 스토리지 클래스입니다. 

* 99.999999999%의 내구성을 제공하도록 설계되었으며, 가장 엄격한 규제 요구 사항도 충족할 수 있는 종합적인 보안 및 규정 준수 기능을 제공합니다. 
* 고객은 월별 테라바이트당 1 USD의 저렴한 요금으로 데이터를 저장할 수 있으므로 온프레미스 솔루션과 비교하면 상당한 비용 절감을 기대할 수 있습니다. 
* 비용을 낮게 유지하면서 동시에 다양한 검색 요구를 지원하기 위해 Amazon S3 Glacier에서는 아카이브에 액세스하는 3가지 옵션(몇 분에서 몇 시간까지 소요)을 제공하며 S3 Glacier Deep Archive는 2가지 액세스 옵션(12~48시간 소요)을 제공합니다.





# 장점

### 1~5분의 빠른 검색

Amazon S3 Glacier 스토리지 클래스에서는 사용 사례에 맞춰 3가지 검색 옵션을 제공합니다. 긴급 검색은 보통 데이터를 반환하는 데 1~5분이 걸리며 [활성 아카이브](https://aws.amazon.com/ko/archive/) 사용 사례에 적합합니다. 표준 검색은 보통 3~5시간 사이에 완료되며 백업 데이터, 미디어 편집 또는 장기 분석과 같이 시간이 덜 민감한 작업에 적합합니다. 대량 검색은 가장 저렴한 검색 옵션으로 대량의 데이터를 5~12시간 안에 반환합니다. Amazon S3 Glacier Deep Archive 스토리지 클래스는 2가지 검색 옵션(12~48시간 소요)을 제공합니다.

[Amazon S3 Glacier 검색 옵션에 대해 자세히 알아보기 »](https://aws.amazon.com/ko/glacier/faqs/#dataretrievals)

[Amazon S3 Glacier Deep Archive 검색 옵션에 대해 자세히 알아보기 »](https://aws.amazon.com/ko/s3/faqs/#Amazon_S3_Glacier_Deep_Archive)

### 따라올 수 없는 내구성 및 확장성

Amazon S3 Glacier 및 S3 Glacier Deep Archive 스토리지 클래스는 세계 최대의 글로벌 클라우드 인프라에서 실행되며 99.999999999%의 내구성을 제공하도록 설계되었습니다. 데이터가 하나의 AWS 리전 내에 지리적으로 분산된 최소 3개의 물리적 가용 영역에 자동 분산됩니다.

[AWS 글로벌 클라우드 인프라에 대해 자세히 알아보기 »](https://aws.amazon.com/ko/about-aws/global-infrastructure/)

### 가장 포괄적인 보안 및 규정 준수 기능

Amazon S3 Glacier 및 S3 Glacier Deep Archive 스토리지 클래스는 [AWS CloudTrail](https://aws.amazon.com/ko/cloudtrail/)과 정교하게 통합되어 감사를 위해 스토리지 API 호출 활동을 기록, 모니터링 및 보존하고 세 가지 서로 다른 암호화 형태를 지원합니다. 또한 이러한 스토리지 클래스는 SEC Rule 17a-4, PCI-DSS, HIPAA/HITECH, FedRAMP, EU GDPR 및 FISMA를 비롯한 보안 표준 및 규정 준수 인증을 지원하며, Amazon S3 객체 잠금은 WORM 스토리지 기능을 지원하므로 전 세계 거의 모든 규제 기관의 규정 준수 요구 사항을 충족할 수 있습니다.