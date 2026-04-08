[[toc depth="3"]] 

## Supported Markdown

## Editing Online

The online editing offers some preview capabilities and toolbars with shortcuts to commonly used features like rich text, lists, insert images, links, etc. 

![](http://localhost:5000/static/images/toolbar.png){width="80%"}

### Main Toolbar

First row of toolbar, traditional options for rich text, plus preview, full screen and undo/redo functions


### Bootstrap Toolbar

A collection of commonly used Bootstrap components. Each button will insert at the cursor position the markdown syntax to use the component. 
Since most boostrap components rely on `<div>` tags, the buttons use the `:::` syntax to represent enclosing divs. Nested divs gain one `:` per level. 

##### Example

The [bootstrap card component](https://getbootstrap.com/docs/5.3/components/card/) is documented as: 

```
<div class="card">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card’s content.</p>
    <a href="#" >Go somewhere</a>
  </div>
</div>
```

To obtain the same in markdown:

###### First Step: insert the card component using the [[icon:card-text]] button 


:::: row
::: col-md-6
**Markdown:**

```
:::: card
::: card-body
**Card Title**

Card content goes here.
:::
::::
```


:::

::: col-md-6

**Preview:**

:::: card
::: card-body
**Card Title**

Card content goes here.
:::
::::

:::
::::

###### Second Step: modify the content of the Card

:::: row
::: col-md-6

**Markdown:**

```
::: card
:::: card-body

##### Card Title

::::: card-text
Some quick example text to build on the card title and make up the bulk of the card’s content.
:::::

[Go Somewhere](https://localhost:5000)

::::
:::
```


:::

::: col-md-6

**Preview:**

::: card
:::: card-body

##### Card Title

::::: card-text
Some quick example text to build on the card title and make up the bulk of the card’s content.
:::::
[Go Somewhere](https://localhost:5000)

::::
:::

:::
::::




## Plugins

The plugins are used to extend the functionality of the wiki. Most of them are accessible through the use of `tags`.
For now there are only a few supported.  

- `[[draw]]` Allows you to add an **interactive drawio drawing** to the wiki.  
- `[[info]]`, `[[warning]]`, `[[danger]]`, `[[success]]` Adds a nice **alert message**.
- `[[ page: some-page ]]` Allows to show an other page in the current one.

[[#]] Go Somewhere

## Latex

It's possible to use latex syntax inside your markdown because the markdown is first converted to latex and after that to html. This means you have a lot more flexibility.

### Change image size
```
![](https://i.ibb.co/Dzp0SfC/download.jpg){width="50%"}
```
![](https://i.ibb.co/Dzp0SfC/download.jpg){width="50%"}

### Image references
```
![\label{test}](https://i.ibb.co/Dzp0SfC/download.jpg){width="50%"}

Inside picture \ref{landscape picture} you can see a nice mountain.

```
![picture \label{landscape picture}](https://i.ibb.co/Dzp0SfC/download.jpg){width="50%"}

Clickable reference in picture \ref{landscape picture}.

### Math
```
\begin{align}
y(x) &= \int_0^\infty x^{2n} e^{-a x^2}\,dx\\
&= \frac{2n-1}{2a} \int_0^\infty x^{2(n-1)} e^{-a x^2}\,dx\\
&= \frac{(2n-1)!!}{2^{n+1}} \sqrt{\frac{\pi}{a^{2n+1}}}\\
&= \frac{(2n)!}{n! 2^{2n+1}} \sqrt{\frac{\pi}{a^{2n+1}}}
\end{align}
```
\begin{align}
y(x) &= \int_0^\infty x^{2n} e^{-a x^2}\,dx\\
&= \frac{2n-1}{2a} \int_0^\infty x^{2(n-1)} e^{-a x^2}\,dx\\
&= \frac{(2n-1)!!}{2^{n+1}} \sqrt{\frac{\pi}{a^{2n+1}}}\\
&= \frac{(2n)!}{n! 2^{2n+1}} \sqrt{\frac{\pi}{a^{2n+1}}}
\end{align}

```
You can also use $inline$ math to show $a=2$ and $b=8$
```
You can also use $inline$ math to show $a=2$ and $b=8$

And many other latex functions.

## Converting the files

Open the wiki folder of your instance.  

|- static  
|- templates  
|- **wiki** $\leftarrow$ This folder  
|- wiki.py  

In this folder all the markdownfiles are listed. Editing the files will be visible in the web-version.  

|- homepage.md  
|- How to use the wiki.md  
|- Markdown cheatsheet.md  

The advantage is that u can use the commandline to process some data. For example using pandoc:
```
$ pandoc -f markdown -t latex homepage.md How\ to\ use\ the\ wiki.md -o file.pdf --pdf-engine=xelatex
```
This creates a nice pdf version of your article.  Its possible you have to create a yml header on top of your document to set the margins etc better
```
---
title: titlepage
author: your name
date: 05-11-2020
geometry: margin=2.5cm
header-includes: |
        \usepackage{caption}
        \usepackage{subcaption}
lof: true
---
```
For more information you have to read the pandoc documentation.

[Using the version control system](/Using the version control system)
