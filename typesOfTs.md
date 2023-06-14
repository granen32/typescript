# optional chaining type

======================

?. 연산자는 . 체이닝 연산자와 유사하게 작동하지만, 불러온 값이 nullish(null 또는 undefined)면, 에러가 발생하는 것 대신에 표현식의 리턴 값은 undefined로 단락된다. 함수 호출에서 사용될 때, 만약 주어진 함수가 존재하지 않는다면, undefined를 리턴한다.

따라서 참조가 누락될 가능성이 있는 경우 연결된 속성으로 접근할 때 더 짧고 간단한 표현식이 생성된다. 어떤 속성이 필요한지에 대한 보증이 확실하지 않는 경우 객체의 내용을 탐색하는 동안 도움이 될 수 있다.

> const player :{name:string, age?:number} = {name:"규"}

if(player.age < 10>){
// Expected output: undefined
}

const adventurer = {
name: 'Alice',
cat: {
name: 'Dinah'
}
};

const dogName = adventurer.dog?.name;
console.log(dogName);
// Expected output: undefined

console.log(adventurer.someNonExistentMethod?.());
// Expected output: undefined

만약에 옵셔널 체이닝을 할당했을 시 값이 없는 경우 undefined를 리턴함

좀 더 세련되게 player의 타입을 지정해주자면 alias를 지정하는 방법이 있음

> type Player = {

    name:string,
    age?:number

}

const player :Player = {name:"규"}

> const playerMaker = (name:string):Player => ({name})

type Player = {
readonly name:string,
age?:number
}

readonly 시 해당값은 읽을 수만 있고 참조변경이나 변경이 불가능해진다. 그러니 정말정말 변하면 안되는 거면 리드온리를 활용해주자

const numbers : readonly number[] = [1,2,3,4]
numbers.push(5) 이거 안됨
왜냐 리드온리라 값이 변경이 안됨

# Turple

=========

const player : [string, number, boolean] = ["rb", 12, false]

# never

never 는 절대 return 하지 않는 함수를 뜻함

> function hello(name:string):never {

    return  name

}

-> 작동하지 않음

# 함수와 call signatures

call signatures란?
일단 함수의 호출 시그니처는 함수의 이름과 매개변수 타입, 반환값으로 이루어져 있고 함

> function functionName(param1: type1, param2: type2, ...): returnType {
> // 함수의 본문
> }
> 여기서 functionName은 함수의 이름을 나타내며, param1, param2 등은 매개변수의 이름입니다. type1, type2는 해당 매개변수의 타입을 나타내며, returnType은 함수의 반환 값의 타입을 나타냄

> function add(a,d){

    return a + b

}
->> 초기 상태는 any임

> const add = (a:number, b:number) => a+b
> 묵시적으로 두개의 파라매터 값이 number이므로 a+b는 number가 됨
> 여기서는 add는 함수의 이름 a,b는 매개변수 a+b 리턴타입값이다

type Add = (a:number, b:number) => number
alias와 합쳐서 사용하면 이런식으로 축약 가능
const add:Add = (a,b) => a + b

# overloading(오버로딩)

오버로딩은 함수가 여러개의 call signatures를 실행할 때 일어남

> type Add = {
>
> > (a:number,b:number):number
> > (a:number,b:string):number
> > }

> type Config = {
>
> > (path:string):void
> > (config:object):void
> > }
> > type Push = {
> > (path:string):void,
> > (confing:Config):void
> > }

> const push:Push = (config) =>{
>
> > if(typeof confing === "string") {console.log(config)}
> > else console.log(config.path)
> > }

# 다형성 (Polymorphism)

폴리란 많은 다수의라는 뜻이고 여러개의 면을 가진 것 그 다양한 구조 및 구조들이라는 뜻이다.

type SuperPrint = {
(arr:number[]):void
(arr:boolean[]):void
}

const superPrint:SuperPrint (arr)=>{
arr.foreach(i => console.log(i))
}

> concreateType type들을 얘기함 저기서 문자열을 추가하려면 string[]을 해야 하지만 이거를 제네릭하게 넘겨주려고함
> type SuperPrint = {
> (arr:number[]):void
> (arr:boolean[]):void
> }

# generic 이란 ?

받아오는 값들을 typescript에서 유추를 통해 타입스크립트가 type을 할당해줌
type SuperPrint = {
<T>(arr: T[]): void;
};

const superPrint : SuperPrint = (arr) =>{
arr.forEach(i => console.log(i))
}

superPrint([1,2,3])
superPrint([true,false,true])
superPrint([true,2,true,"삼"])
