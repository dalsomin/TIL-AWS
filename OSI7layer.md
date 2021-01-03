#### **OSI 7 Layer**

> OSI 모형(Open Systems Interconnection Reference Model)은 국제표준화기구 (ISO)에서 개발한 모델로, 컴퓨터 네트워크 프로토콜 디자인과 통신을 계층으로 나누어 설명한 것이다. 일반적으로 OSI 7 계층 모형이라고 한다. 이 모델은 프로토콜을 기능별로 나눈 것이다. 각 계층은 하위 계층의 기능만을 이용하고, 상위 계층에게 기능을 제공한다.
>
> '프로토콜 스택' 혹은 '스택'은 이러한 계층들로 구성되는 프로토콜 시스템이 구현된 시스템을 가리키는데, 프로토콜 스택은 하드웨어나 소프트웨어 혹은 둘의 혼합으로 구현될 수 있다. 일반적으로 하위 계층들은 하드웨어로, 상위 계층들은 소프트웨어로 구현된다.
>
> 출처 : 위키백과

 



![img](https://blog.kakaocdn.net/dn/bNSsm2/btqDn2e8YWr/TY4y7KUTebPKedIdkusiO1/img.jpg)<OSI 7 Layer(출처 : https://shlee0882.tistory.com/110)>



네트워크 통신 시 송신자와 수신자가 지켜야 할 각 단계의 규칙을 뜻하며, 위로 갈수록 Application에 가까워지며(실제 프로그램) 아래로 내려갈수록 Cable(물리적 연결구간)에 가까워집니다. 또한 아래로 내려 갈수록 Protocol Header가 추가되어 계층 정보(TCP, IP, MAC 등)를 덧붙입니다. 계층을 나눈 이유는 장애 발생 시 어느 구간이 발생하였는지 보다 명확하게 알기 위함입니다. 필수로 이해해야 할 각 단계를 설명하겠습니다.

 

**Application Layer(7 Layer)**

사용자가 UI로 접하는 응용 프로그램과 관련된 계층으로 HTTP,FTP,DHCP,SMTP,DNS 등이 있습니다. 여기에 속한 프로토콜들은 어떠한 방법으로든 사용자와 직접 접하게 됩니다.

(Data + HTTP Header)

 

**Transport Layer(4 Layer)**

송신자와 수신자의 논리적 연결(Connection)을 담당하는 부분으로, 신뢰성 있는 연결을 유지할 수 있도록 도와줍니다. 즉 endpoint(사용자) 간의 연결을 생성하고 데이터를 얼마나 보냈는지 얼마나 받았는지, 제대로 받았는지 등을 확인합니다. TCP와 UDP가 대표적입니다.

(Data + HTTP Header + TCP Header)

 

**Network Layer(3 Layer)**

**IP(Internet Protocol)**이 활용되는 부분으로, 한 endpoint가 다른 endpoint로 가고자 할 경우, 경로와 목적지를 찾아줍니다. 이를 **Routing**이라고 하며 대역이 다른 IP들이 목적지를 향해 제대로 찾아갈 수 있도록 돕는 역할을 합니다.

(Data + HTTP Header + TCP Header + IP Header)

 

**DataLink Layer(2 Layer)**

같은 네트워크 대역을 사용하는 단말들에 대해 신뢰성 있는 전송을 보장합니다. 즉 '**MAC address**'를 활용하여 같은 구간 내의 endpoint 혹은 Switching 장비에 전달하며, 1 Layer에 해당하는 물리 계층에 생길 수 있는 오류를 찾아냅니다.

(Data + HTTP Header + TCP Header + IP Header + Ethernetframe Header)

 

**Physical Layer(1 Layer)**

**'Cable**'로 대표되는 물리적인 계층으로 전기적 신호가 전송되는 구간입니다.

 

여기까지가 OSI 7 Layer의 정의입니다. 정의만 봐서는 이해가 쉽지 않죠? 이를 좀 더 풀어서 설명해보겠습니다.

 

#### **택배 전달 과정**

요즘 택배/온라인 쇼핑몰 업계가 호황이라고 합니다. 로나로나 코로나의 여파로 사람들이 집 밖에 나가길 꺼려하니 생필품을 대부분 온라인 주문한다고 하네요. 그러다 보니 주문량이 폭주할 수밖에 없다고 합니다. 왜 갑자기 택배 이야기냐고요? OSI 7 Layer와 체계가 매우 흡사하기 때문입니다 ^____^

 



![img](https://blog.kakaocdn.net/dn/byzmgp/btqDofZC98x/l3F5ghfoIbOxntFkLQ2Ps0/img.png)<너네집까지 택배가 닿는 과정>



**야탑동에 살고 있는 저는 정자동에 살고 있는 제 지인에게 회사 업무 관련 문서가 담긴 택배를 정자동에 보내려고 합니다.**

(**IP Address는 '야탑동 우리집','정자동 너네집', '택배센터'로, MAC Address는 \**'번지'\**로 정합니다.**)

 

저는 야탑동 우리집, 100번지에서 회사 공식 업무 문서를 회사 문서 내규에 의거하여 문서 1,2,3,4,5를 작성하였습니다. 그리고 정자동 수신자(정자동 너네집, 400번지)에게 택배를 받게 되면 꼭 연락해서 수신 확인을 받고 연달아 나머지 문서도 받고 수신 확인도 받으라고 '**쪽지**'도 적어 문서와 함께 택배 상자에 동봉합니다.

 

택배 상자에 담은 뒤 **출발지**를 '야탑동 우리 집, 야탑동 100번지'로 적고, **목적지**를 '정자동 너네 집, 야탑동 200번지'로 설정합니다.(제1택배센터의 주소는 야탑동 200번지) 그리고 두 발로 제1 택배센터까지 걸어가 전달을 요청했습니다. 

 

제1택배센터(야탑동 200번지)는 택배 상자를 받고 주소를 확인합니다. **'**정자동 너네 집'으로 가기 위해서는 제2택배센터로 가야 함을 알게 됩니다. 그리고 택배 상자에 적힌 출발지, 목적지 중 '야탑동 100번지, 야탑동 200번지'를 지웁니다. 그리고 '서현동 100번지', ' 서현동 200번지'로 변경합니다. 번지만 바꾸는 이유는 실제 목적지는 그대로 남겨두고 그곳으로 향하되, 중간 경로(제2택배센터)로 이동하기 위함입니다. 똑같은 과정을 반복하여 '정자동 너네 집, 정자동 400번지'에 도달합니다.

 

수신자는 '정자동 400번지'를 확인한 후, 목적지 주소인 '정자동 너네집'을 확인하게 되며 택배 상자를 뜯고 '**쪽지**'를 확인한 후 송신자에게 전화를 걸어 택배를 받았음을 알리고 회사 공식 문서 내용를 확인합니다. 그리고 동일한 방법으로 문서 2,3,4,5도 받고 놓친 문서가 없는지 확인한 후 문서 내용을 확인합니다. 

 

#### **데이터 전달 과정(OSI 7 Layer)**

위의 택배 전달 과장을 OSI 7 Layer로 변형하여 설명해보겠습니다. 호칭만 바뀌었지 구조는 완전 동일합니다.

 



![img](https://blog.kakaocdn.net/dn/OnP8A/btqDkAkhRvL/qYaw12DvEorw6VL5LOZB7k/img.png)<너의 컴퓨터까지 데이터가 닿는 과정>



**IP주소가 10.10.1.1/24인 저는 다른 네트워크(10.10.4.2/24)에 있는 제 지인의 컴퓨터에 HTTP로 이루어진 웹페이지를 전달하려고 합니다.**

 

HTTP에 의거하여 규칙에 맞게 웹페이지 1,2,3,4,5를 작성하고 관련 정보를 HTTP Header에 담습니다.

(Data + HTTP Header, Application Layer)

 

그리고 Your Computer(10.10.4.2)에게 TCP에 의거하여 '3-Way Handshake'를 통해 신뢰할 수 있는 Session을 생성한 후, 웹페이지 수신마다 확인을 해줄 것을 요청하였습니다. 또한 TCP 관련 정보를 TCP Header에 담습니다.

(Data + HTTP Header + TCP Header, TCP Layer)

 

IP 정보를 담은 IP Header를 추가로 설정한 뒤, Source IP(10.10.1.1)와 Destination IP(10.10.4.2)를 지정합니다. Address Translation이 적용되지 않는 한, 이 정보는 변하지 않습니다. 

(Data + HTTP Header + TCP Header + IP Header, Network Layer)

 

같은 네트워크 대역에서는 IP Address가 아닌 MAC Address를 이용하여 통신 및 패킷을 이동시킵니다. Ethernet Frame Header를 추가하여 MAC Address, 오류 검출 등의 관련 정보를 담습니다. 또한 MAC Address는 Source, Destination에 따라 수시로 변경됩니다.

(Data + HTTP Header + TCP Header + IP Header + Ethernet Frame Header)

 

데이터가 전기적 신호로 변하여 UTP Cable을 타고 Router 1, Router 2, Router 3 등을 지나갑니다.

 

(데이터가 수신자에게 이동 중....)

 

수신자는 Router 3으로부터 이 데이터를 받은 후 **Ethernet Frame Header**를 보고 Destination MAC이 자신이 맞는 것을 확인합니다. 그리고 **IP Header**를 확인하여 Destination IP가 자신이 맞음을 확인합니다. 그리고 **TCP Header**를 확인하고 신뢰성 있는 연결이 필요하다는 것을 알게되고 '3-way Handshake'를 실시하여 10.10.1.1과 패킷을 주고 받으며 Session을 생성합니다. 마지막으로 **HTTP Header**를 확인하고 HTTP로 작성되었음을 알고 Data를 확인합니다.