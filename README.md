# Advanced CSS

This project contains some more advanced CSS concepts. 
This goes above basic CSS into more complex designs
including animation and abstract shaping to create
artistic and intricate designs. 

## Linear Gradient

A linear gradient is placed over the hero image. When using linear-gradient
we can define the direction, the colour to, and the colour from:

<pre>
<code>
    linear-gradient(
        to right bottom, 
        $light-green-opaque, 
        $dark-green-opaque
    )
</code>
</pre>

This is defined as a primary argument to the <code>background-image</code> attribute. 
This ensures the linear-gradient appears atop of the image.

<pre>
<code>
    background-image: 
        linear-gradient(
            to right bottom, 
            $color1, 
            $color2
        ), 
        url('background-image');
</code>
</pre>

## Clip Path

Clip-path provides a clipping region, setting the parts of an element
to be shown. Parts inside the region are shown whilst anything outside
the defined region is hidden.

The first parameter pair is the coordinates of the first (top-left) corner of the element
via the x and y axis. From there, the next argument-pair is the length to draw from those
coordinates on the x and y axis. The third the the next point after that, with the fourth 
being the final point and so on...

Using this it is possible to create complex shapes and designs.

<pre>
<code>
    clip-path: polygon(
        0 0, 100% 0, 
        100% 75vh, 0 100%
    );
</code>
</pre>

 [Clippy](https://bennettfeely.com/clippy/) is a free and useful tool for playing with this complex shapes.

 ## Positioning

 Positioning an item <code>absolute</code> wihtin a relative parent and using top, bottom, left, right attribtues allows us to position elements relative to their parent. Using <code>transform: tanslate(10%, -10%)</code> we can then position the element relative to itself for fine tuning. 

 ## Animation

 To fix animation shake we can hide the backface of an element: <code>backface-visibility: hidden;</code>

 complex animations can be defined using keyframes:

 <pre>
<code>
    @keyframes moveInLeft {
        0% {
            opacity: 0;
            transform: translateX(-100px);
        }

        80% {
            transform: translateX(10px);
        }
        
        100% {
            opacity: 1;
            transform: translate(0);
        }
    }
</code>
 </pre>

 which are then applied to elements via the animation attribute: <code>animation: moveInRight 1s ease-out 0.75s;</code>

 this takes a keyframe name, a animation time, a animation type and a delay time.

 More simplistic animations can be handled via transition: <code>transition: all .2s;</code>

 This is applied to the parent element, animations can then be smoothly played through events:

<pre>
<code>
    .btn:hover {
        transform: translateY(-3px);
        box-shadow: 0 10px 20px $shadow-trans;
    }
</code>
</pre>


pseudo-selectors can allow for the selection of virtual elements, the <code>::after</code> selector can
be used to place a virtual element after the current element. 

By setting animation fill mode to backwards we can hide elements prior to animating them:

<code>animation-fill-mode: backwards; /** Automatically apply 0% opacity before start **/</code>

## SEO 

Key content should go in our header element for SEO purposes, we don't want to separate this informaiton
as to allow search engines and TTS systems to pick up the key content correctly, we can use a span to style 
our lines independently, keeping this content within a single h1:

<pre>
<code>
                <!-- <h1 class="heading-primary">
                    <span class="heading-primary-main">Outdoors</span>
                    <span class="heading-primary-sub">is where life happens</span>
                </h1> -->
</code>
</pre>

## Sizing Tips

If we set our global <code>font-size</code> to 10px we know 1 rem is exactly 10px, this helps when changing font-sizes throughout the application.