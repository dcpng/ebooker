# What is a module?

`{'mod':'speak'}`  An **Ebooker** module is **a folder** or **a zip file** that consist, at minimum, of the following items:

```{'mod':'tree'}
module/
|-- _plugins/
|-- _res/
|-- _main.md
|-- _sidebar.md
`-- module.json
```

- `{'mod':'speak'}` The `_plugins` contains custom javascript plugin modules, for the advanced authors to enchance the functionality of the reader
- `{'mod':'speak'}` The `_res` contains resource files such as pictures and other data-file that content `.md` files may refer to via `'{mod:..}'` or image-links markdown commands.
- `{'mod':'speak'}` The `_main.md` is the first page to be loaded upon opening the module.
- `{'mod':'speak'}` The `_sidebar.md` contains the layout and content of the ToC (Table of Content), which links to other `.md` files.
- `{'mod':'speak'}` The `module.json` contains configuration information on how reader loads the module.

`{'mod':'speak'}` To make life easier, you can start a new project by just copy and paste the content from the `demo` folder, which contains the basic module structure described above.

# The `module.json` file

`{'mod':'speak'}` This file contains information regarding **how the module will be loaded**. 

```{'mod':'code','lang':'javascript'}
{
    "summary": {
        "ui-group": "Information",
        "ui-visible": true,
        "title": "How to use this application?",
    }
}
```

`{'mod':'speak'}` Currently, there are 3 fields that control the ui navigation on opening the module. Below is a table that Summarises the purpose of these files.

| Field name     | Data-type | Purpose                                                   |
| :------------- | :-------: | :-------------------------------------------------------- |
| `"ui-group"`   |  String   | The sidebar heading the module will display under         |
| `"ui-visible"` |  Boolean  | true: if the module link is visible from the main sidebar |
| `"title"`      |  String   | The name of the module to be displayed on the sidebar     |

`{'mod':'speak'}` Here is an example of what it looks like for an given configuration of the `module.json` file:

![]($/_res/01/Module.json.png)

> `{'mod':'tag','type':'tip'}` `{'mod':'speak'}` The displayed text contents (such as this one) can be reloaded by pressing <kbd>F5</kbd>. This is useful during the content developoment stage, where frequent update of `*.md` files occures.

# More Chapters
`{'mod':'speak'}` If you need more chapters, you can simply create more markdown (`*.md`) files in your module directory. For example, if you create a file named `guide.md`, then it is accessible via `'[guide]($/guide.md)'` markdown-link declaration. Please refer to the [markdown]($/03_markdown.md) chapter for more information on the syntaxes of the other markdown statements.

# Sidebar (Table of Content)
`{'mod':'speak'}` The file `_sidebar.md` contains the markdown text for ToC (Table of Content) is displayed. For example, the snippet below:

```{'mod':'code','lang':'markdown'}
<h3> How to Topics: </h3>

* [Summary]($/_main.md)
* [Add a module]($/01_add_mod.md)
* [Create a module]($/02_create_mod.md)
* [Markdown syntax]($/03_markdown.md)
* [Math syntax]($/04_math.md)
* [Diagraming syntax]($/05_uml.md)
```

`{'mod':'speak'}` Will generate the a ToC that look like this:

![]($/_res/01/TocRendered.png)

> `{'mod':'tag','type':'info'}` `{'mod':'speak'}` Each link declaration has 2 parts:
> - The displayed text, which is between the square "[ ... ]" backets
> - The path of the hyperlink to the chapter's markdown file , which is between the round "( ... )" backets.
> For example the `'[Create a module]($/02_create_mod.md)'` displays that link "Create a module" that opens, when clicked, the `02_create_mod.md` chapter file. The `$/` part tells the system that the file is located within the module.

# Package for deployment

`{'mod':'speak'}` For windows 10 users: following these steps to package your ebook module:
1. In file explorer, open the module folder.
2. Select all files and folders from within.
3. Right click on the selection
4. Select the "Compressed (zipped) folder" option to create the packaged module file.

![]($/_res/01/createZipPkg.png)

> `{'mod':'tag','type':'info'}` `{'mod':'speak'}` You can ignore the notice dialog box if it appears since windows can't compress empty folders such the `_plugin` folder.
>
> ![]($/_res/01/WarningDlgEmptyFolder.png)

`{'mod':'speak'}` Once done, you may rename the file however that name **must NOT contain any spaces**. Use underscores (`_`) instead of spaces to delimit words for the file name. The ebook module can now be distributed via attachment through email, Google Classroom, or Moodle.