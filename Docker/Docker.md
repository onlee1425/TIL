## 도커(Docker)란?
- 도커는 컨테이너 기반 가상화 플랫폼으로, 애플리케이션과 그 의존성을 격리된 환경에서 실행할 수 있게 해주는 오픈 소스 기술이다. 도커를 사용하여 운영체제 수준에서 가상화를 통해 애플리케이션을 패키징하고 실행할 수 있다.

## 가상화(Virtualization) 기술이란?
- 하나의 물리적인 컴퓨터 자원(CPU,메모리,저장장치 등)을 가상적으로 분할하여 여러 개의 가상 컴퓨터 환경을 만들어 내는 기술이다. 이를 통해 물리적인 컴퓨터 자원을 더욱 효율적으로 사용할 수 있으며, 서버나 애플리케이션 등을 운영하는데 있어 유연성과 안정성을 제공한다.

## 가상화의 종류
1. **하드웨어 가상화** :
   이는 하나의 물리적 서버에서 여러 개의 가상 서버를 생성하는 기술로, 각 가상 서버는 독립된 운영체제와 애플리케이션을 실행할 수 있다. 하드웨어 가상화는 가상 머신(Virtual Machine, VM)이라는 단위로 이루어지며, Hypervisor라는 소프트웨어가 이를 관리한다.


2. **컨테이너 가상화** :
   컨테이너는 하드웨어 가상화보다 가볍고 빠르게 동작한다. 컨테이너는 호스트 시스템의 운영체제를 공유하면서 격리된 환경에서 실행된다. 이는 하나의 운영체제에서 여러 컨테이너를 실행할 수 있도록 해주는데, 이러한 격리는 리눅스의 네임스페이스와 컨트롤 그룹을 이용하여 이루어진다.

![](https://lh6.googleusercontent.com/HWd2a3foV81WcdrNub4Q_B265GamwqAFSniZyLqErj9yzsnQWvPqkKMbKExaSEpJLm9L_qCItPSv7kUWL26AcXU9BZprZikZV0D76bTSU7hSYLyR2AuHj_ZioNJX6NgkTHDyhCiM)

## 도커의 특징
- **가볍고 빠른 실행** : 도커는 가상 머신보다 가볍고 빠르게 동작하는 컨테이너를 사용해 애플리케이션을 실행한다.
- **이식성과 확장성** : 컨테이너는 환경에 독립적으로 실행되며, 쉽게 이동하고 확장할 수 있다.
- **이미지 기반 패키징** : 애플리케이션과 환경을 이미지로 패키징하여 배포하며, 일관성과 효율성을 유지한다.
- **자동화된 배포** : 애플리케이션을 컨테이너로 패키징하고 배포하는 과정을 자동화하여 효율적인 CI/CD를 가능하게 한다.
- **리소스 효율성** : 호스트 시스템의 커널을 공유함으로써 자원 사용을 최적화하고 더 많은 애플리케이션을 실행할 수 있다.

## 도커의 구성(Architecture)
1. 도커 데몬
2. 도커 클라이언트
3. 도커 오브젝트
   - 도커 이미지
   - 도커 컨테이너
4. 도커 레지스트리