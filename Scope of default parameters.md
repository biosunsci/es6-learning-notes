一旦设置了参数的默认值，函数进行声明初始化时，参数会形成一个单独的作用域（context）。
等到初始化结束，这个作用域就会消失。
这种语法行为，在不设置参数默认值时，是不会出现的。

注意区别如下代码的执行结果的区别：
EXAMPLE 1
```
var x = 1;
function foo(x,y = function(){
	console.log('inner args x: '+x);
}){
	y();
	var x=10;
	console.log('inner foo x: '+x);
	y();
}

foo();
x;
```
EXAMPLE 2
```
var x = 1;
function foo(x,y = function(){
	console.log('inner args x: '+x);
}){
	y();
  //here is the difference from EXAMPLE 1
	x=10;
	console.log('inner foo x: '+x);
	y();
}

foo();
x;
```
