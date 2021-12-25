<p align="center">
  <a href="https://wodo.io/" target="blank"><img src="https://github.com/wodo-platform/wg-web-ui/blob/master/app/img/_src/branding/logo_purple.png" width="320" alt="Wodo Platform" /></a>
</p>

<div align="center">
<h2> Wodo Platform Nft API Definitions </h2>
</div>

<div align="center">
  <h4>
    <a href="https://wodo.io/">
      Website
    </a>
    <span> | </span>
    <a href="#">
      Product Docs
    </a>
    <span> | </span>
    <a href="#">
      Architecture Docs
    </a>
    <span> | </span>
    <!-- <a href="#"> -->
    <!--   CLI -->
    <!-- </a> -->
    <!-- <span> | </span> -->
    <a href="#/CONTRIBUTING.md">
      Contributing
    </a>
    <span> | </span>
    <a href="https://twitter.com/wodoio">
      Twitter
    </a>
    <span> | </span>
    <a href="https://t.me/wodoio">
      Telegram
    </a>
    <span> | </span>
    <a href="https://discord.gg/fbyns8Egpb">
      Discourd
    </a>
    <span> | </span>
    <a href="https://wodoio.medium.com/">
      Medium
    </a>
    <span> | </span>
    <a href="https://www.reddit.com/r/wodoio">
      Reddit
    </a>
  </h4>
</div>

<h3> Table of Contents </h3> 

- [About](#about)
- [Publish The Module as NPM Package Locally](#publish-the-module-as-npm-package-locally)
- [Adding wp-nft-api dependency](#adding-wp-nft-api-dependency)
- [Running the app](#running-the-app)
- [CI and Github Workflows](#ci-and-github-workflows)
- [Next Steps](#next-steps)

----

## About

API (application programming interface) definitions for NFT capabilities in the wood platform. The Platform NFT APIs define a standard way of NFT integration into the wodo platform. Any developer can implement and plug any kind of NFT integration as NFT engine implementations. Out of the box, the wodo platform has a variety of NFT integration implementations.The API implementations also adhere to the industry standards, Once NFT engines are implemented and integrated into the wodo platform, all functionality and capabilities are made available to the public world (developers, game developers, 3rd party companies) via public APIs of the wodo platform

## Publish The Module as NPM Package Locally

You may need to publish npm packages from your local dev env in order to speed up development process. It is sort of workaround and you should do clean-up your published package versions. Official github actions will take care of package publishing eventually.

Please follow the steps below to publish wp-nft-api npm package from your local development environment.

```bash
npm login --scope=@wodo-platform --registry=https://npm.pkg.github.com
```

in your terminal and you’ll be prompted to provide the following. Enter your github username, access token and wodo-platform email:

```bash
Username: YOUR_GITHUB_USERNAME
Password: YOUR_GITHUB_TOKEN
Email (this IS public): wodo-platform@users.noreply.github.com
```

Once you log in successfully, you will see the messafe below:

```bash
Logged in as your_git_user to scope @wodo-platform on https://npm.pkg.github.com/.
```
Publish the package:

```bash
npm publish
```

Verif that wp-nft-api package has been published successfully with the correct version you provided in package.json file. Go to the page below and make sure that your packge is listed on the  published artifact list

```
https://github.com/orgs/wodo-platform/packages
```

> You should increase version number when you need to re-publish a new package version.

Once the package is published, you can add it to the dependencies list in package.json file. In order to retrieve the dependency, you must run **"npm login --scope=@Ywodo-platform --registry=https://npm.pkg.github.com
"** command at least once in your command prompt.

```
"dependencies": {
        "@wodo-platform/wp-nft-api": "1.0.0",

  }
```

More details can be found on <a href="https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-npm-registry"> this page </a>

##  Adding wp-nft-api dependency

To be able to add wp-nft-api as npm dependency, you need to authenticate to git remote npm package repository by logging in to npm, use the npm login command, replacing USERNAME with your GitHub username, TOKEN with your personal access token, and PUBLIC-EMAIL-ADDRESS with your email address.

If GitHub Packages is not your default package registry for using npm and you want to use the npm audit command, we recommend you use the --scope flag with the owner of the package when you authenticate to GitHub Packages.

```bash
$ npm login --scope=@wodo-platform --registry=https://npm.pkg.github.com --u your_git_user --p your_token 
```

Once you login successfully, you can run "npm install" command and start to develop your features. 

To run the same steps in the gitflow actions we need to create a secret in org level and set a personal access token as secret value so that when we run a repository, it can reach npn package regidtery of another private repository. GITHUB_TOKEN is generated by the gitflows per repository. It can not access to other private repos. We have WODO_TOKEN storing Serhat's personal access token as value today. TODO: It will be fixed later. 

Granting additional permissions
If you need a token that requires permissions that aren't available in the GITHUB_TOKEN, you can create a personal access token and set it as a secret in your repository:

Use or create a token with the appropriate permissions for that repository. For more information, see "Creating a personal access token."
Add the token as a secret in your workflow's repository, and refer to it using the ${{ secrets.SECRET_NAME }} syntax. For more information, see "Creating and using encrypted secrets."

https://docs.github.com/en/actions/security-guides/automatic-token-authentication#using-the-github_token-in-a-workflow



## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```


## CI and Github Workflows

In order to build and package your repo through CI/CD, please have a a look at the file .github/workflows/pipeline.yml under the root project folder. It is preconfigured githubflow. Whenever you push a change onto the main branch, it is triggered. It will be improved to be able to package and release artifacts based on a release process later.

## Next Steps

Once you compose your new repo, you can create helm charts in wodo-helm-charts repo then conitinue with local deployment and official CI/CD gitops deployment. Please refer to Wodo Platform Local Dev Environment guide.
