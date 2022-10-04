# Lume base blog example

A starter repository showing how to build a blog with the
[Lume](https://github.com/lumeland/lume) static site generator.

This project started as a fork of
[eleventy-base-blog](https://github.com/11ty/eleventy-base-blog) but adapted to
Lume and with the NetlifyCMS.

## Getting Started

1. Make sure you have [Deno installed](https://deno.land/#installation).
2. Clone this Repository
   `git clone https://github.com/lumeland/base-blog.git my-blog-name`
3. Edit `_data/site.yml`. Specifically have a look at `_config.js` to see if you
   want to configure any option differently. See the
   [Lume documentation site](https://lume.land/).
4. Run Lume with `deno task serve`.

### Implementation Notes

- `about.md` shows how to add a content page.
- `posts/` has the blog posts but really they can live in any directory. The
  `posts/_data.yml` file adds the value for `type` and `layout` fields to all
  posts.
- The `menu` field adds any page to the top level site navigation. For example,
  this is in use on `index.njk` and `about.md`. You can configure the order with
  `menu.order` and the text with `menu.title`.
- `css` files are processed with `postcss` plugin. The imported styles are in
  `_includes/css`
- `img` folder is copied as is, (keeping the same directory structure).
- The blog post feed template is in `feed.xml.njk` and `feed.tmpl.js`.
- This example uses four layouts stored in `_includes/layouts/`:
  - `base.njk`: the top level HTML structure
  - `home.njk`: the home page template (wrapped into `base.njk`)
  - `post.njk`: the blog post template (wrapped into `base.njk`)
  - `tag.njk`: the tag page template (wrapped into `base.njk`)
- `_includes/templates/postlist.njk` is a Nunjucks a reusable template used to
  display a list of all the posts. `index.njk` has an example of how to use it.
- `admin/` has the [NetlifyCMS](https://www.netlifycms.org/) configuration so
  you can edit or create new posts using a friendly CMS.

## Deployment

### Deno Deploy

- [Create a project in Deno Deploy](https://deno.com/deploy) and configure it.
  - Link to your git repository
  - Set the GitHub Actions deployment mode.
- Open the file `.github/workflows/deno_deploy.yml` and edit the following:
  - The `--location` option with the url of the site, for example:
    `--location=https://my-blog.deno.dev`
  - The project name in the `denoland/deployctl` step with the name of your
    project.
- [See a live demo](https://lume-blog.deno.dev)
