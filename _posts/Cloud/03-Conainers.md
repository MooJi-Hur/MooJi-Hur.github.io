## Containers
- 어플리케이션을 만들기 위해 사용한 소스 및 라이브러리가 일관성 있게 실행되도록 구현한 기술

### Image
- 소스 코드, 사용자 수준의 커널 라이브러리, 설정 등을 담은 상자

### Container
- Image를 참조하여 만든 인스턴스
- 단일한 이미지에 여러 컨테이너 참조 가능

### Container Runtimes
- Docker는 컨테이너 런타임
- 네임스페이스와 cgroup로 추상화를 구현

#### Namespace
- 네트워크, 프로세스 ID와 같은 글로벌 시스템 자원을 격리하여 추상화
- `uts` UNIX time-sharing : 각 네임스페이스의 호스트 이름/도메인 
- `net` IP 주소

#### cgroups : control groups
- 프로세스 계층 구조와 분산 시스템 자원을 구성/설정

#### Union File System a.k.a. layer
- 분리되어있는 파일, 폴더 시스템을 층층이 쌓아서 가상의 파일 시스템 생성
- 컨테이너는 여러 레이어를 모아서 하나의 읽기 전용 파일 시스템을 만들어 일관성 유지
- 가장 위에 읽기-쓰기가 가능한 임시 레이어를 컨테이너에 만듦

### OCI : Open Container Initative
- 컨테이너 추상화 표준
- fork/exec 모델 요구
    - 프로세스를 복제fork한 뒤에는 실행exec해야 함

### Low Level Container Runtime

#### runC
- GO 언어로 구현하여 Thread 기반
- fork/exec 모델 구현을 위해 fork 후 즉시 실행

#### CRun
- row memory, low-level runtime
- 전통적인 UNIX 프로세스 모델
- C언어로 구현하여 fork/exec 모델이나, Multi-thread 미지원

### High Level Container Runtime
- 데몬 프로세스 (백그라운드 실행)로 지속적으로 컨테이너를 관리할 수 있음
- 컨테이너의 생애 주기를 관리

#### containered
- Docker는 Containered를 런타임으로 사용하고, runC를 기반으로 컨테이너를 관리

#### CRI-O 
- **C**ontainer **R**untime **I**nterface - **O**pen Container Initative
- 쿠버네티스는 컨테이너 런타임 인터페이스를 구현하여 현재는 Docker 대신 CRI-O를 사용