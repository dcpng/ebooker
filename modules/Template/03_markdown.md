
# Summary

The content generate by `*.md` files uses an enhanced version of the markdown syntax to cater the generation of more dynamic user interface experiences that includes images, sound, and user interaction. In this Chapter we will cover basic markdown syntaxes used by Ebooker.

# Headings

To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (`<h3>`), use three number signs (e.g., `###` My Header).

| Markdown                 | Rendered Output          |
| :----------------------- | :----------------------- |
| `# Heading level 1`      | <h1>Heading level 1</h1> |
| `## Heading level 2`     | <h2>Heading level 2</h2> |
| `### Heading level 3`    | <h3>Heading level 3</h3> |
| `#### Heading level 4`   | <h4>Heading level 4</h4> |
| `##### Heading level 5`  | <h5>Heading level 5</h5> |
| `###### Heading level 5` | <h6>Heading level 6</h6> |

## Heading Best Practices

Markdown applications don’t agree on how to handle a missing space between the number signs (#) and the heading name. For compatibility, always put a space between the number signs and the heading name.

| `{'mod':'tag','icon':'check-circle','colour':'is-primary','text':'Do this'}` | `{'mod':'tag','icon':'times-circle','colour':'is-danger','text':'Do not do this'}` |
| :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------------: |
|                             `# Here's a Heading`                             |                                `#Here's a Heading`                                 |

# Paragraphs

To create paragraphs, use a blank line to separate one or more lines of text. NOTE: Don’t indent paragraphs with spaces or tabs.

| Markdown                                                                                                                | Rendered Output                                                                                          |
| :---------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------- |
| I really like using Markdown. </br>`'[blank-line]'`</br> I think I'll use it to format all of my documents from now on. | I really like using Markdown. </br> </br> I think I'll use it to format all of my documents from now on. |

# Bold

To bold text, add two asterisks or underscores before and after a word or phrase. To bold the middle of a word for emphasis, add two asterisks without spaces around the letters.

| Markdown                     | Rendered Output            |
| :--------------------------- | :------------------------- |
| `I just love **bold text**.` | I just love **bold text**. |
| `I just love __bold text__.` | I just love __bold text__. |
| `Love**is**bold.`            | Love**is**bold.            |

## Bold Best Practices

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to bold the middle of a word for emphasis.

| `{'mod':'tag','icon':'check-circle','colour':'is-primary','text':'Do this'}` | `{'mod':'tag','icon':'times-circle','colour':'is-danger','text':'Do not do this'}` |
| :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------------: |
|                               `Love**is**bold`                               |                                  `Love__is__bold`                                  |

# Italic

To italicize text, add one asterisk or underscore before and after a word or phrase. To italicize the middle of a word for emphasis, add one asterisk without spaces around the letters.

| Markdown                               | Rendered Output                      |
| :------------------------------------- | :----------------------------------- |
| `Italicized text is the *cat's meow*.` | Italicized text is the *cat's meow*. |
| `Italicized text is the _cat's meow_.` | Italicized text is the _cat's meow_. |
| `A*cat*meow`                           | A*cat*meow                           |

## Italic Best Practices

Markdown applications don’t agree on how to handle underscores in the middle of a word. For compatibility, use asterisks to italicize the middle of a word for emphasis.

| `{'mod':'tag','icon':'check-circle','colour':'is-primary','text':'Do this'}` | `{'mod':'tag','icon':'times-circle','colour':'is-danger','text':'Do not do this'}` |
| :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------------: |
|                                 `A*cat*meow`                                 |                                    `A_cat_meow`                                    |

# Blockquotes

To create a blockquote, add a `>` in front of a paragraph.

```{'mod':'code','lang':'markdown'}
> Dorothy followed her through many of the beautiful rooms in her castle.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.

## Blockquotes with Multiple Paragraphs

Blockquotes can contain multiple paragraphs. Add a `>` on the blank lines between the paragraphs.

```{'mod':'code','lang':'markdown'}
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

## Nested Blockquotes

Blockquotes can be nested. Add a >> in front of the paragraph you want to nest.

```{'mod':'code','lang':'markdown'}
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

The rendered output looks like this:

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

## Blockquotes with Other Elements

Blockquotes can contain other Markdown formatted elements. Not all elements can be used — you’ll need to experiment to see which ones work.

```{'mod':'code','lang':'markdown'}
> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
```

The rendered output looks like this:

> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.

# Lists

You can organize items into ordered and unordered lists.

## Ordered Lists

To create an ordered list, add line items with numbers followed by periods. The numbers don’t have to be in numerical order, but the list should start with the number one.

```{'mod':'code','lang':'markdown'}
1. First item
2. Second item
3. Third item
4. Fourth item
```

The rendered output looks like this:

1. First item
2. Second item
3. Third item
4. Fourth item

## Ordered List Best Practices

CommonMark and a few other lightweight markup languages let you use a parenthesis ()) as a delimiter (e.g., 1) First item), but not all Markdown applications support this, so it isn’t a great option from a compatibility perspective. For compatibility, use periods only.

| `{'mod':'tag','icon':'check-circle','colour':'is-primary','text':'Do this'}` | `{'mod':'tag','icon':'times-circle','colour':'is-danger','text':'Do not do this'}` |
| :--------------------------------------------------------------------------- | :--------------------------------------------------------------------------------- |
| `1. First item`  <br/> `2. First item`                                       | `1) First item`  <br/> `2) First item`                                             |

# Unordered Lists

To create an unordered list, add dashes (`-`), asterisks (`*`), or plus signs (`+`) in front of line items. Indent one or more items to create a nested list.

```{'mod':'code','lang':'markdown'}
- First item
- Second item
- Third item
    - Indented item
    - Indented item
- Fourth item
```

The rendered output looks like this:

- First item
- Second item
- Third item
    - Indented item
    - Indented item
- Fourth item

## Unordered List Best Practices

Markdown applications don’t agree on how to handle different delimiters in the same list. For compatibility, don’t mix and match delimiters in the same list — pick one and stick with it.

| `{'mod':'tag','icon':'check-circle','colour':'is-primary','text':'Do this'}` | `{'mod':'tag','icon':'times-circle','colour':'is-danger','text':'Do not do this'}` |
| :--------------------------------------------------------------------------- | :--------------------------------------------------------------------------------- |
| `- 1st item`  <br/> `- 2nd item` <br/> `- 3rd item` <br/> `- 4th item`       | `- 1st item`  <br/> `+ 2nd item` <br/> `* 3rd item` <br/> `+ 4th item`             |

## Adding Elements in Lists

To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab, as shown in the following examples.

### Paragraphs

```{'mod':'code','lang':'markdown'}
* This is the first list item.
* Here's the second list item.

  I need to add another paragraph below the second list item.

* And here's the third list item.
```

The rendered output looks like this:

* This is the first list item.
* Here's the second list item.

  I need to add another paragraph below the second list item.

* And here's the third list item.

### Blockquotes

```{'mod':'code','lang':'markdown'}
*   This is the first list item.
*   Here's the second list item.

    > A blockquote would look great below the second list item.

*   And here's the third list item.
```

The rendered output looks like this:

*   This is the first list item.
*   Here's the second list item.

    > A blockquote would look great below the second list item.

*   And here's the third list item.

### Embedding Images

```{'mod':'code','lang':'markdown'}
1.  Open the file containing the PNG's Unitech photos.
2.  Marvel at its beauty.

    ![Caption here...]($/_res/ch1-img-mod-example.jpg)

3.  Close the file.
```

The rendered output looks like this:

1.  Open the file containing the PNG's Unitech photos.
2.  Marvel at its beauty.

    ![Caption here...]($/_res/ch1-img-mod-example.jpg)

3.  Close the file.

## Horizontal Rules

To create a horizontal rule, use three or more asterisks (`***`), dashes (`---`), or underscores (`___`) on a line by themselves.

```{'mod':'code','lang':'markdown'}
***

---

_________________
```

The rendered output looks like this:

***

## Links

To create a link, enclose the link text in brackets (e.g., [Duck Duck Go]) and then follow it immediately with the URL in parentheses (e.g., `(https://duckduckgo.com)`).

```{'mod':'code','lang':'markdown'}
My favorite search engine is [Duck Duck Go](https://duckduckgo.com).
```

The rendered output looks like this:

My favorite search engine is [Duck Duck Go](https://duckduckgo.com).

### Adding Titles

You can optionally add a title for a link. This will appear as a tooltip when the user hovers over the link. To add a title, enclose it in parentheses after the URL.

```{'mod':'code','lang':'markdown'}
My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").
```

The rendered output looks like this (to see it you'll need to hover the mouse cursor over the link):

My favorite search engine is [Duck Duck Go](https://duckduckgo.com "The best search engine for privacy").

### Formatting Links

To emphasize links, add asterisks before and after the brackets and parentheses. To denote links as code, add backticks in the brackets.

```{'mod':'code','lang':'markdown'}
I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).
```

The rendered output looks like this:

I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).

## Reference-style Links

Reference-style links are a special kind of link that make URLs easier to display and read in Markdown. Reference-style links are constructed in two parts: the part you keep inline with your text and the part you store somewhere else in the file to keep the text easy to read.

### Formatting the First Part of the Link

The first part of a reference-style link is formatted with two sets of brackets. The first set of brackets surrounds the text that should appear linked. The second set of brackets displays a label used to point to the link you’re storing elsewhere in your document.

Although not required, you can include a space between the first and second set of brackets. The label in the second set of brackets is not case sensitive and can include letters, numbers, spaces, or punctuation.

This means the following example formats are roughly equivalent for the first part of the link:

- `[hobbit-hole][1]`
- `[hobbit-hole] [1]`

### Formatting the Second Part of the Link

The second part of a reference-style link is formatted with the following attributes:

1. The label, in brackets, followed immediately by a colon and at least one space (e.g., [label]: ).
2. The URL for the link, which you can optionally enclose in angle brackets.
3. The optional title for the link, which you can enclose in double quotes, single quotes, or parentheses.

This means the following example formats are all roughly equivalent for the second part of the link:

- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle 'Hobbit lifestyles'`
- `[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle (Hobbit lifestyles)`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> 'Hobbit lifestyles'`
- `[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> (Hobbit lifestyles)`

You can place this second part of the link anywhere in your Markdown document. Some people place them immediately after the paragraph in which they appear while other people place them at the end of the document (like endnotes or footnotes).

## Link Best Practices

To add an image, add an exclamation mark (!), followed by alt text in brackets, and the path or URL to the image asset in parentheses. You can optionally add a title after the URL in the parentheses.


```{'mod':'code','lang':'markdown'}
![Caption here...]($/_res/ch1-img-mod-example.jpg)
```

The rendered output looks like this:

![Caption here...]($/_res/ch1-img-mod-example.jpg)