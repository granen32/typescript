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
