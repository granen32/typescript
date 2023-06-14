# generic recap

type SuperPrint = <T>(arr: T[]) =>void

const superPrint : SuperPrint = (arr) =>{
arr.forEach(i => console.log(i))
}

superPrint([1,2,3])
superPrint([true,false,true])
superPrint([true,2,true,"삼"])

제네릭을 요약하자면 제네릭을 하기 위해서는 제네릭을 선언해주고 그 선언한 오브젝트나 배열값에 제네릭을 할당해주고
리턴하는 값을 제네릭이라는 것을 명시해줘야함 근데 저렇게 할거면 any를 하는 게 낫지 않나? 하는데 문제는
any를 전달해주게 되면 일단 타입 명시값이 any로 잡히고

const d = superPrint([true,2,true,"삼"])
라 치고 d.toUpperCase()로 대문자로 변경을 해줄 때 이 부분 같은 경우 제네릭으로 받아온 문자만 변경해줘야함

type SuperPrint = <T,M>(arr: T[], b:M) => T

superPrint([1,2,3],"x")
superPrint([true,false,true],1)
superPrint([true,2,true,"삼"],false)

type Playrer<E> = {

    name:string
    extraInfo:E

}
type PlayerExtra = {

    favFood : string

}
type PlayersType = Playrer<PlayerExtra>

const gyu : PlayersType = {

    name:"gyu",
    extraInfo:{
    favFood:"zam"
    }

}

const hae:Playrer<undefined> = {
name:"hae",
extraInfo:undefined
}
