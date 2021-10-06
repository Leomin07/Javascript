## Value types & reference types

### Value types (Primitive data types)

- String, Number,Boolean, BigInt, Symbol, undefined, null.

- Khi gán cho nó một giá trị thì nó sẽ lưu lại giá trị đó và tại một thời điểm thì chỉ lưu một giá trị.

```js
let a = 1;
//Tạo ra biến a và lưu giá trị của a vào ô nhớ 1

let b = a;
//Tạo ra biến b, sao chép giá trị của biến a và lưu vào ô nhớ mới 1

a = 2;
//Sửa giá trị của biến a và cập nhật lại ô nhớ 2

console.log(b); //1
```

- Truyền tham trị

```js
function changeNumber(a) {
  //let a = b
  a = 0;
  console.log(a); //0
}

const b = 1;
changeNumber(b);
console.log(b); //1
```

### Reference types

- Object, Array, Function.

- Khi gán cho nó một giá trị thì nó không lưu lại giá trị này mà thực chất nó lưu lại địa chỉ của ô nhớ lưu giá trị này.

```js
let a = { name: 'cat' };
//Tạo ra biến a, lưu giá trị của a vào ô nhớ và gán lại địa chỉ ô nhớ cho biến a (a = #a001)

let b = a;
//Tạo ra biến b và gán giá trị của biến a cho b, ở đây chính là địa chỉ địa chỉ ô nhớ của a (b =#a001)

a.name = 'dog';
//Sửa giá trị của biến a thì giá trị trong ô nhớ được cập nhật

console.log(b); // { name: "dog" }
```

- Object lồng nhau.

```js
const a = {
  id: 1,
  info: {
    name: 'John',
    age: 23,
  },
};
const Info = a.info;
Info.name = 'David';
console.log(a.info.name); //"David"
//vì info và Info có cùng ô nhớ nên khi thổi value của 1 trong 2 thì value của cả 2 đều bị thay đổi.
```

- Truyền tham chiếu

```js
function changeName(people){
    people.name = "Hung";
    console.log(people.name)//Hung
}

const man = { name: "Thanh"}
changeName(man);
console.log(man.name)//Hung

=> Việc gán trong hàm là gán địa chỉ ô nhớ, khi thực hiện thay đổi thì giá trị của ô nhớ cũng thay đổi và man cùng chỉ đến ô nhớ đó nên khi hàm được chạy thì giá trị của man bên ngoài cũng được thay đổi theo.
```
