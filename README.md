# Gatsby-Confluence-EUF

A quick and dirty Gatsby source plugin for retrieving data from everybody's least favourite content editor, Confluence.

[Forked from gatsby-source-confluence - An example site is available on Netlify](https://gatsby-source-confluence.netlify.com)

## Installation

`npm i --save gatsby-confluence-euf`

## Usage

Add the following to your gatsby-config.js file:

```js
module.exports = {
  plugins: [
    "gatsby-plugin-react-helmet",
    {
      resolve: "gatsby-confluence-euf",
      options: {
        hostname: "companyname.atlassian.net",
        auth: "Basic XXX...",
        cql: "ancestor = 534095277",
        limit: 10
      }
    }
  ]
};
```

Please ensure that the following parameters are set:

- hostname (Required): the Confluence base URL to use for all requests
- auth: Your username.password base64 encoded with a `Basic` prefix. Please don't check this in to source control ;)
- cql (Required): a CQL expression to filter out a list of documents
- limit: Defaults to `10`. This is just how many pages to retrieve each time. The plugin wil loop until it has fetched all results from the CQL

## Known issues


- Confluence storage often has macros embedded. Macros that output HTML are handled.
- Only handles pages, not blog posts
- No page tree hierarchy
- url reqrute is for the specifics of this project. You wil have to sort out a better system!
- use gatsby-remote-images to fetch images locally

Pull requests welcome!
