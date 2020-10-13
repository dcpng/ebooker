# Summary

The code-block content is enhances by attaching a configuration tag object at its header like this:

<pre class="language-markdown">
<code>```{'mod':'code'}
...
```</code></pre>

For example, you may add a code section as a block:

<pre class="language-markdown">
<code>```{'mod':'code'}
some code 1
some code 2
...
```</code></pre>

Which will be rendered as:

> ```{'mod':'code'}
> some code 1
> some code 2
> ...
> ```

Or code section as a inline text:

<pre class="language-markdown">
<code>`'some code 1 some code 2'`</code></pre>

Which will be rendered as:

> `'some code 1 some code 2'`

## Syntax highlighting

To active syntax highlighting on a code block, the value for the `'lang'` field must be set. For example, the javascript code below:

<pre class="language-markdown">
<code>```{'mod':'code', 'lang':'javascript'}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```</code></pre>

Will be rendered as:

```{'mod':'code', 'lang':'javascript'}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```

The possible supported values that the `lang` field accepts are: `'javascript'`, `'markdown'`, `'bash'`, `'matlab'`, `'c'`, and , `'makefile'`.

## line highlighting

You may highlight section of the code of uses using `'highlight'` field. Each section is delimited by `,` (comma) and the range of each section is denoted by `-`. Below is an example for highlighting 2 different sections:

<pre class="language-markdown">
<code>```{'mod':'code', 'lang':'javascript', 'highlight':'1,3-6'}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```</code></pre>

Will be rendered as:

```{'mod':'code', 'lang':'javascript', 'highlight':'1,3-6'}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```

## Show lines and invisibles

The `'showlines'` field, if set to `'true'`, will print line numbers for the whole code block. The `'show-all'` field, if set to `'true'`, will print out symbols representing hidden characters such as spaces, tabs, newline, etc. Below is an example on how they are used:

<pre class="language-markdown">
<code>```{'mod':'code', 'lang':'javascript','showlines':true,'show-all':true}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```</code></pre>

Will be rendered as:

```{'mod':'code', 'lang':'javascript', 'showlines':true,'showall':true}
const originalString = `
  &lt;div>
    &lt;p>Hey that's &lt;span>somthing&lt;/span>&lt;/p>
  &lt;/div>
`;

const strippedString = originalString.replace(/(<([^>]+)>)/gi, "");

console.log(strippedString);
```
