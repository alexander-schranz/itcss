# Instruction

After a long time of dissatisfaction I did find some time ago a way
to structure css the way which did make most sense for me. This 
repository should show the structure and code syntax I used and is
mostly for me the css I'm using to begin a project.

In short its a combination by the following sources:

 - [ITCSS](#itcss) develop by [Harry Roperts (@csswizardry)](https://csswizardry.com/)
 - [BEM](#bem) a css methodology by [Yandex](https://yandex.com/)
 - [Rethinking Design Practices](#objects) by [Mark Dalgleish](https://twitter.com/markdalgleish)

## ITCSS

The directory structure you will find in the `src` directory comes
from [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/)
which was build by [Harry Roperts (csswizardry)](https://csswizardry.com/)
a Consultant Web Performance Engineer.

I can really recommend to read the blog on [xfive.co](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture)
to get more detail. But here a short overview about the directory
structure or how they are called in ITCSS "Layers":

### ITCSS - `Settings`

The settings will just define scss variables like `font-sizes`,
`grid-gaps`, `font-families` and other things. Actually this
scss files will generate zero line of css code.

Common Examples:

 - [_breakpoint.scss](src/1-settings/_breakpoint.scss)
 - [_color.scss](src/1-settings/_color.scss)
 - [_font.scss](src/1-settings/_font.scss)
 - [_grid.scss](src/1-settings/_grid.scss)

More Examples:

 - [_h.scss](src/1-settings/_h.scss)
 - [_icomoon.scss](src/1-settings/_icomoon.scss)
 - [_paragraph-space.scss](src/1-settings/_paragraph-space.scss)
 - [_small.scss](src/1-settings/_small.scss)
 - [_zindex.scss](src/1-settings/_zindex.scss)

### ITCSS - `Tools`

Tools are function or mixins we use in our code. For example
mixins to make media queries easier or how to set a font size
on the elements. so this function and mixins are just define
to be reused in the other layers. Also this layer should output
0 lines of code.

Common Examples:

 - Nothing listed

More Examples:

 - [_container-link.scss](src/2-tools/_container-link.scss)
 - [_map-math.scss](src/2-tools/_map-math.scss)
 - [_media.scss](src/2-tools/_media.scss)
 - [_paragraph-spacing.scss](src/2-tools/_paragraph-spacing.scss)

### ITCSS - `Generic`

Generic is the first layer which will actually output any css
it will, in this layer basic things like `box-sizing`, `reset`
or `normalize` css are defined.

Common Examples:

 - _reset.scss or _normalize.scss
 - [_box-sizing.scss](src/3-generic/_box-sizing.scss)

More Examples:

 - [_focus.scss](src/3-generic/_focus.scss)
 - [_font.scss](src/3-generic/_font.scss)

### ITCSS - `Elements`

Elements define the basic styling of any tag its important here
that no class selectors are used inside this layer.

Common Examples:

 - [_a.scss](src/4-elements/_a.scss)
 - [_body.scss](src/4-elements/_body.scss)
 - [_img.scss](src/4-elements/_img.scss)
 - [_li.scss](src/4-elements/_li.scss)
 - [_p.scss](src/4-elements/_p.scss)
 - [_table.scss](src/4-elements/_table.scss)

More Examples:

 - [_button.scss](src/4-elements/_button.scss)
 - [_figure.scss](src/4-elements/_figure.scss)
 - [_small.scss](src/4-elements/_small.scss)
 - [_input.scss](src/4-elements/_input.scss)

### ITCSS - `Objects`

The difference between objects and components are sometimes
hard to understand if you were new to CSS methodologies. If
you are familiar with [SMACSS](http://smacss.com/) you can
see them as layout components. So objects are used to define
the spaces between your other components. They work most with
margins, width, display and similar layout css attributes.
Things like font-sizes, colors, backgrounds, should in my
opinion be not part of any objects component.

Beside the most common [media object](https://css-tricks.com/media-object-bunch-ways/)
I can recommend [Mark Dalgleish](https://twitter.com/markdalgleish)
talk about [Rethinking Design Patterns](https://www.youtube.com/watch?v=jnV1u67_yVg)
in the [Objects](#objects) section we will tak more about thhem.

Common Examples:

 - [_media.scss](src/5-objects/_media.scss)
 - [_grid.scss](src/5-objects/_grid.scss)
 - [_container.scss](src/5-objects/_container.scss)
 - [_stack.scss](src/5-objects/_stack.scss)
 - [_inline.scss](src/5-objects/_inline.scss)
 - _animations.scss

### ITCSS - `Components`

The components is the layer where we mostly will write the
css in project. As in this layer we define how the navigation,
footer, header and other components will look like. Its very
important that components itself do not define any spaces around
them. This make 

Common Examples:

 - [_menu.scss](src/6-components/_menu.scss)
 - [_footer.scss](src/6-components/_footer.scss)
 - [_header.scss](src/6-components/_header.scss)
 - [_button.scss](src/6-components/_button.scss)
 - [_teaser.scss](src/6-components/_teaser.scss)

More Examples:

 - _pagination.scss
 - _slider.scss

### ITCSS - `Utilities`

The utilities is the last layer of ITCSS it contains utility
and helper classes. Most common used to hide elements or some
utility classes

Common Examples:

 - [_none](src/7-utilities/_none.scss)
 - [_text](src/7-utilities/_text.scss)

More Examples:

 - _space.scss

## BEM

Beside the structuring I use the widely spreaded [BEM](http://getbem.com/)
syntax to write my component. In most cases I try to avoid the
Modifiers as I think its better to have different block elements
then uncompatible modifiers. I common mistake I see here is for
example having one teaser BEM css with a lot of modifiers
instead of having different BEM teasers like `teaser-small`, `teaser-big`.

## Objects

### Object - `Container`

The container exist in mostly every common CSS Framework for 
example [Bootstrap](https://getbootstrap.com/docs/5.0/layout/containers/).
The task of a container object is the center content and give space
to it to the screen.  
This is mostly done to keep content readable because if the text
is too long in one line it is not longer readable to the user. 

### Object - `Grid`

Grid is also one of the most common object in CSS Framework.
Mostly today is worked with 12-column grid. Most designers
should keep here in mind that this 12-column grid is not only
available over the full width of the page. Also a 12 column
grid can be nested or is also available inside a container.

In my case I created my own grid which has no spaces at top
and bottom and just inside gaps. Also the width of the grid
items are controlled over separated width classes as they are
reusable on other none grid elements.

### Object - `Media`

... coming soon

### Object - `Stack`

... coming soon

### Object - `Inline`

... coming soon
