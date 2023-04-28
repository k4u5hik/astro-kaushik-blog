---
author: Kaushik Chemburkar
pubDatetime: 2023-02-25T09:02:01+11:00
title: Markdown
postSlug: markdown
featured: false
draft: false
tags:
  - markdown
ogImage: ""
description:
  Extra markdown tips.
---

# Markdown

I shall skip the basic syntax, most of it you can find in the [reference](#reference). I will add some tips that I do not use frequently enough but ought to.

## Coloured Text

<font color="red">This text is red!</font>

```html
<font color="red">This text is red!</font>
```

### To-do List / Checkbox

- [ ] Mercury
- [x] Venus
- [x] Earth (Orbit/Moon)
- [x] Mars
- [ ] Jupiter
- [ ] Saturn
- [ ] Uranus
- [ ] Neptune
- [ ] Comet Haley

```markdown
- [ ] Mercury
- [x] Venus
- [x] Earth (Orbit/Moon)
- [x] Mars
- [ ] Jupiter
- [ ] Saturn
- [ ] Uranus
- [ ] Neptune
- [ ] Comet Haley
```

## Table Alignment

You can align text in the columns to the left, right, or center by adding a colon (:) to the left, right, or on both side of the hyphens within the header row.

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
| Text1.      | Text2       | And more      |

```markdown

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
| Text1       | Text2       | And more      |

```

## Table of content / Internal Links

```markdown
## Content

* [Chapter 1](#chapter-1)
* [Chapter 2](#chapter-2)

## Chapter 1 <a name="chapter-1"></a>

Some text here.  
Some text here.
Some text here.

## Chapter 2 <a name="chapter-2"></a>

Some text here.  
Some text here.
Some text here.
```

## Reference Links

[I'm an inline-style link](https://www.somewebsite.com)

[I'm an inline-style link with title](https://www.somewebsite.com "somewebsite's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself]

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.somewebsite.org
[1]: http://somewebsite.org
[link text itself]: http://www.somewebsite.com

```markdown
[I'm an inline-style link](https://www.somewebsite.com)

[I'm an inline-style link with title](https://www.somewebsite.com "somewebsite's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself]

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.somewebsite.org
[1]: http://somewebsite.org
[link text itself]: http://www.somewebsite.com
```

## Comments

The comment is below this line

[//]: # (This is a comment and will not be seen in the output)
<!-- This content will not appear in the rendered Markdown -->

The comment is above this line

```markdown
[//]: # (This is a comment and will not be seen in the output)
[//]: # (This is a comment and will not be seen in the output)
<!-- This content will not appear in the rendered Markdown -->
```

## Adding Footnotes

Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.

```markdown
Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
```

## Continue numbered list

Use four spaces to indent content between bullet points or indent the second paragraph by at least 1 space.

1. item 1
2. item 2

    ```sh
    Code block
    ```
3. item 3

```markdown
1. item 1
2. item 2

    ```
    Code block
    ```
3. item 3
```

## Resources<a name="resources"></a>

- [Dillinger.io](https://dillinger.io/): Very good online markdown editor
- [Obsidian](https://obsidian.md/): Very good knowledge management software.
- [Free Book Format](http://manuscripts.github.io/): Write Books in Plain Text

## Reference<a name="reference"></a>

- [Markdown Guide](https://www.markdownguide.org/)
- [Daring Fireball: Markdown](https://daringfireball.net/projects/markdown/)
- [Awesome Markdown](https://github.com/mundimark/awesome-markdown)
- [Github Flavoured Markdown](https://github.github.com/gfm/#what-is-github-flavored-markdown-)

## Footnotes
