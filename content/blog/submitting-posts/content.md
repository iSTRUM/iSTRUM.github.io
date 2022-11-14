+++
fragment = "content"
weight = 100
summary = "Overview of how to submit new blog posts."
date = "2022-11-14"

display_date = true
+++

## Overview 

This post includes instructions for:

* [Creating and submitting a new post](#creating-a-new-post)
* [Formatting your markdown](#markdown-header)
* [Including images](#including-images)
* [Including math](#including-math)


## Creating a new post 

Blog posts are written in markdown (see [here](https://itsfoss.com/markdown-guide/) for a nice introduction). There are two ways to write and submit a new post: via github issues or via a github pull request. 
 
### submission via issue 

Start a [new issue](https://github.com/TRANSIENTproject/TRANSIENTproject.github.io/issues/new) and title it `New Post: <your title>`. Write your post directly in the issue! You can upload images and write in standard markdown. When ready, click `Submit New Issue` and a maintainer will help to get port the post over to a pull request.

[top](#overview)

### submission via pull request 

Fork the repository and clone it locally. 

Each blog post has its own folder in `/content/blog/`. Once the markdown folder is merged into the github repository, it will automatically get picked up and rendered. So to write a new post, you need to:

1. create a new branch for your post:
```
    $ git branch -b my_new_post
```
2. add a new folder to  `/content/blog/`
3. add two files: `index.md` and `content.md`. Note that both files rely on markdown headers in a particular syntax (see the following section)
4. write your post.
5. commit your `.md` (and any image files that you added).
6. push your branch to your fork and open a pull request! 

[top](#overview)

## markdown header

for a new post to get picked up, both the `index.md` and `content.md` file have to have a proper header. At the top of the `index.md` file, paste the following and edit: 

```
+++
title = "Your blog post title!"
date = "2020-11-14"
+++
```

The rest of this file will always remain blank. 

At the top of `content.md` add:

```
+++
fragment = "content"
weight = 100
summary = "Overview of how to submit new blog posts."
date = "2022-11-14"
+++
```

The `summary` entry will be displayed at https://istrum.github.io/blog . Make the `date` field match the `index.md` file. Do not edit the `fragment` or `weight` fields. 

And that's it! You're now ready to write your post in `content.md`.

Note that if you're new to markdown, you can also look at the source code for this post to see some examples for headers, links and more. 

[top](#overview)

## Including images

To include images that exist somewhere on the web, you can use 

```
![Alt text](https://www.yoururl.com/nice.png "a title")
```
&nbsp;

If you are writing your blog post locally to submit as a pull request, you'll have a couple extra steps. First create a folder in `/static/images/blog/` for your post and add your images to that folder. Then to embed the images in the markdown, you'll reference the images with:

```
![Alt text](/images/blog/your_post/figure_1.png "a title")
``` 
&nbsp;

Note that the image path must start with `/images/`, not `/static/`. For example, for **this** post, there is a corresponding folder, `static/images/blog/submitting-posts/` where the `VBRsimpleFlowchart.png` figure exists. To add it here:

```
![flow chart showing the VBRc](/images/blog/submitting-posts/VBRsimpleFlowchart.png "VBRc flowchart")
``` 

&nbsp;

![flow chart showing the VBRc](/images/blog/submitting-posts/VBRsimpleFlowchart.png "VBRc flowchart")


[top](#overview)

## Including math 

The blog allows mathjax expressions (very similar to latex). Note that if you're writing your post as a github issue, the math will not render in preview mode.

For equation blocks, you wrap with `$$`. 

for example

`$$ x = \phi $$` 

renders as 

$$ x = \phi $$

For multi-line, aligned equations use `eqnarray` with `&=&` to align around the `=`. Separate lines with `\\\\`: 

```
$$
\begin{eqnarray} 
\frac{\partial{T}}{\partial{t}} + V \cdot \nabla{T} &=& \kappa \nabla ^2 T \\\\
\rho \frac{DV}{Dt} &=& - \nabla p + \eta \nabla^2 + \rho g \\\\
\nabla \cdot {V} &=& 0 \\\\
\end{eqnarray}
$$
```

renders as 

$$
\begin{eqnarray} 
\frac{\partial{T}}{\partial{t}} + V \cdot \nabla{T} &=& \kappa \nabla ^2 T \\\\
\rho \frac{DV}{Dt} &=& - \nabla p + \eta \nabla^2 + \rho g \\\\
\nabla \cdot {V} &=& 0 \\\\
\end{eqnarray}
$$


For inline equations, use `\\(` and `\\)`. So `\\(x=\phi\\)` will render as \\(x=\phi\\).

[top](#overview)

## Testing the web-rendering locally 

If you want to see what your new post will look like when it's fully rendered, you'll need to set up a development environment for the blog.

First, install `hugo` **extended edition** following [instructions at gohuo.io](https://gohugo.io/installation/) (note that the hugo theme we use here requires the extended, not the standard hugo!).

Now, fork https://github.com/iSTRUM/iSTRUM.github.io and clone your fork locally, being sure to enable initialize submodules:

```
$ git clone --recurse-submodules git://github.com/YOURUSERNAME/iSTRUM.github.io.git
```

Now you should be able to locally build and serve the full website with:

```
$ cd iSTRUM.github.io
$ hugo server
```

after which the website should be avaialbe to view at [http://localhost:1313](http://localhost:1313).


[top](#overview)
