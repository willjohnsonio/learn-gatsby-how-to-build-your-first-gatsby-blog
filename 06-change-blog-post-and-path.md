## Change from chronological order to to alphabetical order

Inside of **src**>**pages** there is an `index.js` file

Look at `pageQuery` inside of `allMarkdownRemark(sort:` replace the fields of `[frontmatter____date], order: DESC` with `[frontmatter____title], order: ASC`. This will sort by the title in our markdown files frontmatter

```js
allMarkdownRemark(sort: { fields: [frontmatter___title], order: ASC }) {
      edges {
        node {
          excerpt
          fields {
            slug
          }
```

The URL for each blog post is being auto-genrated based off the folder name we want to change that.

In `gatsby-node.js` the `createPages` hook is being used to pull in the blog post template `./src/templates/blog-post.js` and query everything we need

We're query a `field` called `slug` and when we using it in `createPage` to define he `path`

```js
allMarkdownRemark(sort: { fields: [frontmatter___date], order: DESC }) {
      edges {
        node {
          excerpt
          fields {
            slug
          }
.          
...
 createPage({
      path: post.node.fields.slug,
      component: blogPost,
...      
 ```
To change the path you can add `+ "test"` to end of of just but it the oage wont't show and run `gatsby develop`in the terminal to re-build the site

```js
 createPage({
      path: post.node.fields.slug + "test",
      component: blogPost,
...   
```

Then go to `index.js` and inside of `Link` we have {title} but the to is set to `{node.fields.slug}` add `+ "test" to the end of slug and the next path will appear

```js
 <Link style={{ boxShadow: `none` }} to={node.fields.slug + "test"}>
                    {title}
                  </Link>
```

### Resources


[Gatsby Page Query Docs](https://www.gatsbyjs.org/docs/page-query/)
