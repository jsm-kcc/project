# partners-center
포들리 파트너스 센터 프로젝트

### COMMIT TAG 정의
- [INITIAL] - 레포지토리 최초 생성
- [ADD] - 신규파일 추가
- [UPDATE] - 코드수정
- [REFACTOR] - 코드개선
- [FIX] - 버그 수정
- [REMOVE] - 파일 제거


### Naming
1. 쉬운단어 선택.
2. 변수는 CamelCase를 기본.
 - userEmail, userCellPhone ...
3. URL, 파일명 등은 kebab-case 사용.
 - /user-email-page ...
4. 패키지명은 단어가 달라지더라도 무조건 소문자 사용.
 - frontend, useremail ...
5. ENUM이나 상수는 대문자로 네이밍.
 - NORMAL_STATUS ...
6. 함수명은 소문자로 시작하고 동사로 네이밍.
 - getUserId(), isNormal() ...
7. 클래스명은 명사로 작성하고 UpperCamelCase를 사용.
 - UserEmail, Address ...
8. 객체 이름을 함수 이름에 중복해서 넣지 않는다. (= 상위 이름을 하위 이름에 중복시키지 않는다.)
 - line.getLength() (O) / line.getLineLength() (X)
9. 컬렉션은 복수형을 사용하거나 컬렉션을 명시.
 - List ids, Map<User, Int> userToIdMap ...
10. 이중적인 의미를 가지는 단어는 지양.
 - event, design ...
11. 의도가 드러난다면 되도록 짧은 이름을 선택.
 - retreiveUser() (X) / getUser() (O)
단, 축약형을 선택하는 경우는 개발자의 의도가 명백히 전달되는 경우이다. 명백히 전달이 안된다면 축약형보다 서술형이 더 좋다.
12. 중복 기능의 함수일 경우 Or를 사용한다.
 - getOrder() (X) / getOrCreateOrder() (O)
13. 일자시간일경우 LocalDateTime -> xxxAt, 일자일겨우 LocalDate -> xxxDt로 네이밍
14. 가급적 view form element name과 도메인을 일치.

### Structure

1. 패키지는 목적별로 그룹.
 - user(User 관련 패키지), coupon(쿠폰 관련 패키지)
2. Controller에서는 최대한 어떤 Service를 호출할지 결정하는 역할과 Exception처리만을 담당.
3. Controller 단에서 로직을 구현을 최소.
4. 하나의 메소드와 클래스는 하나의 목적.
5. 하나의 메소드 안에서 한가지 일만 처리.
6. 하나의 클래스 안에서는 같은 목적을 둔 코드들의 집합.
7. 메소드와 클래스는 최대한 작게 코딩.
8. 메소드와 클래스가 커진다면 하나의 클래스나 메소드 안에서 여러 동작을 하고 있을 확률 높음.
9. 수많은 책임을 떠안은 클래스는 피함. 큰 클래스 몇 개가 아니라 작은 클래스 여럿으로 이뤄진 시스템이 더욱 바람직.
10. 도메인 서비스를 만들어지는 것을 피하자
User라는 도메인이 있을 때, UserService로 만드는 것을 금지.
기능별로 세분화 (UserRegisterService, UserEmailService 등...)

### Programming
1. 반복되는 코드를 작성 피함.
 - 단, 테스트코드는 예외.
2. 변수는 최대한 사용하는 위치에 가깝게 사용.
 -  파라미터 변수와 내부 변수를 구별할 땐 언더바가 아닌 this로 구별.
 - this.name = name (O) / name = _name (X)
3. 모든 예외는 무시하지말고 처리. 만약 예외를 처리하지 않을거라면 그 이유에 대해서 명확하게 주석처리.
 - 예외를 던질 때는 최대한 세부적인 Exception(= Custom Exception)을 작성.
4. 조건이 복잡한 경우 임시 boolean 변수를 만들어 단순화.
5. 조건문에 부정조건을 넣는 것을 피함.
 - if(status.isNormal()) (O) / if(!status.isAbnormal()) (X)
6. 최대한 객체 타입 대신 기본 자료형을 선택, 생각지도 못한 Autoboxing이 발생하지 않도록 유의.
