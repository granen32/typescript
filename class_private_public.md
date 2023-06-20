# class_private

===

> private 키워드는 TypeScript 클래스의 멤버 변수 또는 메서드를 선언할 때 사용되는 접근 제한자입니다. private로 선언된 멤버는 동일한 클래스 내에서만 접근할 수 있으며, 클래스 외부에서는 접근할 수 없다.

class MyClass {
private myPrivateVariable: number;

constructor() {
this.myPrivateVariable = 10;
}

private myPrivateMethod(): void {
console.log("This is a private method.");
}

public myPublicMethod(): void {
this.myPrivateMethod(); // private 메서드 내부에서 호출 가능
console.log("This is a public method.");
}
}

const myObject = new MyClass();
myObject.myPublicMethod(); // This is a private method.
// This is a public method.

console.log(myObject.myPrivateVariable); // 에러: 접근 불가능
myObject.myPrivateMethod(); // 에러: 접근 불가능

# class_public

===

> public 키워드는 TypeScript 클래스의 멤버 변수 또는 메서드를 선언할 때 사용되는 또 다른 접근 제한자입니다. public으로 선언된 멤버는 클래스 내부에서와 클래스 외부에서 모두 접근할 수 있습니다. 따라서 public으로 선언된 멤버는 해당 클래스의 인스턴스 또는 클래스 자체를 통해 접근할 수 있습니다.

class MyClass {
public myPublicVariable: number;

constructor() {
this.myPublicVariable = 10;
}

public myPublicMethod(): void {
console.log("This is a public method.");
}
}

const myObject = new MyClass();
console.log(myObject.myPublicVariable); // 10
myObject.myPublicMethod(); // This is a public method.
