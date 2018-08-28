# Mutex Locks
앞서 설명한 해결책은 솔직히 너무 복잡할 뿐 아니라 응용 프로그래머가 사용할 수 없다. 때문에 운영체제 설계자들은 임계구역 문제를 해결하기 위한 소프트웨어 도구들을 개발하는데 그중 가장 간단한 도구가 바로 mutex lock이다.
***

## Mutex Locks
* mutex는 mutual exclusion(상호 배제)의 약어이다.
* 프로세스는 임계구역에 들어가기 전 lock을 하고 나올 때 lock을 반환한다.
* acquire 함수가 락을 획득, release 함수가 락을 반환한다.
* mutex lock은 available이라는 boolean형 변수를 하나 가진다.
    * 이 값이 lock의 사용 여부를 나타낸다.
* mutex lock의 함수 호출은 원자적으로 수행되야 한다.
* 이 방식의 단점은 busy waiting을 한다는 것 이다.
    * 임계구역에 들어가길 원하는 프로세스들은 acquire함수 안에서 루프를 돌고있다.
    * 때문에 spinlock이라고 부른다.
    * test_and_set이나 compare_and_swap 명령어 에서도 동일한 문제가 발생한다.
    * 락을 기다리는 동안 context switch를 하지 않는것이 spinlock의 장점이다.