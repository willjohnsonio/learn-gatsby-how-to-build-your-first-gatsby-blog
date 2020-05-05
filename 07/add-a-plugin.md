# Add A Plugin

To install the reading time plugin go to the terminal and type

```bash
yarn add gatsby-remark-reading-time
```
Once it's installed add it to `gatsby-config.js` since it is a remark plugin the plugin name needs to be added inside `gatsby-remark-transformer`

```js
     resolve: `gatsby-transformer-remark`,
      options: {
        plugins: [
       ........
       ........
       ........
          },
          `gatsby-remark-prismjs`,
          `gatsby-remark-copy-linked-files`,
          `gatsby-remark-smartypants`,
          `gatsby-remark-reading-time`
        ],
      },
    },
```
If you re-run the site suing `gatsby-develop` you get a query error in the browser to go `localhost:8000___graphql` to go to a GraphQl playground. You can test and see if the reading-time plugin is even going to work before to intergrate it in your app.


Inside of `gatsby-node.js` copy the query from `result` that's been awaited and paste it and run it in the GraphQL Playground

```js
  const result = await graphql(
    `
      {
        allMarkdownRemark(
          sort: { fields: [frontmatter___date], order: DESC }
          limit: 1000
        ) {
          edges {
            node {
              fields {
                slug
              }
              frontmatter {
                title
              }
            }
          }
        }
      }
    `
  )
```
Add `readingTime{}` under `slug` and inside of `readingTime{}` type in `text`

```js
  {
        allMarkdownRemark(
          sort: { fields: [frontmatter___date], order: DESC }
          limit: 1000
        ) {
          edges {
            node {
              fields {
                slug
                readingTime{
                text
                }
              }
              frontmatter {
                title
              }
            }
          }
        }
      }
```
To use the the information we got from the GraphQL query we need to pass it go to `createPage` and pass `readingTime: post.node.fields.readingTime.text` under slug

```js
createPage({
      path: post.node.fields.slug,
      component: blogPost,
      context: {
        slug: post.node.fields.slug,
        readingTime: post.node.fields.readingTime.text,
        previous,
        next,
      },
    })
  })
}
```

Go back to `blog-post.js` inside of 'BlogPostTemplate` add `readingTime` to the values currently being extracted right now it's only getting previous and next

```js
const { previous, next, readingTime } = this.props.pageContext
```

Now go down to where were adding the `{post.frontmatter.date}` and add `- {readingTime}`
```html
    <p
       style={{
        ...scale(-1 / 5),
         display: `block`,
         marginBottom: rhythm(1),
         }}
   >
         {post.frontmatter.date} - {readingTime}
   </p>
```

Restart the server by running `gatsby develop` in the terminal


🤔 ## What are Gatsby Plugins? 

[Gatsby Plugin Docs](https://www.gatsbyjs.org/docs/plugins)

🤔 ##  Reading Time Plugin 

[gatsby-remark-reading-time](https://www.gatsbyjs.org/packages/gatsby-remark-reading-time/)
