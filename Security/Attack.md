## Brute Force Attack
- `억지 기법(무차별 대입해 억지로 문제를 푸는)`이라 해석되며 아주 단순한 공격 기법이다.
- 특정 암호를 풀기 위해 임의의 문자의 조합을 하나씩 대입해 보는 공격 기법이다.

## Brute Force Attack 문자열 생성 및 대입 방법
  <ul>
    <li>무작위 순차 대입 : 조합 가능한 모든 문자열을 순차적으로 하나씩 모두 대입해 보는 것이다. 암호의 길이와 복잡도의 증가에 따라 공격에 걸리는 시간이 기하급수적으로 늘어나므로 무조건 성공한다고 보기 어렵다.</li>
    <li>사전(Dictionary) 대입 : 상당한 시간이 소요되는 무작위 순차 대입 방식 단점을 극복/보완하는 방법으로, 미리 정의된 문자열 목록을 대입하는 방법이다. 사전 파일을 이용한 공격이라고 해서 `사전 공격`이라고 한다. 미리 정의된 비밀번호 사전을 준비하여 하나씩 대입해 보는 방식이다. 사전 파일은 그동안 통계적으로 많이 사용되어 오거나, 사람들이 흔히 사용할법한 비밀번호 조합을 미리 목록 형태로 정의해 둔 파일이다.</li></ul>
