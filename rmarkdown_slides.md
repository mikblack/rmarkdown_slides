Slides in R Markdown
================
Mik Black
30 May 2019

<!-- Run line below in R to render multiple documents: -->

<!-- rmarkdown::render("rmarkdown_slides.Rmd", output_format=c("ioslides_presentation","github_document")) -->

## (R) Markdown May in almost over\!

  - Just making sure that you’ve seen these links:
    
    <https://rmarkdown.rstudio.com/index.html>
    
    <https://rmarkdown.rstudio.com/lesson-1.html>

  - This is a great guide to using R Markdown within the R Studio
    environment.

  - This is also awesome:
    
    <https://bookdown.org/yihui/rmarkdown/presentations.html>

  - Today we’re going to use R Markdown to make some presentation slides
    (just like these ones).

## Slides in R markdown

  - R Studio makes it easy to produce slides using R Markdown.

  - R Markdown renders to four presentation formats:
    
      - [beamer
        presentation](https://bookdown.org/yihui/rmarkdown/beamer-presentation.html)
        - PDF presentations with beamer
      - [ioslides\_presentation](https://bookdown.org/yihui/rmarkdown/ioslides-presentation.html)
        - HTML presentations with ioslides
      - [slidy\_presentation](https://bookdown.org/yihui/rmarkdown/slidy-presentation.html)
        - HTML presentations with slidy
      - [powerpoint\_presentation](https://bookdown.org/yihui/rmarkdown/powerpoint-presentation.html)
        - PowerPoint presentation
      - [revealjs::revealjs\_presentation](https://bookdown.org/yihui/rmarkdown/revealjs.html)
        - HTML presentations with reveal.js

  - We will focus on the `ioslides_presentation`.

<BR><BR> From: <https://rmarkdown.rstudio.com/lesson-11.html>

## New presentation

  - File menu:
      - New File -\> Rmarkdown…
  - Select “Presentation” and click “OK”

<center>

<img src="figures/newfile.png" height="350">

</center>

## Your new document

  - Following the steps on the previous slide will produce a new R
    Markdown *presentation*, complete with some example text and code.
  - It should look suspiciously familiar…
  - What is the difference between this and a R Markdown *document*?

## YAML header

**R Markdown document:**

    ---
    title: "Untitled"
    author: "Mik Black"
    date: "28/05/2019"
    output: html_document
    ---

**R Markdown presentation:**

    ---
    title: "Untitled"
    author: "Mik Black"
    date: "28/05/2019"
    output: ioslides_presentation
    ---

# Let’s see what is in the example slides

## Slide 1 (title slide): code

    ---
    title: "Untitled"
    author: "Mik Black"
    date: "28/05/2019"
    output: ioslides_presentation
    ---

## Slide 2: code

    ## R Markdown
    
    This is an R Markdown presentation. Markdown is a simple formatting
    syntax for authoring HTML, PDF, and MS Word documents. For more 
    details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **Knit** button a document will be generated 
    that includes both content as well as the output of any embedded 
    R code chunks within the document.

## R Markdown

This is an R Markdown presentation. Markdown is a simple formatting
syntax for authoring HTML, PDF, and MS Word documents. For more details
on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that
includes both content as well as the output of any embedded R code
chunks within the document.

## Slide 3: code

    ## Slide with Bullets
    
    - Bullet 1
    - Bullet 2
    - Bullet 3

## Slide with Bullets

  - Bullet 1
  - Bullet 2
  - Bullet 3

## Slide 4: code

    ## Slide with R Output
    
    ```{r cars, echo = TRUE}
    summary(cars)
    ```

## Slide with R Output

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

## Slide 5: code

```` 

## Slide with Plot

```{r pressure}
plot(pressure)
```
````

## Slide with Plot

![](rmarkdown_slides_files/figure-gfm/pressure-1.png)<!-- -->

## Echoing code

  - Note that code is not displayed by default
  - This can be specified per code chunk:

<!-- end list -->

```` 
  ```{r cars, echo = TRUE}
  summary(cars)
  ```
````

  - Or you can define it globally at the top of the file:

<!-- end list -->

```` 
  ```{r setup, include=FALSE}
  knitr::opts_chunk$set(echo = TRUE)
  ```
````

## Let’s make a presentation…

  - File menu:
      - New File -\> Rmarkdown…
  - Select “Presentation” and click “OK”

<center>

<img src="figures/newfile.png" height="350">

</center>

## …and customise it

  - Give it a proper title

  - Click “Knit” to generate the output

  - Click the “Open in Browser” button (at the top of the output page)
    to open the slides in a web browser.

  - Try adding some content - perhaps a slide containing a boxplot:
    
    `boxplot( cars$speed )`

## Inserting an image

  - The following code will add an image to the slide (note, this isn’t
    R code, it’s Markdown, so doesn’t sit in a code chunk):

<!-- end list -->

``` 
  ![some text](figures/img.png)
```

![some text](figures/otago_logo.jpg)

## How I do it

  - Simple HTML code can also be used:

<!-- end list -->

``` 
  <center>
  <img src="figures/otago_logo.jpg" width="400">
  </center>
```

<center>

<img src="figures/otago_logo.jpg" width="400">

</center>

## And here is the newer cooler way…

  - `knitr` now includes a built-in function for this:

<!-- end list -->

```` 
  ```{r, out.width = "400px", fig.align="center"}
  knitr::include_graphics("figures/otago_logo.jpg")
  ```
````

<img src="figures/otago_logo.jpg" width="400px" style="display: block; margin: auto;" />

# Random tricks\!

## Like - what’s with that grey slide?

  - If you use a single hashtag for the slide title, you get a
    grey-background “transition slide”

<!-- end list -->

``` 
  # Random tricks!
```

  - Note that most of my “random tricks” are directly from:
    
    <https://bookdown.org/yihui/rmarkdown/presentations.html>

## Math formulae

  - LaTeX commands can be used to insert equations.

  - Code

<!-- end list -->

``` 
    $\pi(\theta|X) = \frac{f(X|\tha)\pi(\theta)}
                     {\int{f(X|\tha)\pi(\theta)d\theta}}$
```

  - Output:

<center>

\(\pi(\theta|X) = \frac{f(X|\theta)\pi(\theta)}{\int{f(X|\theta)\pi(\theta)d\theta}}\)

</center>

## Size changes

  - You can display the presentation using a wider form factor using the
    widescreen option. You can specify that smaller text be used with
    the smaller option. For example:

<!-- end list -->

``` 
  ---
  output:
    ioslides_presentation:
      widescreen: true
      smaller: true
  ---
```

  - You can also enable the “smaller” option on a slide-by-slide basis
    by adding the .smaller attribute to the slide header:

<!-- end list -->

``` 
  ## Title {.smaller}
```

## Smaller text slide

  - The text on this slide is smaller
  - You could use this if you need to squeeze some more words in…

## Two column layout

    <div class="columns-2">
    
    ```{r, out.width = "300px"}
    knitr::include_graphics("figures/otago_logo.jpg")
    ```
    
    - Bullet 1
    - Bullet 2
    - Bullet 3
    
    </div>

<BR>

<div class="columns-2">

<img src="figures/otago_logo.jpg" width="300px" />

  - Bullet 1
  - Bullet 2
  - Bullet 3

</div>

## Text colour

You can color content using base color classes red, blue, green, yellow,
and gray (or variations of them, e.g., red2, red3, blue2, blue3, etc.).
For example:

    <div class="red2">
    This text is red
    </div>

<div class="red2">

This text is red

</div>
