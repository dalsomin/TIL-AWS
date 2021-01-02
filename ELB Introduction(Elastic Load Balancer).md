#### **ELB Introduction(Elastic Load Balancer)**

- EC2 인스턴스로 트래픽을 부하분산하는 서비스
- 리스너와 대상그룹으로 이루어짐
- 리스너는 부하 분산을 실시할 포트를 설정하며, 대상그룹엔 부하 분산 대상인 서버들이 탑재되어 있음
- 인스턴스는 다수의 AZ에 분산 배치 가능
- 다수의 Region에 부하분산하려면 Route 53을 추가로 이용해야 함
- ELB의 종류 : ALB, NLB, CLB
  - ALB(Application Load Balancer) : Layer 7 Protocol인 HTTP, HTTPS 트래픽을 부하분산하기 위한 로드밸런서
  - NLB(Network Load Balancer) : Layer 4 Protocol의 트래픽을 부하분산하기 위한 서비스, Direct Connect를 이용하여 On-premise에 있는 Resource 부하분산 가능
  - CLB(Classic Load Balancer) : 과거 EC2-Classic이 있던 시절의 로드 밸런서로, HTTP/HTTPS 트래픽을 부하분산하기 위한 로드 밸런서. 사용이 추천되지 않음
- ELB Health check : 부하분산 대상이 되는 서버들의 상태를 체크하기 위한 기능, HTTP/HTTPS/TCP로 상태를 확인하며 상태 체크 주기, 비정상으로 판단하기 위한 상태 체크 횟수 등을 정함
  - 상태 체크 확인에 실패하면 ELB는 자동으로 해당 서버를 부하 분산 대상에서 제외하고 트래픽을 보내지 않음(중요!!)
- 외부 인터넷 트래픽을 처리할 수 있는 Internet-Facing Load Balancer, 내부 트래픽을 처리하는 Internal Load Balancer로 나뉨
  - 생성시 설정 가능



![img](https://blog.kakaocdn.net/dn/INq9K/btqIs8nyc82/mJvfRvjbvwyaegLbmOY1e0/img.jpg)<Internet-Facing Load Balancer(출처 : Rick Crisci ANS 강의)>



 



![img](https://blog.kakaocdn.net/dn/cRzBsh/btqIs8Vu3JT/q0oxT4X6Mo8D06kDMuTwe1/img.jpg)<Internal Load Balancer(출처 : Rick Crisci ANS 강의)>



#### **ALB Listener and HTTPS(SSL Offload)**

- ELB의 HTTPS 리스너는 HTTPS로 암호화(443)된 패킷을 복호화(80)하여 서버로 보냄
- 리스너의 포트는 443이어야하지만, 대상그룹의 포트는 80으로 설정되어야 함
- 이 기능을 사용하기 위해서는 SSL 인증서가 ELB에 탑재되어야 함
- AWS Certificate Manager(ACM) 또한 인증서 생성 가능
- 다수의 도메인(다수의 IP)을 위한 멀티 인증서 사용 가능
- ALB의 리스너는 규칙 작업과 규칙 조건을 가질 수 있으며, 조건에 따라 행동 규칙을 정할 수 있음
- 규칙 : 리스너가 정의한 규칙에 따라 로드밸런서가 하나 이상의 대상 그룹에서 대상으로 요청을 라우팅함. 각 리스너는 기본 규칙을 가지며, 선택적으로 추가 규칙 정의 가능
  - 기본 규칙은 삭제가 불가능하고 조건을 가질 수 없으며 다수의 규칙이 존재할 때 가장 마지막에 적용됨
  - 각 규칙은 우선 순위와 하나 이상의 조건, 하나 이상의 작업으로 구성됨
- 규칙 작업 : 작업을 수행하는 데 필요한 유형, 순서 및 정보
  - Forward : 요청을 지정한 '대상 그룹'으로 전달
  - Redirect : URL의 요청을 다른 URL로 변경하여 전달, 즉 요청된 URL이 아닌 다른 URL을 요청하는 것으로 바뀜
  - Fixed-response : 사용자가 지정한 HTTP Response를 반환, 즉 200을 포함하여 2XX, 4XX, 5XX 응답코드와 메시지 반환 가능
- 규칙 조건 : 작업을 수행할 규칙에 대한 조건 충족
  - Host-header : 도메인 이름을 기반으로 라우팅
  - HTTP-header : 각 요청의 HTTP Header를 기반으로 라우팅
  - Source-ip : 각 요청의 소스 IP 주소를 기반으로 라우팅

#### **AWS ELB Target Group**

- EC2 인스턴스 ID를 이용하여 로드밸런싱하거나 IP 주소를 이용하여 로드밸런싱 가능
- Lambda Function으로 로드밸런싱 가능
- 상태 체크가 확인된 인스턴스에게 로드밸런싱함
- 다른 포트를 사용한다면 같은 인스턴스를 여러번 등록할 수 있음
- AutoScaling와 연동하여 Target Group의 Scale up/down 가능
- Sticky Session : Cookie를 활용해 요청을 수행했던 서버로 재연결 가능
  - NLB의 경우 Source IP를 활용하여 Sticky Session 기능 실시
  - TLS 리스너/대상그룹은 사용할 수 없음

#### **ALB의 Host and Path Contidtion**

- Host Condition : [example.com,](http://example.com%2C/) dev.example.com, test.example.com 등 도메인 이름을 기반으로 로드밸런싱
- Path Condition : 도메인의 경로를 이용한 로드밸런싱. 예를 들어 '/img/*'이 포함된 요청은 지정된 Target Group으로 보냄

#### **Connection Draining**

- 종료될 인스턴스에 요청 전달을 중단하고 수행중인 요청을 방해 없이 완료한 후 인스턴스 종료
- 1초 ~ 3600초까지 설정 가능
- AutoScaling은 인스턴스를 종료시키기 전에 Connection Draining을 기다림
- Connection Draining Enable/Disable 가능
- ALB, CLB 지원

#### **AWS ELB X-Forwarded-For**

- Client IP를 보존해주는 기능인 X-Forwared-For를 ALB, CLB가 지원
- 기본활성화이기에 활성화시킬 필요 없음