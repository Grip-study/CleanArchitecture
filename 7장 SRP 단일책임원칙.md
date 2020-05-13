# 7장 SRP 단일 책임 원칙

> 하나의 모듈은 변경의 이유가 하나, 오직 하나뿐이어야 한다. 
>
> 오직 하나의 액터에 대해서만 책임져야 한다.

<br>

### 단일 책임 원칙을 위반하는 징후들

#### 1. 우발적 중복

1-1. Emplyoee라는 클래스 안에 calculatePay, reportHours, save라는 메소드가 있는데, 
이 메소드를 각각 다른 세명의 액터가 책임지는 경우

=> Emplyoee라는 단일 클래스에 세개의 메서드가 결합되어 서로 의도치않은 영향을 줄 수 있다.

1-2. 코드 중복을 피하기위해 calculatePay, reportHours 메소드를 regularHours라는 메서드 안에 넣은 경우

=> 한쪽의 메소드가 수정된경우 다른한쪽의 메소드에서 의도치않은 결과를 얻을 수 있다.



#### 2. 병합

두명의 액터가 하나의 Emplyoee 클래스 코드를 동시에 수정할때 이들의 변경사항에 충돌이 발생한다. 결국 병합이 발생한다.



#### 3. 해결책

1-1. 메서드를 각기 다른 클래스로 이동시키는 방법.

=> 간단한 데이터 구조 클래스 EmplyoeeData를 만들어 세 개의 클래스가 공유하도록한다.

- class PayCalculator / func calculatePay
- class HourReporter / func reportHours
- class EmplyoeeSaver / func saveEmployee

각 클래스는 자신의 메서드에 필요한 소스코드만을 포함하며 서로의 존재를 몰라야한다. 이렇게 우연한 중복을 피할 수 있다.

1-2. 퍼사드 패턴

EmployeeFacade 클래스 생성

 => 위 세 클래스의 객체를 생성 및 소유

=> 요청된 메서드를 그것을 갖고있는 객체로 위임.

(퍼사드패턴 참고: https://jusungpark.tistory.com/23)





