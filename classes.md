# 객체지향프로그래밍 OOP

===

> 구조체(오브젝트)에 산재해 있는 데이터들을 의미 있는 데이터로 구조화 시켜서 프로그래밍 하니 동작보다는 데이터를 중심으로 코딩하게 되면
> **코드의 덩치가 커져도 일관성을 유지하기 편해짐** 즉 프로그래밍에서 필요한 데이터를 추상화 시켜서 **상태와 행위를 가진 객체**로 만들어서 객체들간의 상호작용을 통해 로직을 구성하는 방법

# Class

=====

> 그렇다면 구조체(오브젝트)에 항상 쓰이는 함수들을 하나로 묶어서 함께 함수까지 포함하는 개념을 만들게 되고 이를 **class**라고 하게됨

class Player {
constructor(
private firstName : string,
// private 자바스크립트에서 보이지 않음
private lastName :string,
private nickname:string  
 ){}
}

const gyu = new Player("gyu", "gwon", "규형")

# abstract 추상화

===

> 구조체 객체에서 상속 받을 수 있는 객체를 만드는 것 다만 이거는 새로운 객체를 만들 수는 없어
> 추상 메소드는 추상 클래스에서 상속받는 모든 것들이 구현을 해야 하는 메소드

abstract class User {
constructor(
protected firstName : string,
// private 자바스크립트에서 보이지 않음
protected lastName :string,
protected nickname:string  
 ){}
abstract getNickName():void
// method에도 private 이나 public이 가능함
getFullNmae (){
return console.log(`${this.firstName} ${this.lastName}`)
}
}
class Player extends User {
getNickName(){
console.log(this.nickname)
}
}

const gyu = new Player("gyu", "gwon", "규형")
// private 키워드는 TypeScript 클래스의 멤버 변수 또는 메서드를 선언할 때 사용되는 접근 제한자입니다. private로 선언된 멤버는 동일한 클래스 내에서만 접근할 수 있으며, 클래스 외부에서는 접근할 수 없습니다. gyu.private => 호출안됨

const gyu = new Player("gyu", "gwon", "규형")
// private 키워드는 TypeScript 클래스의 멤버 변수 또는 메서드를 선언할 때 사용되는 접근 제한자입니다. private로 선언된 멤버는 동일한 클래스 내에서만 접근할 수 있으며, 클래스 외부에서는 접근할 수 없습니다. gyu.private => 호출안됨
