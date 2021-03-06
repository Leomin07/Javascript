## Scope

### Global(Toàn cầu)

Là những biến, hàm không nào trong bất kì một phạm vi(`block, local`) nào khác.

```js
let a = 8;

function log() {
  console.log('global');
}
log();
```

Biến global sẽ xoá khỏi bộ nhớ khi F5, closed tab or trình duyệt.

### Block(Khối: let, const)

Là những biến, hàm nằm trong `{}`.

```js
{
  let log = 'block'; //chỉ bên trong block mới sử dụng được log, trừ var.
}
console.log(log); //Uncaught ReferenceError: log is not defined
```

Biến block sẽ xoá khỏi bộ nhớ khi thoát khỏi block.

### Local(Var, function)

Là những biến nằm trong `function`.

```js
function log() {
  var name = 'hoa';
}
log(); //khi hàm log được gọi biến name được khởi tạo và chỉ được sử dụng bên trong hàm log.
console.log(name); //name is not defined

//note: đối với let và const khai báo trong phạm vi hàm thì vẫn thuộc phạm vi hàm. Vì body của hàm vẫn là `{}`
```

Mỗi khi gọi hàm thì luôn có phạm vi mới được tạo ra.

```js
function fullName(first, last) {
  console.log(first, last);
}
fullName('Hoa', 'Nguyen'); //Hoa Nguyen
fullName('Huynh', 'Phan'); //Huynh Phan
fullName('Hoang', 'Tran'); // Hoang Tran
//vì mỗi lần gọi hàm fullName có đối số khác nhau, nên mỗi lần hàm fullName được gọi sẽ nhận tham số khác nhau nên tạo ra các phạm vi mới.
```

Các hàm có thể truy cập được các biến được khai báo trong phạm vi của nó và bên ngoài nó.

```js
const age = 18; // biến global
function box1() {
  const age = 16;
  function box2() {
    console.log(age); // có thể truy cập biến age ở hàm box1
  }
  box2();
}
box1();
//note: luôn truy cập biến có phạm vi gần nhất.
```

Biến function sẽ xoá khỏi bộ nhớ khi thoát khỏi function.

## Closures

Là một hàm có thể truy cập được biến ở bên ngoài phạm vi của nó

```js
function celebrityID() {
  var celebrityID = 999;
  // Ta đang trả về một object với các hàm bên trong.
  // Tất cả các hàm bên trong có thể truy cập đến biến của hàm ngoài (celebrityID).
  return {
    getID: function () {
      // Hàm này sẽ trả về celebrityID đã được cập nhật.
      // Nó sẽ trả về giá trị hiện tại của celebrityID, sau khi setID thay đổi nó.
      return celebrityID;
    },
    setID: function (theNewID) {
      // Hàm này sẽ thay đổi biến của hàm ngoài khi gọi.
      celebrityID = theNewID;
    },
  };
}

var mjID = celebrityID(); //Lúc này, celebrityID đã trả về
mjID.getID(); // 999
mjID.setID(567); // Thay đổi biến của hàm ngoài
mjID.getID(); // 567: Tả về biến celebrityID đã được cập nhật.
```
