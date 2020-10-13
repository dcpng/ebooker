ASCIIMath and Latex-syntax math formulae are rendered to produce a clean and visually appealing depiction of math equations. By default, Ebooker uses ASCIIMath syntax to draw math equations since it is more natural and easy-to-write when compare to latex;

# Math blocks

Ebooker begins the rendering of math equations as it encounters a math block. Math blocks are declared using by setting the `mod` field to the text value: `math`. The example below:

<pre class="language-markdown">
<code show-invisible>```{'mod':'math'}
sum_(i=1)^n i^3=((n(n+1))/2)^2
```</code></pre>
Will rendered as:

> ```{'mod':'math'}
> sum_(i=1)^n i^3=((n(n+1))/2)^2
> ```

# Math inline-blocks

The previous equation can be embedded inline using the inline-code block syntax with the equation being defined in the `'eq'` field. The example below:

<pre class="language-markdown"><code show-invisible>The formulae: `{'mod':'math','eq':'sum_(i=1)^n i^3=((n(n+1))/2)^2'}` is very good looking.</code></pre>
Will rendered as:

> The formulae: `{'mod':'math','eq':'sum_(i=1)^n i^3=((n(n+1))/2)^2'}` is very good looking.

# Syntax
For more information regarding AsciiMath syntaxes visit <http://asciimath.org/>:


