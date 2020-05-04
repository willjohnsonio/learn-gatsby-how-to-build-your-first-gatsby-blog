## Create your own blog post

To create your own blog post got to you project files in your IDE and go to content>blog. Inside of the blog folder there are folders named the same each blog post.

Inside the folders for the blog post there is a markdown file with some text and **frontmatter**

To create your own blog post use the same structure as the post there are there by default

Create a new folder `my-first-coding-project`

Inside of that folder create a `index.md` file and copy the **frontmatter** from one of the default post and change it to what we want.

👍 **Frontmatter allows you to have descriptive information that get picked up later**

`index.md`

```markdown
---
title: My FIrst Coding Project
date: 2020-05-04
description: "Let's Learn Gatsby"
---
```

Save then refresh and `localhost:8000` will hot reload and show your new blog post.

You can make content inside the index file by writing in **markdown**

[Markdown Cheatsheet](https://www.markdownguide.org/cheat-sheet/)

👍 The `title` from the frontmatter is an `h1` so any header below it should be a `h2` for accessibility 

You can code to your blog post by typing 3 back ticks then the programming language name. And typing you code in another anohter set of back ticks.

```markdown
```javascript
let name = "Coder"
```


The syntax hightling and styling of the code snippet is possible because of a Gatsby plugin called [gatsby-remark-prismjs](https://www.gatsbyjs.org/packages/gatsby-remark-prismjs/#required-pick-a-prismjs-theme-or-create-your-own). 

You can view your plugin inside of the `gatsby-config.js` file

```javascript
.
.
.
plugin: [
.
.
`gatsby-remark-primjs`,
.
.
],
.
.
.
```

Prism has different theme so you can chage the look/theme of your syntax hightling. You can chnage the theme by going to the `gatsby-browser.js` file and changing the name of what your importing from prism.

```javsacript
import "prismjs/themes/prism-okadia.css"
```

🌟 **Here's the [list of built in themes](https://github.com/PrismJS/prism/tree/1d5047df37aacc900f8270b1c6215028f6988eb1/themes)**
