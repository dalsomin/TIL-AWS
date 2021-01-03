 

#### **SQS(Simple Queue Service)**

- 메시지 큐 서비스(Push가 아닌 Pull 기반 서비스)
- 서비스 요청을 저장하고 대기열을 만들어 처리할 수 있도록 하는 서비스
- 각 컴포넌트들을 분할하여 독립적으로 운영하게 함으로써 한 서비스가 실패할 경우에도 서비스 요청을 보존할 수 있게 함
- 열람중에 서비스가 처리되면 사라지지만 처리되지 않으면 다른 열람자가 읽을 수 있도록 보존됨
- 각 메시지는 최대 256KB의 텍스트로 구성될 수 있음
- 1분 ~ 14일간 저장가능하지만 Default 값은 4일임
- Standard Queues : 표준 서비스로 초당 무제한에 가까운 요청을 처리할 수 있으며 최소 한 번 처리를 보장하나 순서는 보장하지 않음. 그러나 중복으로 처리될 수 있음
- FIFO Queues : 선입선출, 순서를 정확히 지켜 처리함, 초당 300개로 제한됨

#### **SNS(Simple Notification Service)**

- Notification를 통보하는 서비스로 애플, 구글, 파이어폭스, 윈도우 디바이스 등에 알림을 보낼 수 있음
- SQS와는 다르게 Push Base 서비스



#### **Elastic Load Balancer(ELB)**

- 부하 분산 서비스, 로드밸런서, L4 스위치에 해당하는 서비스 
- Application Load Balancer(ALB) : HTTP, HTTPS에 특화된 Load Balancer
- Network Load balacner(NLB) : TCP에 특화된 Load Balancer
- Classic Load balancer(CLB) : ALB, NLB가 나오기 전의 Load Balancer
  - HTTP, HTTPS와 Sticky, X-Forwared-For 같은 특정 기능 사용 가능
- DNS A 레코드가 자동으로 할당되기 때문에 IP를 할당할 필요 없음
- Sticky Session : 특정 EC2에 세션이 고정되도록 해주는 기능
- Cross Zone Load Balancing : 가용영역(AZ) Load Balancing이 아닌 인스턴스 개체 수를 기준으로 Load Balancing함
  - 가용영역별(AZ)로 한 이후 ELB가 자신의 가용영역이 아닌 다른 가용영역의 Pool member에 Load Balancing함

 