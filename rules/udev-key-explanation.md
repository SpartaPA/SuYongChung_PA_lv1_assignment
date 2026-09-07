# udev 규칙 키 설명

## 매칭 키 (조건)

| 키 | 뜻 | 예시 값 |
|---|---|--------|
| SUBSYSTEM== | 장치가 속한 분류 | block (블록 장치) |
| ATTR{loop/backing_file}== | loop 장치의 원본 이미지 경로 | /home/pa24/fake_sensors/lidar.img |

## 동작 키

| 키 | 뜻 | 예시 값 |
|---|---|--------|
| SYMLINK+= | 고정 심볼릭 링크 이름 추가 | robot_lidar |
| MODE= | 접근 권한 설정 | 0666 (누구나 읽기/쓰기) |
| GROUP= | 소유 그룹 설정 | dialout |

## 안정 키 선택 이유

ATTR{loop/backing_file}은 장치를 해제·재연결해도 값이 변하지 않는 안정 속성이다.
diskseq, KERNEL(loop 번호)은 재연결 시 바뀌므로 구분 키로 부적합하다.
