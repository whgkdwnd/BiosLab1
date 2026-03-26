# 작업된 파일 목록 및 역할

Git 커밋 기록을 기반으로 사용자가 수정한 파일 목록과 각 파일의 역할입니다.

### README 및 문서
- `README.md`: 프로젝트 전반에 대한 설명과 과제 1의 진행 상황이 업데이트되었습니다.

### 빌드 설정
- `xv6edk2/xv6/Makefile`: 새로운 사용자 프로그램(`_student_id`, `_test_wait`)을 빌드 대상에 추가하고, 컴파일 규칙을 수정했습니다.

### 사용자 프로그램 (User Space)
- `xv6edk2/xv6/studentid.c`: 학번을 출력하는 간단한 사용자 프로그램 소스 코드입니다.
- `xv6edk2/xv6/testwait.c`: 상태 코드를 인자로 받는 `exit2`와 이를 받아오는 `wait2` 시스템 호출을 테스트하기 위한 프로그램입니다.
- `xv6edk2/xv6/_student_id`: `studentid.c`가 컴파일된 실행 파일입니다.
- `xv6edk2/xv6/_test_wait`: `testwait.c`가 컴파일된 실행 파일입니다.
- `xv6edk2/xv6/user.h`: 사용자 공간에서 호출할 수 있는 `exit2`와 `wait2` 시스템 호출의 함수 원형을 추가했습니다.
- `xv6edk2/xv6/usys.S`: 시스템 호출을 위한 어셈블리 스텁(SYSCALL_STUB)을 추가했습니다.

### 커널 내부 구현 (Kernel Space)
- `xv6edk2/xv6/proc.h`: 프로세스 구조체(`struct proc`)에 종료 상태 값을 저장할 `xstate` 필드를 추가했습니다.
- `xv6edk2/xv6/proc.c`: 상태 코드를 저장하며 종료하는 `exit2()`와, 자식 프로세스의 상태 코드를 읽어오는 `wait2()`의 실제 커널 로직을 구현했습니다.
- `xv6edk2/xv6/defs.h`: 커널 내부에서 사용되는 `exit2`와 `wait2` 함수의 원형을 정의했습니다.
- `xv6edk2/xv6/syscall.h`: 새로운 시스템 호출 번호(`SYS_exit2`, `SYS_wait2`)를 정의했습니다.
- `xv6edk2/xv6/syscall.c`: 시스템 호출 테이블에 `exit2`와 `wait2`를 등록했습니다.
- `xv6edk2/xv6/sysproc.c`: 사용자 공간의 인자를 커널 함수로 전달하는 시스템 호출 래퍼(`sys_exit2`, `sys_wait2`)를 구현했습니다.
