# mf_shell.js

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

### _.g(id);

wrap of document.getElementById

```js
_.g('foo').addEventListener('click', function(e){

    // logg the event object on click of element with id 'foo';
    _.l(e);

});
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
