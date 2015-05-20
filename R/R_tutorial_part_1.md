<h2> Quick & Basic R Tutorial </h2>
==================================================
<h3> Getting Started </h3>

Please see the main web-page of R - <a href="http://www.r-project.org">r-project.org</a> - to download R if you don't already have it.  At the R website you can download installation files for Apple Mac OS X, Microsoft Windows PC, and lots of flavors of Linux. Once you have downloaded the installation file then run the file by clicking on it. You should be able to access the R-GUI (graphical user interface) on your computer.

As a reference for the many commands you will come across using R, I like this <a href="http://cran.r-project.org/doc/contrib/Short-refcard.pdf">R Cheat Sheet from the R-project website</a>.

<h4>Writing &amp; Saving Code</h4>

On PCs, you can use the built in R editor but it doesn’t give you any help with writing your code.

On Macs, the built-in R editor is nice for writing and saving code because it gives you some hints through color coding and highlighting.

<h4>Good applications for writing code</h4>

There are several R editing packages that are specially designed for use with R.  I really like the RStudio package. It is compatible with most operating systems. You can download the RStudio editor from <a href="http://www.rstudio.org">rstudio.org</a>.
<ul><li>RStudio organizes your screen so that you can see four windows at the same time. These windows include the console, your code document, a list of objects and a graphic within the same Rstudio window. RStudio can let you know if you have made a mistake in syntax by highlighting code. </li>
<li>When using functions Rstudio will give you help at the prompt (type all or part of the function name and hit tab). This is just like you have at the command line.</li>
<li>The <a href="http://www.rstudio.org">rstudio.org</a> website has good documentation on what the editor does and how to make it work best for your needs.</li></ul>

Some personal recommendations to avoid writing bad code:
<ul><li>I avoid writing all my code directly into the R console because it's difficult to save it in a ’runnable’ format afterwards. This can be done, but it's often easier to experiment in the source console.</li>
<li>Microsoft Word is not a text editor, it's a word processing program.  Programs such as Word may capitalize words or make other changes to your code that are unwanted so if you write your code elsewhere make sure you are using a text editor.</li></ul>


<h3>Important Symbols and Commands</h3>
Below are a few of the basic symbols that are seen in the R environment and used frequently.

<h4>Table 1 - Important R Symbols</h4>

| Symbol        | Meaning / Use  |
|:-------------:|:--------------:|
| >      | Prompt for a new command line, you do NOT type this, it appears in the console  |
| +      | Continuation of a previously started command, you do NOT type this      |
| # | Comment in code; R does not "see" this text -- important to explain your computational train of thought          |
| <- or = (= not prefered) |    set a value to a name     |


If you are starting a new command line you should see the prompt >. If you are in the middle of an operation/command you will see a +. If you are stuck with a + and are not sure why, check to make sure your parenthesis or brackets are closed.
To get out of an unclosed operation hit the Escape key.

You can scroll through old commands in the console using the up and down arrow keys, just like you can do at the command line at the shell. This allows you to re-run or modify code without re-typing it all out.

<h3>Getting Help</h3>
There are a few ways to get help in R, if you know the exact name of a function using ? is useful, for example:

<pre><code>> ?(log)</code></pre>

Often we don’t know the name of the function, in this case use help.search("search phrase"). This function pulls up a new screen with a list of R help pages containing the phrase you are searching for. For example:

<pre><code>> help.search("linear model")</code></pre>

Sometimes the language in the R help files can be confusing, especially if you are new to the program. If you cannot find what you are looking for in the help files or are confused by them try ’googling’ your problem or question. There are many R forums online and they can be quite helpful.

<h3>Brackets</h3>

There are three types of brackets used in R. Below is a quick reference table on when to used each type.

<h4>Table 2: Bracket Types Usage</h4>

| Bracket Type|Bracket|Bracket Usage|
|:-------------:|:--------------:|:--------------:|
| Round|( )| Use these brackets when calling a function |
| Squared  | [ ] | Use these brackets when calling a subset of an object|
| Curved | { } | Use these brackets when defining operations when writing 'for' loops and functions|

<h3>Objects</h3>

R recognizes and saves things that are input into it as ’objects’. There are a few types of objects that R recognizes and they each have slightly different properties.

Types of objects include:
<ul><li>Variable: a single value or character.</li>
<li>Vector: a list of values of characters.</li>
<li>Dataframe: a matrix of values that makes it easy to call columns by name.</li>
<li>Function: a protocol in R for performing an operation.</ul>


A couple of other R objects that we are not going to cover here but are still important are:
<ul><li>Matrix: a matrix of values</li>
<li>List: the most flexible object, can hold multiple other objects of different types</li></ul>

<h3>Variables and Simple Assignments</h3>

To assign a name to a value use &lt;- (or =, but this is not preferred due to R scripting syntax)

R will of course do math operations (such as +, -, /, *), you can save the output as a variable, for example:

<pre><code>> b = 7 * 24
>b
[1] 168</code></pre>

Once a variable is assigned you can call them when doing operations, for example:

<pre><code>> ab = b/a
> ab
[1] 33.6</code></pre>

<h3>Built-in R functions</h3>

R has many functions that come with the program. To use a function we call the function name and then use ROUND brackets. For example if we want to see the list of ’objects’ that we have created we use the ls( ) function:

<pre><code>> ls( )
[1] "a"  "ab" "b"</code></pre>

