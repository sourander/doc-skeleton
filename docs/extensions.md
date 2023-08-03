# Extensions How-To

Below, you can see a demonstration of all extensions that have been activated in the default `mkdocs.yml` file.

## Syntax highlighting

The code block also demonstrates the copy code, annotation, mark text and keyboard keys functionalities

```python
import os

a = os.name + '-' + 'cat' # (1)
print(a)
```

1.  :cat: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.

Clicking the ==Copy to clipboard== saves you from a tedious ++ctrl+c++ process.

# Admonitions

!!! tip
    You can add longers tips inside their own container blocks using `!!! tip ["Headline"]`, including an optional headline.

!!! question "Exercise: Do it"
    Exercise: It must be done.

??? note
    You can add longers tips inside their own container blocks using `??? <admonition>`.

!!! quote
    The way to get started is to quit talking and begin doing. *--Walt Disney*

# Emoji

Prefer these standard usages for emojis:

| Visual        | Code            | Usage         | Alt. admonition         |
|---------------|-----------------|---------------| ----------------------- |
| :fire:        | `:fire:`        | Short tip     | tip                     |
| :question:    | `:pushpin:`     | Exercise      | question                |
| :exclamation: | `:exclamation:` | Important     | N/A                     |
| :exclamation: | `:exclamation:` | Important     | Long, off the map note. |
| :book:        | `:book:`        | Read more     | quote                   |

 The list of Unicode emoji shortnames can be found at :book: [Emojipedia](https://emojipedia.org/twitter/). 

# Mermaid Graphs

``` mermaid
flowchart LR
    Markdown-->Git-->|magic|Success
```

:book: Check more at [Mermaid Tutorials](https://mermaid.js.org/config/Tutorials.html)