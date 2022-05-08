## 1. 목적

https://www.google.com/ 접속 시 웹 통신 흐름 파악하기

---

## 2. 내용

웹통신 흐름을 이해하기 위해서는 우선 OSI를 알아야한다.

### 2.1 OSI(Open System Interconnection)

컴퓨터가 데이터를 어떻게 주고 받는지 구조화한 것.

![OSI](Images/OSI.png)

- Layer 7: Application  
  애플리케이션 레이어는 유저와 직접적으로 상호작용하는 계층이다. 즉 우리가 사용하는 브라우저(크롬, 사파리, 파이어폭스)다.
  -> google.com을 클릭하면 -> 브라우저는 request를 보낼 web server를 선택한다. -> server에서 response가 도착하면 브라우저에 보여준다.
- Layer 6: Presentation  
  데이터를 캡슐화(Encapsulation)하고 암호화(Encryption)/해독, 압축/압축을 푸는 계층이다.
  -> 서로 다른 데이터 구문(syntax)을 Mapping한다. -> 애플리케이션과 네트워크 사이에 다른 format을 번역한다.
  -> 또다른 기능으로는 데이터를 캡슐화하고 압축한다.
  -> 인간들의 언어(HTML, XML, ASCII, GIF, JPG, MPG, MOV, WMV, SSL, TLS)를 -> 컴퓨터 언어(2진수)로 변환해주거나 그 역방향도 마찬가지다.
  -> SSL를 사용해서 암호화(Encryption)도 한다.
  -> 그림을 이진수로 표현하는 방법
  ![picturePexel](Images/picturePexel.png)
- Layer 5: Session  
  호스트간 통신을 연결해준다.
  -> 두 컴퓨터간 세션을 establish하고 manage하고, terminate한다.
  -> 우리가 어떤 웹사이트를 방문할 때 session을 웹서버와 생성한다. -> 브라우저에서 웹 페이지 request를 웹서버로 보내면 브라우저는 TCP/UDP 연결을 하고 -> 웹 서버는 요청한 웹 페이지를 다시 브라우저로 보내고 연결을 닫는다 -> 각 TCP/UDP가 session이다.
- Layer 4: Transport
  End to End(종단)간 통신과 신뢰성을 보장해준다.
  -> 호스트간 통신 서비스를 제공한다. -> 데이터를 프로세스에 전달한다. -> 또한 데이터의양, 속도, 동작등을 조정한다.-> 2개의 중요한 프로토콜이 있다.
  -> TCP(Transmission Control Protocol)과 UDP(User Datagram Protocol)이다.
  - TCP 프로토콜
    TCP가 원래는 IP네트워크를 통해서 End to End로 데이터를 전송하는 용어로 단독으로 쓰였다.
    -> 그 이후에 TCP/IP 가 함께 쓰이기 시작 해서 OSI 모델과 같은 전체 네트워크 모델을 나타내는 용어로 쓰이고 있다.
    ![TcpIpModel](Images/TcpIpModel.png)
    1. Connetion-oriented(연결지향적): 상호간에 통신을 하기 위해서 3 way handshaking을 한다.
    2. Reliable(신뢰할수 있는): 데이터의 올바른 순서와 무결성(Integrity)을 보장한다. 순서가 맞지 않거나 데이터가 중간에 손실되면 서버는 재요청 한다.
  - UDP 프로토콜  
    신뢰성 보다는 속도에 무게감을 두는 프로토콜이다.
    1. Connectionless communication: 비연결형 모델이다. 데이터가 사전 협의 없이(handshaking) 전송된다.
    2. No care about packet order and lost: 중간에 손실되거나 순서가 뒤죽박죽되더라도 신경쓰지 않는다.
    3. Less computer resources: 그래서 컴퓨터 자원을 더 소모 시킨다.
    4. Sutable for streaming media and real-time apps: 에러체킹이나 수정이 필요하지 않는 Apps에 적절한 프로토콜
    5. Sutable for simple query-response protocol: DNS같은 단순 쿼리 응답(빠르고, 하나의요청, 하나의응답) 프로토콜에 적절하다.
    6. Sutable for modeling other protocols: 다른 프로토콜 모델링에 적합. **예를들어 IP tunneling 또는 Remote Procedure Call**
- Layer 3: Network Layer  
  경로를 결정하고 논리적 주소를 지정해준다.  
  -> 가능한 Several 프록시(네트워크)를 통해서 소스부터 목적지까지 가변길이의 네트워크 패킷을 전송해주는 역할을 한다.  
  -> 라우터가 중요한 역할을 한다.-> 스위치로 구성된 네트워크를 연결한다. -> 여기서 중요한 프로토콜은 IP이다.
  1. IP: 고유한 주소를 제공하고, 비연결형, 라우팅, 유니캐스트/브로드캐스트/멀티캐스트를 제공한다. -> IP 주소가 고유하다는 것이 중요하다.
  2. Router/Gateway: 네트워크간 패킷을 전달하는 역할을 한다. -> 광역 네트워크 통신을 위해 많은 네트워크가 서브네트워클 쪼개지고 다른 네트워크와 연결되기 때문에 라우터가 필요하다.
  3. **Sending a Packet to Router: 목적지의 IP주소와 MAC주소를 알고 있으면 데이터를 보낼 수 있다. -> 소스와 목적지가 동일한 IP 도메인으로부터 오지 않았다면, 소스는 데이터를 라우터로 먼저 보낸다.**
- Layer 2: Data Link  
  물리적 주소를 지정한다.  
  -> 데이터가 비트 프레임으로 디코딩된다.-> Physical layer의 에러를 관리 및 처리한다. -> 2개의 서브 층이 더 있다. -> Medium Access Control (MAC) layer과 Logical Link Control (LLC) layer 계층이다.
  1. MAC: 컴퓨터 하드웨가 데이터에 접근하고 데이터를 보내는 것을 컨트롤한다. -> MAX 주소는 네트워크 세그먼트 안에서 통신하는 장치의 고유한 식별자다. -> Wi-Fi, Bluetooth, Ethernet 같은 기술을 위한 네트워크 주소로 사용된다.(3A-34–52-C4–69-B8처럼 생김)
  2. LLC: MAC서브레이어와 Network 레이어 사이에 인터페이스로 활동한다.-> 프레임 동기화, 흐름제어, 에러 체킹을 컨트롤한다.
  3. Network Switch: 스위치는 컴퓨터 네트워크 장치다. -> 하드에워 주소(MAC주소)를 사용하여 데이터를 처리하고 전달한다. -> port to port와 버퍼링 서비스를 지원한다.
- Layer 1: Physical
  미디어, 시그널, 바이너리 전송을 담당한다.  
  -> raw data가 네트워크를 통해서 비트 0과 1의 형태로 전송되는 곳이다. ->전기적, 기계적, radio waves(전파)의 형태다.

---

## 3. 정리

URL을 클릭하면 브라우저는 그 클릭 이벤트를 request로 해석하고 -> OSI 모델로 보낸다. -> 네트워크를 지나서 각 Layer를 거슬러 올라가 response가 도착하기 전에, 데이터가 수신되고 처리되는 서버의 계층으로 올라간다.
