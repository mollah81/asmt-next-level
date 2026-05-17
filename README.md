//solution-1

const numbers:number[]=[1, 2, 3, 4, 5, 6];
const filterEvenNumbers= numbers.filter(num=> num %2 === 0);



//solutions-2

const str = "typescript";
const reverseString=(text:string): string =>{
 return text.split("").reverse().join("");
};


// solution-3

type StringorNumber= string | number ;
const checkValue=(value:StringorNumber):string => {
    if(typeof value === "string"){
        return "String"
    }
    else {
        return "Number"
    }
}
// solutions-4

  function getProperty<T, K extends keyof T>(obj: T, key:K):T[K]{
    return obj[key];
  }
  
const user = { id: 1, name: "John Doe", age: 21 };

const result = getProperty(user, "name");



// solutions-5


interface Book{
    title: string;
    author: string;
    publishedYear: number;
}
const toggleReadStatus =(book : Book): Book & {isRead: boolean} => {
    return {
        ...book,
        isRead:true};
}
const myBook = {
  title: "TypeScript Guide",
  author: "Jane Doe",
  publishedYear: 2024
};

const updatedBook = toggleReadStatus(myBook);



// solution-6
class Person{
    name:string;
    age:number;

    constructor(name: string, age: number){
        this.name=name;
        this.age=age;
    }
}

class Student extends Person{
    grade: string; 
    constructor(name:string, age:number, grade:string ){
        super(name, age);
        this.grade=grade;
    }
    getDetails():string {
    return `Name: ${this.name}, Age: ${this.age}, Grade: ${this.grade}`;
}
}
const student= new Student("Alice", 20, "A");

//solution-7

function getIntersection<T>(arr1:T[], arr2:T[]):T[]{
    const set2 = new Set(arr2);
    return arr1.filter(item=>set2.has(item));
}
const result1=getIntersection([1, 2, 3, 4, 5], [3, 4, 5, 6,7]);
