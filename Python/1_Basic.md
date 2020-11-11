### '==' 와 'is' 의 차이
- __is__ 는 변수가 같은 __Object(객체)__ 를 가리키면 True
- __==__ 는 변수가 샅은 __Value(값)__ 를 가지면 True

```
a = [1,2,3]
b = a
c = [1,2,3]

a is b  #True
a is c  #False

a == b  #True
a == c  #True
```