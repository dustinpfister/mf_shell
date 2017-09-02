# mf_shell.js
### It all starts with a shell

There seems to be a need to have a certain lowest level toolkit that adds a few usual suspects shared across other frameworks of mine. In my effort to make my own collection of frameworks that will help me keep form writing the same code over and over again each time I start a new project, I was thinking that it might be good to start with something like this.

What I want is something where I can just grab a copy of it, and it adds a bunch of methods that I actually use in my projects, and not what I don't. In other words this is my custom cut deal of something like underscore, only it is not at all like underscore.

## A need for a base with my own way of doing things

Although I just started making this project, this file has a long history. I seem to keep remaking it, and calling it different things. For now I want to give it a standard name, and use it in one or more of my mf_ line of projects.

## The methods

### _.l(mess);

wrap of console.log

```js
_.l('foo'); // '_.l: foo' logged to the console
```

### _.lo(m,r)

log once, set r to true to reset

```js
 
var loop = function(){
 
   setTimeout(loop,1000);
   
   _.l('every tick');
   _.lo('just once');
 
};
 
loop();
```

### _.g(id);

wrap of document.getElementById

```js
_.g('foo').addEventListener('click', function(e){

    // logg the event object on click of element with id 'foo';
    _.l(e);

});
```

### _.r(n1,n2)

random number wrap

```js
_.l(_.r(100));  // random number bnetween 0 and 100
_.l(_.r(128,255)); // randm number between 128 and 255
```

### _.d(x1,y1,x2,y2)

Yes this is the 2d distance formula.

```js
var obj = {

  x : 20,
  y: 15

},
d = _.d(0,0,obj.x,obj.y);

_.l(d); // 25
```

### _.b(o1,o2)

Bounding box

```js
var obj1 = {
  x:0,
  y:0,
  w:32,
  h:32
},

obj2 = {
  x:16,
  y:8,
  w:32,
  h:32
};

_.l(_.b(obj1,obj2)); // true
obj2.x = 100;
_.l(_.b(obj1,obj2)); // false
```

### _.c(obj)

Shallow copy (root primitives only) of an object.

```js
var obj = {

  x: 15,
  y: 33

};

var clone = _.c(obj);
clone.x = 20;

console.log(obj.x + ',' + obj.y); // 15,33
console.log(clone.x + ',' + obj.y); // 20,33
```

### _.as

Get or set the Angle Scale property.

```js
if (_.as === 360) {
 
  _.l(_.as(45));
 
} else {
 
  _.l(_.as / 360 * 45);
 
}
```

### _.m(x,m)

Mathematical Modulo method.

```js
_.l(-13 % 6); // -1
_.l(_.m(-13, 6)); // 5
```

### _.tau

PI * 2

```js
_.l(_.tau); // 6.28...
```

### _.an(a)

Angle Normalize, Normalize and angle to 0 to PI * 2 (or 0 to 360 depending on _.as)

```js
_.l(_.an(-Math.PI * 8.5)); // 4.71
```

### _.anh(a)


Angle Normalize Half, normalize and angle to -Pi to PI (or -180 to 180 depending on _.as)

```js
_.l(_.anh(-Math.PI * 8.5)); // -1.57
```

### _.asd(f,t)

Angle Shortest Distance. Give from, and To angles and receive a 1 for clockwise, and -1 for counter clockwise. Useful for finding the quickest direction with angular movement.

```js
_.l(_.asd(0, -1)); // -1 (counter clockwsie)
_.l(_.asd(0, 1)); // 1 (clockwsie)
_.l(_.asd(3.14, 1.57)); // -1 (counter clockwsie)
_.l(_.asd(3.14, 4)); // 1 (clockwsie)
```