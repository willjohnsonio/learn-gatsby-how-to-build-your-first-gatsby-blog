## Adding an Image to the page

**This was a request from the chat**

First you need to go is install is `gatsby-image` by running `npm install gastby-image` in the terminal

Then go to `gatsby-config.js` and add `gastby-image` to your plugins

In src > pages > index.js add `import Img from "gatsby-image"` to get to use the `Img` JSX tag

We'll use example in the `bio.js` component copy the query and paste it into the `pageQuery` in `index.js`

```js
  query BioQuery {
      avatar: file(absolutePath: { regex: "/gatsby-icon.jpg/" }) {
        childImageSharp {
          fixed(width: 50, height: 50) {
            ...GatsbyImageSharpFixed
          }
        }
      }
```

Once it's added change `fixed` to `fluid` and remove width and height and change `GatsbymageShrapFixed` to `GatsbymageShrapFluid`

```js
      avatar: file(absolutePath: { regex: "/gatsby-icon.jpg/" }) {
        childImageSharp {
          fluid {
            ...GatsbyImageSharpFluid
          }
        }
      }
```

You can then copy `avatar` key and paste it into the GraphQL Playground

To make sure you're getting the image you can replace `...GatsbyImageSharpFluid`  with `src` in the query

`...GatsbyImageSharpFluid` pulls a rendered version of the image and that doesn't work in th GraphQL playground 


```js
      avatar: file(absolutePath: { regex: "/gatsby-icon.jpg/" }) {
        childImageSharp {
          fluid {
           src
          }
        }
      }
```

**In the query `absolutePath` is not relative to where the `index.js` is. It's relative to the assets folder in the filesystem**


Back in `index.js` add the `Img` JSX tag right under `<Bio />` tag

```html
<Bio />
<Img fluid={data.avatar.childImageShap.fluid}
```



## [Gatsby Image Docs](https://www.gatsbyjs.org/packages/gatsby-image/)