Many functions take arguments, or information on the operation of interest. For example if we want to take the natural log of ’a’ we use the function log( ):

<pre><code>> log(a)
[1] 1.609438</code></pre>

If we want to find the possible arguments that a function takes we can use the args( ) function:

<pre><code>> args(log)
function (x, base = exp(1))
NULL</code></pre>

We can also look at the function definition by calling the function name without brackets:

<pre><code>> log
function (x, base = exp(1))  .Primitive("log")</code></pre>

<h3>Vectors and Sequences</h3>

A vector in R is a object that contains a list of several numbers in order. There are several ways of creating a vector.

If we want a sequence of increasing or decreasing whole numbers, with a step size of one we can use the ’:’ operator.

<pre><code>> 2:15
[1] 2 3 4 5 6 7 8 9 10 11 12 13 14 15</code></pre>

We can assign names to vectors as we did with variables, for example:

<pre><code>> d = 1:10
>d
[1] 1 2 3 4 5 6 7 8 9 10</code></pre>

Often we would like a sequence of numbers in which the step size is smaller or larger than one, in these cases we can use the seq() function. For this function we need to set the value it starts at (from), the value it ends at (to), and the length we want the vector to be, such that seq(from, to, length=length of vector). For example:

<pre><code>> f = seq(9, 3, length = 10)
>f
[1] 9.000000 8.333333 7.666667 7.000000 6.333333 5.666667 5.000000 4.333333
[9] 3.666667 3.000000 </code></pre>

<pre><code>> g = seq(5, 16, by = 0.5)
>g
[1]  5.0  5.5  6.0  6.5  7.0  7.5  8.0  8.5  9.0  9.5 10.0 10.5 11.0 11.5
[15] 12.0 12.5 13.0 13.5 14.0 14.5 15.0 15.5 16.0 </code></pre>

Another very useful function to create vectors is the c( ) function. This function will stick things together in whatever order you give it. For example:

<pre><code>> h = c(6, 3, 9, 2, 27, 1)
>h
[1] 6 3 9 2 27 1</code></pre>

<pre><code>> 6,3,9    # won't work! R doesn't recognize "raw" lists</code></pre>

It will also recognize previously assigned variables and vectors:

<pre><code>> k = c(b, a, f)
>k
[1] 168.000000   5.000000   9.000000   8.333333   7.666667
[7]   6.333333   5.666667   5.000000   4.333333   3.666667</code></pre>

And it will do calculations on the fly:

<pre><code>> n = c(2 + 4, 7 * 8, a + b, seq(1:3, by = 2), 5:3)
>n
7.000000
3.000000

[1] 6 56 173 1 2 3 5 4 3</code></pre>

Finally, when you want to create a vector with repeated values we use the rep( ) function. This
function takes a value and repeats it for a specified number of times. For example:

<pre><code>> rep(2, length = 5)
[1] 2 2 2 2 2</code></pre>

<pre><code>> rep(c(1, 2, 3), times = 3)
[1] 1 2 3 1 2 3 1 2 3</code></pre>

<pre><code>> rep(c(1, 2), each = 4)
[1] 1 1 1 1 2 2 2 2</code></pre>

<h3>Subscripting: taking pieces of vectors</h3>

You can take pieces of a vector by using SQUARE brackets:
<pre><code>> d[3]  #the third element of d
[1] 3</code></pre>

<pre><code>> f[3:6]  # elements 3, 4, 5 and 6 of f
[1] 7.666667 7.000000 6.333333 5.666667</code></pre>

<pre><code>> g>10  # logical vector
[1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
[13] TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE</code></pre>

<pre><code>> g[g>10]  # just the elements in g that are greater than 10
[1] 10.5 11.0 11.5 12.0 12.5 13.0 13.5 14.0 14.5 15.0 15.5 16.0</code></pre>

We can assign a new value, such as 1 to a subset of a vector:

<pre><code>> d[d < 5] = 1</code></pre>

<pre><code>>d
[1] 1 1 1 1 5 6 7 8 9 10</code></pre>

<h3>Working with vectors</h3>

Once we have created a vector we can do arithmetic on it element-by-element, for example:

<pre><code>> a = 1:10 > b = 3:12
> a+2
[1] 3 4 5 6 7 8 9 10 11 12</code></pre>

<pre><code>> a+b
[1] 4 6 8 10 12 14 16 18 20 22</code></pre>

Most of the math operation functions (i.e., exp, log, etc) are written such that they work element-by-element as well:
<pre><code>> exp(a)  # exponential of a
[1]     2.718282     7.389056    20.085537    54.598150   148.413159
[6]   403.428793  1096.633158  2980.957987  8103.083928 22026.465795</code></pre>

<pre><code>> log10(b)  # log base 10 of b
[1] 0.4771213 0.6020600 0.6989700 0.7781513 0.8450980 0.9030900 0.9542425
[8] 1.0000000 1.0413927 1.0791812</code></pre>

<pre><code>> log(a,base=2)  # log with base 2, you can do logarithms with any base
[1] 0.000000 1.000000 1.584963 2.000000 2.321928 2.584963 2.807355 3.000000
[9] 3.169925 3.321928</code></pre>

The latter example is a demonstration of how functions have default values. For the function log the default is a natural log, however we can ask it to calculate log with any base by defining the base when we call the log( ) function. To check on the default values of functions in R you can use help - ?() - which is similar to the "man" command when you are at the command line.