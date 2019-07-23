---
title: "Maintain and customize this site"
linkTitle: "Maintain and customize"
weight: 5
date: 2019-07-11
description: >
  Understand how to maintain and customize this documentation site.
---

{{% alert title="Note" %}}
This topic is for documentation site maintainers only!
{{% /alert %}}

If you are a maintainer of this documentation site, this topic includes all the information you need to maintain and customize the site.

## Before you start

* Complete the steps in [Set up and work locally](setup_work_locally)

## Overview of tools

This documentation site uses the following tools:

* GitHub - All source files are stored in a Github repo.
* Hugo - The documentation site is built using the Hugo static site generator.
* Docsy - The documentation site uses the Docsy documentation theme from Google.
* Netlify - The site is deployed on Netlify. Deployments are triggered by pushes to GitHub.
* Netlify CMS - Provides a WYSIWYG view of documentation pages.

<!--- TODO Add info about TravisCI, linters, recommended editors --->
<!--- TODO Add info about customizations already done --->

## Overview of config files

This following configuration files can be found in the site root:

* `config.toml` - Hugo and Docsy theme configuration
* `netlify.toml` - Netlify deployment configuration
* `static/admin/config.yml` - Netlify CMS configuration

## Update the Docsy theme

The Docsy theme is installed in this site's git repo as a git submodule. To update the theme with the latest commits from the [Docsy GitHub repo](https://github.com/google/docsy):

1. In Git CLI, navigate to the root of the local repo and checkout **master**. For example:

    ```
    cd improve-the-docs
    git checkout master
    ```

2. To update the submodule, run:

    ```
    git submodule update --remote
    ```

3. Add and then commit the change:

    ```
    git add .
    git commit -m "Updating Docsy theme submodule"
    ```

4. Push the commit to your project repo. For example:

    ```
    git push
    ```

5. Tell  all project maintainers to run:

    ```
    git checkout master
    git pull
    git submodule update --recursive
    ```

## Customize the Docsy theme

This section explains how to customize various elements of the Docsy theme.

### Add code for Netlify CMS

To add the required code for Netlify CMS to the `head` and end of the `body` sections of each page, create the files `layouts/partials/hooks/head-end.html` and `layouts/partials/hooks/body-end.html` and add the code in those files. For details, see [the Docsy instructions](https://docsydocs.netlify.com/docs/adding-content/lookandfeel/#add-code-to-head-or-before-body-end).

### Change colors and fonts

To change the theme colors and fonts, modify the file `assets/scss/_variables_project.scss` as detailed in [the Docsy instructions](https://docsydocs.netlify.com/docs/adding-content/lookandfeel/).

### Change the logo and background images

To change the logo, add a logo file as `assets/icons/logo.svg`. This overrides the theme logo.

To change the background image on the home page (`content/en/_index.html`) add an image containing `background` in the file name to the `content/en/` folder, for example, `content\en\featured-background.jpg`.

For more details, see [the Docsy instructions](https://docsydocs.netlify.com/docs/adding-content/iconsimages/).

### Remove the About section

To remove the About section in the main navigation, delete the folder `content\en\about` and set the following parameter in `config.toml`:

```
footer_about_disable = true
```