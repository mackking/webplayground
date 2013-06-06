# CSS Grid System Survey/Comparison

Ah, the ever popular [CSS Grid System](http://en.wikipedia.org/wiki/CSS_frameworks). So much 
(many would likely say far too much) has been written about them, and there are more implementations 
than you can shake a stick at out there in the wild. This little survey though isn't an attempt to 
compile an exhaustive list of all the actual implementations, or to catalogue the raft of features 
available in them. Instead, this is going to be an exploration/review into the most basic CSS features used to 
implement the grid.

## Position and Margins

 - 'original' layout solution (after tables of course)
 - very pixel/magic number sensitive
 - best for laying out only a couple elements

```css
.container { position: relative; }
.main { margin-left: 120px; }
.sidebar { position: absolute; top: 0; left: 0; width: 110px; }
```
```html
<div class="container">
	<div class="main">Main content goes in here</div>
	<div class="sidebar">Sidebar content</div>
</div>
```

[Demo](position.html)

## Float Based Grids

 - need to `clear` float contexts in order to maintain parent elements awareness of contained elements
    - history of clearfix: [PIE](http://www.positioniseverything.net/easyclearing.html)(2004), [Vitamine](http://thinkvitamin.com/design/everything-you-know-about-clearfix-is-wrong/)(2010), [YUI](http://www.yuiblog.com/blog/2010/09/27/clearfix-reloaded-overflowhidden-demystified/)(2010)
    - clearfix vs new block formatting context and when to use each
    - [@necolas 1](http://nicolasgallagher.com/micro-clearfix-hack/) &amp; [@necolas 2](http://nicolasgallagher.com/better-float-containment-in-ie/) (2011)

## inline-block Based Grids

A more recent development in the world of grids is the use of `display: inline-block` to create grids.

 - no clearfix requried
 - potential problem with intervening whitespace affecting layout
    - HTML comments between grid elements: `</div><!-- \r\n --><div>`
    - apply negative `letter-spacing` to grid container element. sensitive to changes in `font-family`.
 - pushing and pulling more difficult (??)