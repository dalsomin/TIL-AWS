#### **VPC**

- 가상 사설 네트워크 기능을 제공하는 서비스
- 서브넷, 라우팅 테이블, ACL 등의 기능을 제공
- 1 Subtnet은 1 AZ에 상응함
- 인스턴스의 가상 방화벽인 Security group은 Stateful, Network ACL은 Stateless 성격을 지님
  - Stateful : 인바운드 정책과 아웃바운드 정책 중 어느 한쪽만 허용되어도 통신 가능
  - Stateless : 인바운드 정책과 아웃바운드 정책 모두 허용되어야 통신 가능
- Region 당 5개의 Elastic IP(공인IP)를 사용할 수 있음
- VPC 하나당 하나의 IGW만 가질 수 있음
- VPC Peering
  - VPC와 VPC를 연결하는 것
  - Region 내 VPC를 연결하거나 Region 간 VPC를 연결할 수 있음
  - 다른 계정간 VPC 연결 또한 가능
  - Star형 구조로 설정가능, 즉 하나의 중앙 VPC에 4개 VPC를 연결하는 것
- VPC를 생성할 때, 라우팅 테이블, ACL, Security group은 자동으로 생성됨
- 아무리 AZ가 같다하더라도 계정이 다르면 엄연히 다른 네트워크에 해당함 

#### **NAT Instance** 

- Private Subnet 내의 리소스가 외부 인터넷 통신이 가능하도록 Source IP NAT를 지원하는 인스턴스
- NAT 인스턴스를 생성할 때는 Source/Destination Check 설정을 Disable해야 함
- NAT 인스턴스는 반드시 Public Subnet에 존재해야 함
- Priavet Subnet에서는 반드시 NAT 인스턴스로 라우팅을 잡아주어야 함
- 인스턴스 사이즈에 따라 성능이 달라지므로 병목현상이 발생하면 인스턴스사이즈를 변경해주어야 함
- 인스턴스가 다운될 경우 혹은 부하가 많을 때를 대비하여 Autoscaling과 같은 기능을 같이 해주면 좋음

#### **NAT Gateway**

- NAT 인스턴스와 동일한 역할을 수행하는 서비스
- EC2 인스턴스를 이용한 NAT 인스턴스와 달리 하나의 서비스로 존재함
- AZ 내에 시스템 상의 이중화가 되어있음(고객 입장에서는 보이지 않음)
- 5Gbps에서 45Gbps까지 확장 가능함
- NAT 인스턴스와 달리패치가 필요 없음
- Security group의 영향을 받지 않음
- NAT 인스턴스와 마찬가지로 라우팅 테이블을 반드시 업데이트 해야함