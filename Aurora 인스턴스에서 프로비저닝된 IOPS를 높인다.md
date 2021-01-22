## Aurora 인스턴스에서 프로비저닝된 IOPS를 높인다?

*  MySQL 및 PostgreSQL과 호환되는 완전 관리형 관계형 데이터베이스 엔진
* 기존 MySQL 및 PostgreSQL 데이터베이스에 사용되는 코드, 도구 및 애플리케이션 모두 Aurora에서도 사용가능
* 일부 워크로드의 경우 Aurora은 기존 애플리케이션을 거의 변경하지 않고도 MySQL의 처리량을 최대 5배, PostgreSQL의 처리량을 최대 3배 제공
* Aurora에는 고성능 스토리지 하위시스템이 포함
* MySQL 및 PostgreSQL과 호환되는 데이터베이스 엔진은 빠른 분산형 스토리지를 활용하도록 사용자 지정된다
*  기본 스토리지는 필요에 따라 자동으로 커질수 있따.
*  Aurora 클러스터는 최대 128 tebibytes (TiB) 크기까지 늘릴 수 있다. 
* Aurora는 또한 데이터베이스 구성 및 관리의 가장 어려운 측면 중 하나인 **데이터베이스 클러스터링 및 복제를 자동화하고 표준화**한다.
* Aurora은 관리형 데이터베이스 서비스 Amazon Relational Database Service(Amazon RDS)의 일부입니다.



---

#### * IOPS란? 

IOPS(Input/Output Operations Per Second, IOPS)는 HDD, SDD 또는 NVMe등 

**저장장치의 속도를 나타내는데 사용되는 측정 단위**이다. 

 MB/s, MiB/s 또는 GB/s, GiB/s 등과 같이 초당 전송량과 함께 많이 최근 들어 많이 사용되고 있는 단위

IOPS 측정값은 세부적으로 초당 전송량과 같이 **임의 접근(Random Acess)과 순차접근(Sequential Acess)**에 따라 다르고, **읽기 및 쓰기 동작**에 따라 다르다. 이외의 성능 측정 프로그램과 CPU 와 메모리에 상화에 따라 차이가 나게 측정된다.

![img](https://hiseon.me/wp-content/uploads/2019/06/random-and-sequential-access-1024x614.png)(출처 : 위키피디아)

순차 접근의 경우 데이터를 쓰거나 읽기 위해서 순차저적으로 접근하기 때문에 데이터 및 위치 검색 등의 오버헤드가 없어 속도가 빠르다.

하지만 임의 접근의 경우 데이터에 접근하기 위해서 추가적으로 접근, 검색하기 때문에 순차 접근과 비교했을 경우 속도가 많이 느린 것이 일반적.

Disk I/O 등 성능 측정과 관련해서는 다음을 참고==>**[리눅스 성능 측정 sysbench 사용법](https://hiseon.me/2019/06/01/linux-sysbench-examples/)**

---

### * IOPS 계산 방법

* 주어진 IOPS 값에서 **초당 데이터 전송량**을 계산하는 방법
  * **초당 데이터 전송량 =    IOPS   x     블럭크기(단위 데이터 용량)**
* 만약 블럭 크기 등 단위 데이터 용량에서 IOPS 를 계산하고싶다면?
  * **IOPS = 초당 데이터 전송량 / 블럭크기(단위 데이터 용량)**

블럭 크기인 단위 데이터 용량과 초당 데이터 전송량의 단위가 차이가 날 경우 추가 계산이 필요할 수 있다. 아래의 예제를 통해서 실제 계산 방법에 대해서 설명.

### IOPS 계산 예제

AWS에서 호스팅되고 있는 EBS 볼륨 유형의 IOPS 값을 이용하여, 이해하기 쉬운 초당 전송량을 계산해보자.

**[Amazon EBS 볼륨 유형](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/EBSVolumeTypes.html)**

![IOPS 계산 방법](https://hiseon.me/wp-content/uploads/2019/06/aws-ebs-types.png)

위에서 나타나 있는 최대 IOPS 값에서 범용 SSD(gp2) 값의 16,000 IOPS 가 초당 얼마만큼의 데이터를 전송 할 수 있는지 계산해보자.

IOPS 값에서 초당 전송량을 계산하기 위해서는, IOPS 수치가 나타내는 단위 크기의 값을 알아야한다.

![IOPS 계산 방법](https://hiseon.me/wp-content/uploads/2019/06/aws-block-size.png)

같은 페이지에 IOPS 블럭 크기가 나와있다.

SSD(gp2) 가 16KiB 이기 때문 이 값을 이용하여 계산해 보도면 다음과 같이 최대 처리량(초당 데이터 전송률)250MiB/s (256,000 KiB/s) 으로 계산된다.

**16,000 IOPS \* 16KiB = 256000 KiB/s = 256000 / 1024 = 250MiB/s**

출처: https://hiseon.me/server/iops-calculator/