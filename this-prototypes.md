## This & Prototypes

### This

- Từ khoá `this` trong js đề cập đền đổi tượng mà nó thuộc về.

- Trong một phương thức, `this` tham chiếu tới đối tượng truy cập phương thức (đối tượng trước dấu .).

- Đứng ngoài phương thức, `this` tham chiếu tới đối tượng global.

- `Note`
  - `this` trong hàm tạo (constructor) là đại diện cho đỐi tượng sẽ được tạo.
  - `this` trong một hàm là `undefined` khi ở `strict mode`.
  - Các phương thức `bind()`, `call()`, `apply()` có thể tham chiếu `this` tới đới tượng khác.

```js
const iphone7 = {
  //thuộc tính - property
  name: 'iphone7',
  color: 'gold',
  //phương thức - method
  takePhoto() {
    console.log(this);
  },
};
console.log(iphone7.takePhoto()); //{name: "iphone7", color: "gold", takePhoto: ƒ}
```

### Prototypes

Là cơ chế mà các object trong javascript kế thừa các tính năng từ một object khác.

```js
//Tạo ra 1 mẫu khởi tạo, cũng là tạo ra 1 prototype object
function Person(_age, _name) {
  this.age = _age;
  this.name = _name;
}

//Có thể thêm thuộc tính vào thuộc tính prototype của hàm khởi tạo
Person.prototype.height = 0;

//Tạo ra 1 instance của Person
//Có cả 3 thuộc tính của mẫu khởi tạo Person
var jack_person = new Person(10, 'Jack');
for (var att in jack_person) {
  console.log(att);
}

//Xem đối tượng prototype của instance vừa tạo
jack_person.__proto__;
```
