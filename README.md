<div align="center">

  # Gigacounts Guides

  [**Live Demo →**][demo]

</div>


## Features

<details>
  <summary>
    <i>Click to view features</i>
  </summary>
  <p>

  - Dark / Light Theme Mode
  - Localized UI language
  - Pinned Posts
  - Hierarchical Categories
  - Trending Tags
  - Table of Contents
  - Last Modified Date of Posts
  - Syntax Highlighting
  - Mathematical Expressions
  - Mermaid Diagram & Flowchart
  - Dark / Light Mode Images
  - Embed Videos
  - Disqus / Utterances / Giscus Comments
  - Search
  - Atom Feeds
  - Google Analytics
  - SEO & Performance Optimization

  </p>
</details>

## Documentation

To explore usage, development, and upgrade guide of the project, please refer to
the [Wiki][theme info].


## Requirements

Follow the instructions in the [Jekyll][jekyll-installation] Docs to complete the installation of the basic environment.


## Installing Dependencies

Before running local server for the first time, go to the root directory of your site and run:

```shell
bundle
```

## Usage

### Configuration

Update the variables of ___config.yml__ as needed. Some of them are typical options:

* url
* avatar
* timezone
* lang

### Customizing Stylesheet

If you need to customize the stylesheet, copy the theme’s __assets/css/style.scss__ to the same path on your Jekyll site, and then add the custom style at the end of it.

Starting with version 4.1.0, if you want to overwrite the SASS variables defined in ___sass/addon/variables.scss__, copy the main sass file ___sass/jekyll-theme-chirpy.scss__ into the _sass directory in your site’s source, then create a new file ___sass/variables-hook.scss__ and assign new value.

### Customing Static Assets
Static assets configuration was introduced in version 5.1.0. The CDN of the static assets is defined by file ___data/origin/cors.yml__, and you can replace some of them according to the network conditions in the region where your website is published.

Also, if you’d like to self-host the static assets, please refer to the ][chirpy-static-assets][chirpy-static-assets].

### Running Local Server
You may want to preview the site contents before publishing, so just run it by:

```shell
$ bundle exec jekyll s
```

Or run the site on Docker with the following command:

```shell
$ docker run -it --rm \
    --volume="$PWD:/srv/jekyll" \
    -p 4000:4000 jekyll/jekyll \
    jekyll serve
```


After a few seconds, the local service will be published at http://127.0.0.1:4000.


### Deploymnet

Before the deployment begins, check out the file ___config.yml__ and make sure the url is configured correctly. Furthermore, if you prefer the [project site][project-site] and don’t use a custom domain, or you want to visit your website with a base URL on a web server other than **GitHub Pages**, remember to change the _baseurl_ to your project name that starts with a slash, e.g, _/project-name_.

Now you can choose ONE of the following methods to deploy your Jekyll site.

### Deploy by Using GitHub Actions

There are a few things to get ready for.

* If you’re on the GitHub Free plan, keep your site repository public.
* If you have committed **Gemfile.lock** to the repository, and your local machine is not running Linux, go the the root of your site and update the platform list of the lock-file:

```shell
$ bundle lock --add-platform x86_64-linux
```

Next, configure the Pages service.

1. Browse to your repository on GitHub. Select the tab _Settings_, then click _Pages_ in the left navigation bar. Then, in the **Source** section (under _Build and deployment_), select *[GitHub Actions][github-actions]* from the dropdown menu.

2. Push any commits to GitHub to trigger the _Actions_ workflow. In the _Actions_ tab of your repository, you should see the workflow _Build and Deploy_ running. Once the build is complete and successful, the site will be deployed automatically.

At this point, you can go to the URL indicated by GitHub to access your site.

### Manually Build and Deploy

On self-hosted servers, you cannot enjoy the convenience of **GitHub Actions**. Therefore, you should build the site on your local machine and then upload the site files to the server.

Go to the root of the source project, and build your site as follows:

```shell
$ JEKYLL_ENV=production bundle exec jekyll b
```

Or build the site on Docker:

```shell
$ docker run -it --rm \
    --env JEKYLL_ENV=production \
    --volume="$PWD:/srv/jekyll" \
    jekyll/jekyll \
    jekyll build
```

Unless you specified the output path, the generated site files will be placed in folder **_site** of the project’s root directory. Now you should upload those files to the target server.

---


[jekyll-installation]: https://jekyllrb.com/docs/installation/
[demo]: https://dappsar.github.io/jekyll-g/
[theme info]: https://chirpy.cotes.page/posts/getting-started/
[chirpy-static-assets]: https://github.com/cotes2020/chirpy-static-assets#readme
[project-site]: https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites
[github-actions]: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow