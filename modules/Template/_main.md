# Summary

This ebook app is designed by Mr. David Chen, who lecturers at the Department of Electrical and Communication Engineering, to implement a more efficient way to distribute course content in environments where network connectivity is deficient.

The App provides the following set of functions to address the challanges of implementing online teaching within the campus:

## Speech-synthesis services

High-quality **speech-synthesis services** to alleviate the need for video recording lectures.
    
Video files require hundreds of **Megabytes** to store. On the other hand, standard text files occupy far lesser space (within only tens of **Kilobytes**). Also, a wholesome bundled module, including linked images, vector graphics diagrams, and parametric animation, can be compiled to less than one-tenth of the size of video lecture files. This way both the student and lecturer will waste less time on uploading and downloading of course content, while lecture can be carried out through the synthetic voice reader. Hear an example below:

`{'mod':'speak'}` "The PNG University of Technology, is the best university in Papua New Guinea"

> `{'mod':'tag','type':'tip'}` 
> 
> You may also select different voices from the **Narrator** drop-down menu at the top left corner of the screen. These functions may improve learning as the learning no longer need to put up with delicate accents or low speech volumes.

## Math equation rendering

ASCIIMath and Latex-syntax math formulae are rendered to produce a clean and visually appealing depiction of math equations. They can either draw in sections like this:
    
```{'mod':'math','tex':true}
\begin{multline}
\begin{split}
x & = {-b \pm \sqrt{b^2-4ac} \over 2a}\\
-{x \over b} & = {1 \over 2ab} \pm {\sqrt{b^2-4ac} \over 2a}\\
-{x \over b} - {1 \over 2ab} & = \pm {\sqrt{b^2-4ac} \over 2a}\\
\end{split}
\end{multline}
```

## built-in syntax highligthing

Provide syntax highlighting for different programming languages. Below is an example for displaying javascript code with different sections of the code highlighted:

```{'mod':'code','lang':'javascript','highlight':'1,3-5,7-9'}
window.gCodebockHandlers = {
    "math": function(code, configJSON, isInline)
    {
        vRenderedMath = MathJax.tex2svg(code);
        vContainer = document.createElement("div");
        vContainer.appendChild(isInline ? vRenderedMath.firstChild : vRenderedMath);
        return vContainer.innerHTML;
    },
    "code": function(code, configJSON, isInline)
    {
        vRenderedText = Prism.highlight(code, Prism.languages.javascript, configJSON.lang);
        return isInline ? "<code>"+vRenderedText+"</code>" : "<pre class=\"language-markup\">"+vRenderedText+"</pre>"
    }
}
```

## UML Diagramming via *Mermaid.js*

Mermaid is a tool that generates diagrams and charts, from markdown-inspired text definitions

This allows for simplified generation and updating of even the most complex diagrams and charts, while avoiding time-damanding and heavy tools like visio.

mermaid, is a simple markdown-inspired script language for generating charts from text-definitions, via javascript. As such, using it cuts the times it takes to create, modify and render diagrams.

### Example: Flowcharts

```{'mod':'uml'}
flowchart TB
    c1-->a2
    subgraph one
    a1-->a2
    end
    subgraph two
    b1-->b2
    end
    subgraph three
    c1-->c2
    end
    one --> two
    three --> two
    two --> c2
```

### Example: Sequence Diagram

```{'mod':'uml'}
sequenceDiagram
    autonumber
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

For more information regarding the use of diagram syntaxes please refer to [Mermaid-js](https://mermaid-js.github.io/)

## Embedded bitmaps Images

For all other pictorial materials, they can be saved as `'.jpg'`, or `'.png'` format as it is shown below:

`{'mod':'img','url':'$/_res/ch1-img-mod-example.jpg'}`

## Need more functions?
Undoubtedly, once you are accustomed to this tool, later discoveries of functional deficiencies may occur and wish the author to address them. To do so, please contact david.chen@pnguot.ac.pg.

