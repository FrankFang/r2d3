[![build status](https://secure.travis-ci.org/mhemesath/d34raphael.png)](http://travis-ci.org/mhemesath/d34raphael)


r2d3
==========

R2D3 is a customized build of D3 powered by [RaphaelJS](http://raphaeljs.com/).  The combination of D3 and Raphael enable developers to easily
data visualizations that work IE7+ and all modern browsers.


Getting Started
---------------

To get started using R2D3,  include r2d3 and the necessary shims.
Sizzle and Compat need to be incldued for IE8. If you are using jQuery,
R2D3 will use the bundled sizzle.

```html
<html>
  <head>
    <title>R2D3 101</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
    <!--[if lte IE 8]>
    <script type="text/javascript" src="js/compat.js"></script>
    <![endif]-->
    <script src="js/sizzle.js"></script>
    <script src="js/raphael.js"></script>
    <script src="js/r2d3.min.js"></script>
  </body>
</html>
```

R2D3 extends the default behavior of D3. To use Raphael, instead of SVG
create a selection around a raphael paper.

```javascript
var paper = d3.select('div').raphael(200,200);
```

Using the paper selection,  Raphael elements can be created and
manipulated using D3 syntax:

```javascript
paper.append('circle')
  .attr('cx', 50)
  .attr('cy', 50)
  .attr('r', function() { return Math.random() * 50; });
```

R2D3 can also query for existing shapes on the paper and update them.

```javascript
paper.select('circle')
  .transition()
  .attr('fill', '#ff0000');
```

Events can also be bound to Raphael elements using D3 syntax:
```javascript
paper.select('circle')
  .on('click', function() { alert('hi'); });
```



Developers
----------
### D3 ###
D3 is included in this project as as submodule. To pull down D3 for a build run:

```
$ git submodule init
$ git submodule update
```

### Build Commands ###
We have included a makefile to build a custom version of D3 packaged with r2d3. 

+ **dependencies**
Our makefile depends on you having recess, uglify.js. To install, just run the following command in npm:

```
$ npm install uglify-js -g
```

+ **build** - `make`
Runs the  makefile to concatenate and minify r2d3.js
