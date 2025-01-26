# stepik-ts
https://stepik.org/course/221935/syllabus

```ts
// Стрелочная функция
const o8 = (s: string, n: number): string => {
    return '1234sss';
}

// Объект
const o9: { name: string; age: number; car: { color: string; } } = {
    name: 'alex', age: 20, car: {color: 'red'}
}

// Переиспользование
type User = {
    name: string;
    age: number;
    car: { color: string; }
}

interface User2 {
    name: string;
    age: number;
    car: { color: string; }
}

const o10: User = {name: 'alex', age: 20, car: {color: 'red'}}
const o11: User2 = {name: 'alex', age: 20, car: {color: 'red'}}

// Опциональный элемент
interface User3 {
    name: string;
    age: number;
    car?: { color: string; }
}

const o12: User3 = {name: 'alex', age: 20}

// Массивы
const a13: string[] = ['123213', 'ssss', 'tttttttt'];
const a14: Array<string> = ['123213', 'ssss', 'tttttttt'];

// Практика (Типизация сложного объекта)
type Obj13_Config = {
    status: string
}

type Obj13_GetMoreInfo = {
    data: number
}

type UserName = string | number;

type Obj13 = {
    name: string,
    age: number | string,
    hasJob: boolean | null | undefined,
    fn?:  () => number,
    getMoreInfo?: (config: Obj13_Config) => Obj13_GetMoreInfo
}

// const o13: Array<Obj13 | null | Obj14>
const o13: Obj13[] = [
    {
        name: 'Alex',
        age: 20,
        hasJob: true,
        fn: function test(){
            return 5;
        },
        getMoreInfo: (config) => { return {data: 1234567} }
    },
     {
        name: 'Serg',
        age: 23,
        hasJob: true
    }
]

// ИЛИ (union (или одно или другое), intersection (склеивание 2-х типов в один общий))
// НЕЛЬЗЯ делать union между интерфейсами, а вот между типами МОЖНО
function f14(config: {status: string}): string | number {
    if(config.status == 'ok') {
        return '1234567';
    }

    return 1234567;
}

const age = f14({status: 'ok'});

if(typeof age === 'string') age.charAt(123456);
else if(typeof age === 'number') age.toFixed(2);

// Склеивание интерфейсов
interface Test1 {
    name: string;
}

// Дополняет сам себя
interface Test1 {
    age: number;
}

const o14: Test1 = {
    name: 'Alex',
    age: 20
}

// Лучше использовать ТИПы чтобы не получить проблему склеивания 2х интерфейсов, из разных модулей, в один

// intersection
type O15_Car = {
    color: string,
    speed: number,
    left: boolean
}

type O16_User = {
    name: string;
    age: number
}

// intersection types
type O17_UserAndCar = O15_Car & O16_User;

function renderUser(user: O16_User) {}
function renderCar(user: O15_Car) {}
function renderUserAndCar(user: O17_UserAndCar) {}
function renderUserAndCar2(user: O15_Car & O16_User) {}

// intersection interfaces
interface i16_User2 extends i17_Car, i17_User {}
```