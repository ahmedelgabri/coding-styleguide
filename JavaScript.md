For personal projects I use [Standrad](http://standardjs.com) but when working in teams I prefer [Airbnb styleguide](https://github.com/airbnb/javascript)

Generally I avoid using prototypical inheritance using `.prototype` & `new` and I use `Object.create()` instead. I also avoid using `class` _which is just syntactic sugar over prototypical inheritance_ in ES2015 unless using React stateful components otherwise I write stateless components using pure functions.
