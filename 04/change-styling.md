## Change the styling 

Go to the `src` folder and add a new `styles` folder and create a `global.css` file

In this this video select the `html` element and change the `background-color` property to `lightseagreen`

The same way you would write normal css

```css
html {
  background-color: lightseagreen;
}
```

In order for the styled to take affect they need to be imported

Go to `gatsby-browser.js` and type the import statement:

```js
import "./src/styles.global.css"
```
Now change the link color but the current blue has too low of a contrast for accessibiliy

👍 [WebAIM Color Contrast Checker](https://webaim.org/resources/contrastchecker/)


```css
a {
  color: #000052
}
```

## Change the image from Kyle Matthews

Inside of `src/templates/blog-post.js` which get used in `gatsby-node.js` that uses `createPages` React hook that takes the template and creates all of our blog posts (we'll explore this more later)

Back in the the `blog-post.js` template there is a `<Bio />` component inside of the `<footer>` tag

Go to the  `components` folder and open the `bio.js` file inside the component there is a `useStaticQuery` hook that runs a GraphQL query 

🌟 **[Gatsby useStaticQuery Docs](https://www.gatsbyjs.org/docs/use-static-query/)**

In of the GraphQL query we have `siteMetaData` includes author, social, and twitter. 

`siteMetadata` is inside of the `gatsby-config.js` file inside of `module.exports`

```js
module.exports = {
 siteMetadta: {
  title: `Coding Blog`,
  author: `Gatsbee Coder`,
  description: `A blog for learning code`
  ...
  social: {
    twitter: `AskGatsbyJS`,
  },
 }
}
```

Back into `bio.js` there is a `<p>` tag that has the sentence thats included in the bio. Change San Francisco to Gatsbyland and change him to them

```html
<p>Written by Coder Gatsbee who lives and works in GatsbyLand building useful things.</p> 
```




