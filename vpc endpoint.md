### vpc endpoint 란?
vpc endpoint 는 가상 장치로서 VPC와 AWS서비스를 전용 연결 할 수 있도록 한다. 
즉 private connection이 가능하도록 만들어주는 것이다.

예를 들어 인스턴스에서 S3에 엑세스 할때, 인터넷 게이트웨이나 NAT가 필요없이 VPC endpoint만으로도 가능하다. 
현재는 동일 리전 내의 S3 에서만 액세스 가능하지만 점차 지원가능한 AWS 서비스를 늘려 나갈 예정이다. 
VPC Endpoint 는 VPC 내에서 Gateway 처럼 Route Tables에 등록하는 형식으로 간편하게 사용할 수 있다. 

출처 : 
https://wisen.co.kr/pages/blog/blog-detail.html?idx=223
