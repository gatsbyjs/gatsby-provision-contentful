# Gatsby Provision Contentful

This package is to be used for provisioning Contentful data models and content associated with a Gatsby site.

When included as a dependency, it can be used in two contexts — within Gatsby Cloud and locally. Convention dictates that it be used in conjunction with the npm script named `gatsby-provision`. It also requires the path to the Contentful export JSON file as an argument. For example:

`"gatsby-provision": "gatsby-provision-contentful --contentful-data-path='./data.json'"`

Optionally, you may include the SPACE_ID and MANAGEMENT_TOKEN as arguments like so:

`gatsby-provision-contentful --contentful-data-path='./data.json' --space-id=$SPACE_ID --management-token=$MANAGEMENT_TOKEN`

## Cloud usage

**Note:** Instructions subject to change

In order to use this script in Gatsby Cloud, all environment variables must be provided in the Environment Variables form prior to electing to Provision the Contentful Space in the Deploy Now flow.

## Local usage

When running this locally, you will be prompted for environment variables if they are not found on the current process. Additionally, after provisioning your Contentful space, the script will generate a `.env.development` and an `.env.production` file populated with the provided variables for you.
