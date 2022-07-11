# Gatsby Provision Contentful

This package is to be used for provisioning Contentful data models and content associated with a Gatsby site.

When included as a dependency to your Gatsby site, and configured correctly, it can be used in two contexts — within Gatsby Cloud and locally.

# Usage

First, install this package as a dependency:

```shell
   npm install --save-dev gatsby-provision-contentful
```

or for the yarn users:

```shell
  yarn add --dev gatsby-provision-contentful
```

Next, convention dictates that this package be used in conjunction with the npm script named `gatsby-provision`. It also **requires** the path to the Contentful export JSON file as an argument to function. For example:

```json
// package.json
"scripts": {
  "start": "gatsby develop",
  "test": "jest",
  ...
  "gatsby-provision": "gatsby-provision-contentful --contentful-data-path='./data.json'"
}
```

Optionally, you may include the SPACE_ID and MANAGEMENT_TOKEN as arguments like so:

`gatsby-provision-contentful --contentful-data-path='./data.json' --space-id=$CONTENTFUL_SPACE_ID --management-token=$CONTENTFUL_MANAGEMENT_TOKEN`

## Cloud usage

The easiest way for a `gatsby-provision` script to work in Gatsby Cloud is for you to use Deploy Now. If you are using this package in a template repository you intend other's to re-use, consider adding a Deploy Now button to the README like so:

[![Deploy to Gatsby](https://www.gatsbyjs.com/deploynow.png "Deploy to Gatsby")](https://www.gatsbyjs.com/dashboard/deploynow?url={YOUR_GITHUB_REPO_URL})

When adding a site with a `gatsby-provision` script in the Deploy Now flow, Gatsby Cloud will detect the script when you [Quick Connect](https://support.gatsbyjs.com/hc/en-us/articles/1500000965601-Connecting-to-Contentful-with-Quick-Connect) to the suggested Contentful integration and populate the necessary environment variables for the script to run successfully.

If for whatever reason you choose not to Quick Connect, for the purposes of `gatsby-provision-contentful`, both `CONTENTFUL_SPACE_ID` and `CONTENTFUL_MANAGEMENT_TOKEN` environment variables are required.

## Local usage

When running the `gatsby-provision` locally, you will be prompted for environment variables if they are not found on the current process. Additionally, after provisioning your Contentful space, the script will generate a `.env.development` and an `.env.production` file, populated with the environment variables values you provided.
