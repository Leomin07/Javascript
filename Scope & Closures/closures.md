## Closures

Là một hàm có thể truy cập được biến bên ngoài phạm vi của nó.

```js
function createCounter() {
  let counter = 0;
  return function increase() {
    console.log(++counter);
  };
}
const counter1 = createCounter();
console.log(counter1());
console.log(counter1());
console.log(counter1());
```

### Note

Biến được tham chiếu trong closure sẽ không được xoá khỏi bộ nhớ khi cha thực thi xong.
