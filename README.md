<p align="center">
  <a href="https://www.gatsbyjs.com">
    <img alt="Gatsby" src="https://www.gatsbyjs.com/Gatsby-Monogram.svg" width="60" />
  </a>
</p>

<h1 align="center">
  Gatsby Provision Contentful
</h1>

This package is to be used for provisioning Contentful content models and content associated with a Gatsby site. This is a way to include example content that is associated with the site in the repository and allow for others to make copies. A typical use case would be if you're building a Gatsby Starter, or a boilerplate or template site for your own re-use.

When included as a dependency to your Gatsby site, and configured correctly, it can be used in two contexts — within Gatsby Cloud and locally.

# Usage

First, export your Contentful Space's content model and content. You can find instructions on how to do this in [one of Contentful's tutorials](https://www.contentful.com/developers/docs/tutorials/cli/import-and-export/).

Then, install this package as a dependency in the repository you want to enable easy provisioning of data for:

```sh
   npm install --save-dev gatsby-provision-contentful
```

or for the yarn users:

```sh
  yarn add --dev gatsby-provision-contentful
```

Next, convention dictates that this package be used in conjunction with an npm script named `gatsby-provision`. It also **requires** the path to the Contentful export JSON file as an argument to function. For example:

```json
// package.json
"scripts": {
  "start": "gatsby develop",
  "test": "jest",
  ...
  "gatsby-provision": "gatsby-provision-contentful --contentful-data-path='./data.json'"
}
```

Optionally, you may include the Contentful Space ID and Management Token as arguments like so:

`gatsby-provision-contentful --contentful-data-path='./data.json' --space-id=$CONTENTFUL_SPACE_ID --management-token=$CONTENTFUL_MANAGEMENT_TOKEN`

## Cloud usage

The easiest way for a `gatsby-provision` script to work in Gatsby Cloud is for you to use Deploy Now. If you are using this package in a template repository you intend other's to re-use, consider adding a Deploy Now button to the README like so:

[![Deploy to Gatsby](https://www.gatsbyjs.com/deploynow.png "Deploy to Gatsby")](https://www.gatsbyjs.com/dashboard/deploynow?url={YOUR_GITHUB_REPO_URL})

When adding a site with a `gatsby-provision` script in the Deploy Now flow, Gatsby Cloud will detect the script when you [Quick Connect](https://support.gatsbyjs.com/hc/en-us/articles/1500000965601-Connecting-to-Contentful-with-Quick-Connect) to the suggested Contentful integration and populate the necessary environment variables for the script to run successfully.

If for whatever reason you choose not to Quick Connect, for the purposes of `gatsby-provision-contentful`, both `CONTENTFUL_SPACE_ID` and `CONTENTFUL_MANAGEMENT_TOKEN` environment variables are required.

## Local usage

When running the `gatsby-provision` locally, you will be prompted for environment variables if they are not found on the current process. Additionally, after provisioning your Contentful space, the script will generate a `.env.development` and an `.env.production` file, populated with the environment variables values you provided.

## Example

You can see an example of this package in use in the following repositories:

- [gatsby-starter-contentful-homepage](https://github.com/gatsbyjs/gatsby-starter-contentful-homepage)
- [gatsby-starter-contentful-homepage-ts](https://github.com/gatsbyjs/gatsby-starter-contentful-homepage-ts)
- [gatsby-starter-landing-page](https://github.com/gatsbyjs/gatsby-starter-landing-page)
- [starter-gatsby-blog](https://github.com/contentful/starter-gatsby-blog)
