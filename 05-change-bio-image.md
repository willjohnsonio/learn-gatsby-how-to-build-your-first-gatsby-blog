## Changing the bio image

In the `bio.js` file there is an `Image` component that comes from `data.avatar.childImageSharp.fixed` which comes from the BioQuery GraphQL Query.

```js
 <Image
        fixed={data.avatar.childImageSharp.fixed}
        alt={author}
        style={{
          marginRight: rhythm(1 / 2),
          marginBottom: 0,
          minWidth: 50,
          borderRadius: `100%`,
        }}
        imgStyle={{
          borderRadius: `50%`,
        }}
      />
```

The image query callled avatar is using a relative path `"/profile-pic.jpg/"`

```js
const Bio = () => {
  const data = useStaticQuery(graphql`
    query BioQuery {
      avatar: file(absolutePath: { regex: "/profile-pic.jpg/" }) {
        childImageSharp {
          fixed(width: 50, height: 50) {
            ...GatsbyImageSharpFixed
          }
        }
      }
```

Go to **content**>**assets** and that's where you'll find the `profile-pic,jpg` file. If you don't have an image in the assets folder, place one there and go back to `bio.js` and change `profile-pic.jpg` to your file name. In the stream it was `gatsby-icon.png`

```js
const Bio = () => {
  const data = useStaticQuery(graphql`
    query BioQuery {
      avatar: file(absolutePath: { regex: "/pgatsby-icon.png/" }) {
        childImageSharp {
          fixed(width: 50, height: 50) {
            ...GatsbyImageSharpFixed
          }
        }
      }
```


