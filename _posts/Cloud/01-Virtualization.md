## 가상화
- 컴퓨팅 자원을 소프트웨어로 제어하여 가상 시스템 생성

### Cloud Computing
- 원격으로 컴퓨팅 자원 관리 및 사용

### Virture Machine
- 하드웨어 컴퓨터 자원을 운영 환경 소프트웨어로 만듦
- Hypervisor 가상화 소프트웨어를 호스트 머신에 설치
- 가상 운영 환경을 독립적으로 사용 가능

#### 유형
- Type1 : Native or Bare-metal Hypervisor
    - 호스트 머신 하드웨어에서 바로 실행하는 Hypervisor

- Type2 : Hosted Hypervisor
    - 호스트 머신의 OS 위에서 실행

- KVM : Kernel-based Virtual Machine
    - Type 1, 2의 역할을 하는 리눅스 커널 모듈

### Kernel-based Virtual Machine
- Full virtualization solution for Linux on x86
- 리눅스 커널을 게스트 가상 머신을 관리할 수 있는 Hypervisor로 사용
- x86 하드웨어 용으로 설계되었지만, 현재는 다른 프로세서에도 포팅이 가능


#### 구조
- **KVM Guest**
    - Applications
    - KVM Guest's kernel
    - Vertual CPUs  ... <-> **Hardware Emulation**

- **Linux Kernel**
    - KVM   ... <->iothread <-> **Hardware Emulation**
    - File system and Block Devices
    - Physical Drivers

- **Hardware**
    - CPUs
    - Disks

