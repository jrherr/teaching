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

<h3>Reading in Data</h3>

There are several functions for reading data sets into R. We are going to focus on the read.csv function, but there are many other methods and functions for reading in data.

Often data is saved in excel workbooks (or in a SQL database), when this is the case one of the easy ways to convert them into a file type that R can understand is to save them as comma delimited files or .csv files (filename.csv). In excel this is done through ”Save As...” then choosing the csv option under file type.

Once the data file is saved in the proper format we need to check where it has been saved. This is very important because we need to tell R where to look for the file. There are a few ways to make sure R is ’looking’ in the correct location. One way is to set the R ”working directory” to be the same location as the file of interest.

To change or view the working directory on a Mac:
Go to ”Misc” drop down menu in R and select ”Change Working Directory...” to change the directory or ”Get Working Directory” to find out what the directory is set as.

To change or view the working directory on a PC:
Go to the ”File” drop down menu in R and select ”Change dir...”

To change the working directory in RStudio (both Macs and PCs): Go to the ”Tools” drop down menu and select ”Set Working Directory”

Another way to make sure that R finds the file is to give R the entire file path name when we load the file into R, just like we would do when working at the command line.

Example: We can load the expData.csv file into R using the read.csv( ) function as follows:
<pre><code>> dat=read.csv("expData.csv") # use when the working directory is the same as the location of the file</code></pre>
<pre><code>> dat
    times expVal
1   1      2.718282
2   2      7.389056
3   3     20.085537
4   4     54.598150
5   5    148.413159
6   6    403.428793
7   7   1096.633158
8   8  	2980.957987
9   9  	8103.083928
10  10 22026.465790
</code></pre>

To read the file in with the path name we use the same function, just include the path, for example:
<pre><code>> dat=read.csv("/YOUR-PATH-HERE/expData.csv")</code></pre>

Data that is read into R, comes in as ’dataframe’ object. This means the data is in a matrix format, with rows and columns and it can have column names associated with it.

<h3>Subsetting: taking part of a dataframe</h3>

As with vectors when we want to call only part of a dataframe we can do it by using SQUARE brackets. However, unlike vectors, each element in a dataframe has two position indicators, one for the row and one for the column. When we call a piece of a dataframe we have to include both positions. The way the position works is: dataframe[row, column]. (This is also true of matrix objects.) For example if we want the value of the number in the 3rd row 2nd column we would use the following code:

<pre><code>> dat[3, 2]
[1] 20.08554</code></pre>

We can also call sequences of rows or columns.

<pre><code>> dat[1:3 ,2] #Calls rows 1, 2 and 3, second column
[1]  2.718282  7.389056 20.085537</code></pre>

<pre><code>> dat[6, ] #calls row 6, all columns
     time   expVal
6    6 403.4288</code></pre>

<pre><code>> dat[ ,1] #calls column1, all rows (the "," separates the row indicator from the column one)
[1] 1 2 3 4 5 6 7 8 9 10 </code></pre>

Because dataframes have column names we can also subset the dataset using those. We do this using the $ operator, for example:

<pre><code>> dat$time # this is the same as calling dat[ ,1]
[1] 1 2 3 4 5 6 7 8 9 10</code></pre>

<pre><code>> dat$expVal[4:8] # calls the second column, rows 4 through 8, same as dat[4:8,2]
[1]   54.59815  148.41316  403.42879 1096.63316 2980.95799</code></pre>

<h3>Loading Packages</h3>

The basic R program that you download to your computer has many built-in capabilities, how- ever, there are a large number of very diverse additional packages that can be added to the basic program to perform more specialized tasks.

<h4>In Rstudio</h4>
To download a package, go to the Tools menu, and select Install Packages. Type the name of the package, "plyr" into the Packages box and click install. This will download this package onto your computer.

<h4>Macs</h4>
To download a package, first go to the Packages &amp; data menu and select Package Installer. A window will open up with a drop down menu that should say CRAN (binaries). Click the Get List button. This will cause another window to open up called CRAN mirror, select one near to where you are (the Ohio (OH) mirror is stable so I would suggest choosing it). A list of packages will be pulled up. Search for a package called psych. Select it and click Install Selected. This will download the package onto your computer.

<h4>PCs</h4>
To download a package, go to the Packages menu and click on Install Packages. It asks for you to select a CRAN mirror (the Ohio (OH) mirror is stable so I would suggest choosing it). That will pull up a list of all available packages, scroll down the list until you see the package psych. Select it, and click ok. This will download the package onto your computer.

For all operating systems, we load a package it onto our workspace using the library() function.

<pre><code>> library(plyr)</code></pre>

<h3>Functions</h3>
Writing functions in R is very useful when the task you wish to accomplish is not written in the built-in R functions (this happens more often then you think). As with loops, functions can be a bit confusing at first so be patient and don’t get discouraged.

The first step in writing a function is to define the function and what it will do. This is accomplished by using the 'function( )' function. Inside the ROUND brackets we define the arguments our function will take. Inside the CURLY brackets we define the operation the function will be performing, and what we want the function to tell us, such that:

<pre><code>name=function(x, y){ #this function would have 2 arguments
z=operation #here we are telling the function what to do
return(z) #return tells R what to give us back once it has run the function
}</code></pre>

NOTE: When R is running an operation inside a function, it CANNOT "see" objects that you have defined outside the function. Similarly, when you are outside a function, R cannot "see" objects created inside a function UNLESS you tell it to return them at the end of the function.

Once the function is written, we can have it perform the operations by calling it as we do with built-in R functions (for example: 'function()'). NOTE: writing the function does NOT run the operation. We MUST call it in order for the operation to be executed. This is why it is important to always name your function, without a name you will not be able to refer to the function in your analysis.

<h3>Examples Of Functions</h3>

If we want to create a function that squares things for us we do the following:

<pre><code>> square=function(x){ #name our function and define one argument
+         res=xˆ2 #operation the function will perform when called
+         return(res) #the information we want back
+ } #end of function</code></pre>

Now that our ”square” function is created we can call it as follows:

<pre><code>> square(5) #call the square function and give it the argument of 5,
[1] 25</code></pre>

What if we want to create a function that squares things as a default but can take things to other powers as well? We can do this with just a few modifications on our square function. We will call our new function power.

<pre><code>> power=function(x,y=2){ #name our function and define two arguments,
+ #y has the default value of 2
+         res2=xˆy #operation the function will perform when called
+         return(res2) #the information we want back
+ } #end of function</code></pre>

Because we have defined y to have the default value of 2, the power function will square our x argument unless otherwise specified, for example:

<pre><code>> power(5) #does the same thing as our square function
 [1] 25
 > power(5,3) #cubes 5
 [1] 125
 > power(y=0.5, x=25) #takes the square root of 25
 [1] 5</code></pre>

Notice in the above example, when we don’t specify the order of the arguments, R will automatically go in order (i.e., x first, y second). However, we can go out of order if we define the arguments in the function (i.e. x= and y=).

<h3>Loops</h3>

Loops are very handy when you want to run an operation multiple times, for example we might want to calculate how something changes over time or reiterate a code over many strings (such as DNA sequences). We will accomplish this with a ’for’ loop. Understanding the logic behind loops is difficult and it usually takes many attempts to get the hang of it so don’t get discouraged.

Before actually writing the loop part of our 'for loop', we need to create a place to store the results in, a vector for example. Then to write the for loop we must call the for() function. We will be running an operation over many time steps, so we need a ’counter’ or index for the current location, here we will use i, we also need to tell R where it is starting the index and were it is ending. All of this information goes within the ROUND brackets. With for loops we also use CURLY brackets after the round brackets to define the operation the loop will execute.

<pre><code>for(i in starting:ending){
 result.vector[i]=operation
 } #end of for loop</code></pre>

For example, if we want to take 4 to increasingly higher powers we would write a loop as follows:

<pre><code>> IT=5 #number of times we want our loop to do the operation
 > p=seq(3,7,by=1) #a vector of powers we are going to take 4 too.
 > result=rep(NA, length=IT) #create an empty vector to store the results in
 > for(i in 1:5){ #tell our loop that it is going to start with i=1 and count up
 + #(by whole numbers) until i=5
 + result[i]=4ˆp[i] #stores the result of the calculation in the i'th place in
 + # our result
 + #vector, e.g. result[1]=4ˆp[1] or 4ˆ3
 + } #end of for loop
 > result

[1]    64   256  1024  4096 16384
</code></pre>

In the previous example, the loop sets i to be equal to 1 then 2 etc until i is equal to 5. So when i = 3 the loop replaces the ’NA’ in the 3rd position of the result vector.

<h3>Basic Plotting</h3>

Creating nice plots in R is fairly straightforward. The plot(x,y) function by default plots a scatterplot of points, but it is quite flexible and easy to manipulate. NOTE: your x and y vectors MUST be the same length. For example:
<pre><code>> a = 1:10
 > b = seq(1, 100, length = 10)
 > plot(a, b)</code></pre>

There are lots of pretty incredible graphing packages for R: in my opinion <a href="http://ggplot2.org/">ggplot2</a> and <a href="http://cran.r-project.org/web/packages/lattice/index.html">lattice</a> are two of the best.  There's also a lot of applications which will help you present your R figures online (such as<a href="http://www.rstudio.com/shiny/"> shiny</a>) or render documentation (such as <a href="http://yihui.name/knitr/">knitr</a>).

                     QUICK AND DIRTY GUIDE TO R
           (just about enough to cover a first stats course).
                        by William B. King, Ph.D.
                       Coastal Carolina University
-------------------------------------------------------------------------------
Best used with R in front of you and running -- for simplicity I have done away
with certain annoying statistical formalisms.
-------------------------------------------------------------------------------
Getting it.

Download R from www.r-project.org (click on the CRAN link on the left side of
the page under downloads). As of this moment, the current version is 2.7.1. It
is available for Windows, OS X, and Linux.

-------------------------------------------------------------------------------
The R prompt.

R is command-line driven. The prompt looks like a greater than sign, >. When
you see it, start typing. (Much faster than hunting and clicking once you get
used to it!)

-------------------------------------------------------------------------------
Quitting R.

> quit()                          # the parentheses are mandatory!

Note: best to know this right away! Also, q() works. When it asks to save your
workspace, pick no until you know what this means.

-------------------------------------------------------------------------------
Interactive mode.

R can be used by writing programs into scripts and reading them in. It's easier
to use R in interactive mood, typing individual commands at the command prompt.
Notes or comments can be added to the R session by typing a hash or pound
symbol, #. Anything on the line following this symbol will be ignored by R.

-------------------------------------------------------------------------------
Simple data input.

Small data sets can be entered using the c() function. This produces a data
vector. Name it anything you want, but don't put spaces or dashes in the name.
Use underline characters or periods instead.

> my.data = c(22, 38, 12, 23, 29, 18, 16, 24)

Note: spaces after the commas are optional.

> my.data=c(22,38,12,23,29,18,16,24)

To examine what you've entered, just type its name.

> my.data
[1] 22 38 12 23 29 18 16 24

To change value i in the list, address it as my.data[i]. For example...

> my.data[2] = 28
> my.data
[1] 22 28 12 23 29 18 16 24

-------------------------------------------------------------------------------
Simple frequency distributions.

To put a simple frequency distribution into a vector, do this.

      X     f
    -----------
      7     3
      6     0
      5     2
      4     7
      3     5
      2     1
      1     1

> X = 7:1                         # same thing as X = c(7, 6, 5, 4, 3, 2, 1)
> f = c(3, 0, 2, 7, 5, 1, 1)
> the.data = rep(X, f)            # rep() is the repeat function
> the.data
[1] 7 7 7 5 5 4 4 4 4 4 4 4 3 3 3 3 3 2 1

-------------------------------------------------------------------------------
A simple (and grouped) frequency table (kinda).

> table(the.data)                 # use your variable name inside the ( )
the.data
1 2 3 4 5 7                       # the X "column"
1 1 5 7 2 3                       # the f "column"

Note: there are no 6's, so R doesn't report them.

> table(my.data)                  # not much to see here
my.data
12 16 18 22 23 24 28 29 
 1  1  1  1  1  1  1  1

**grouping (a bit tricky)**

> bins = seq(10, 30, 5)           # same thing as bins = c(10, 15, 20, 25, 30)
> table(cut(my.data, bins))
(10,15] (15,20] (20,25] (25,30]   # closed on the right by default
      1       2       3       2

Or, since doing more than one thing at a time makes most students nervous...

> bins = c(10, 15, 20, 25, 30)
> temp.table = cut(my.data, bins, right=FALSE)
> table(temp.table)

Note: the right=FALSE (or right=F) option closes the bins on the left.

> stem(my.data)                   # stem-and-leaf display is better anyway!

  The decimal point is 1 digit(s) to the right of the |

  1 | 2
  1 | 68
  2 | 234
  2 | 89

-------------------------------------------------------------------------------
Histogram.

> hist(the.data)

Note: bars in R histograms include the right limit but not the left.

> hist(the.data, right=F)         # now includes the left, not the right

This makes it much clearer...

> bins = seq(.5, 7.5, 1)          # creates a sequence from .5 to 7.5 by 1
> hist(the.data, bins)

-------------------------------------------------------------------------------
Categorical (nominal) data.

> colors = c("red", "black", "brown", "blonde")
> freqs  = c(  8  ,    22  ,    30  ,    18   )       # spaces don't matter
> hair.color = rep(colors, freqs)
> table(hair.color)
hair.color
 black blonde  brown    red 
    22     18     30      8 
> barplot(table(hair.color))
> barplot(table(hair.color), col=c("black","yellow","brown","red"))

Note: the order of the bars can be changed, too.

-------------------------------------------------------------------------------
Summation.

> sum(the.data)                   # sigma X
[1] 77

> sum(the.data)^2                 # (sigma X) quantity squared
[1] 5929

>sum(the.data^2)                  # sigma (X squared)
[1] 359

Note: the squared values themselves can be returned with...

> the.data^2
[1] 49 49 49 25 25 16 16 16 16 16 16 16  9  9  9  9  9  4  1

> x = c(2, 3, 5)
> y = c(3, 8, 9)
>sum(x * y)                       # sum of the crossproducts
[1] 75

-------------------------------------------------------------------------------
Descriptive statistics.

**sample size**

> length(the.data)
[1] 19
> length(hair.color)
[1] 78

**sample median**

> median(the.data)
[1] 4

**sample mean**

> mean(the.data)
[1] 4.052632

**range**

> range(the.data)                 # reports the min and max values
[1] 1  7

**IQR**

> IQR(the.data)
[1] 1.5

Note: this may not be the "textbook" IQR. R can use 9 different methods to
calculate Q1 and Q3. By default it uses a different one than most elementary
textbooks. See below for a fix.

**sample variance**

> var(the.data)
[1] 2.608187

**sum of squares**

> var(the.data) * (length(the.data) - 1)
[1] 46.94737

Note: there is no built-in function, but it is easy enough to create one.

**sample standard deviation**

> sd(the.data)
[1] 1.614988

**more or less all at once**

> summary(the.data)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  1.000   3.000   4.000   4.053   4.500   7.000

Note: these quartiles are technically correct for continuous data. The
"textbook" method would give Q3 = 5, which is correct for discrete data. To 
get this...

> quantile(the.data, c(.25,.75), type=2)
25% 75% 
  3   5 

-------------------------------------------------------------------------------
Unit normal distribution.

Note: R has a built-in function for converting to z-scores, but it is too
confusing for most students, I'd bet. Instead, they can use R as a calculator.

If mu = 25 and sigma = 8, convert these scores to z-scores: 18, 28, 38, 21.

**one at a time**

> (18 - 25)/8
[1] -0.875

**or all at once**

> scores = c(18, 28, 38, 21)
> z = (scores - 25)/8             # assignment to variable z is optional
> z
[1] -0.875  0.375  1.625 -0.500

**probabilities under the normal curve**

> pnorm(0.375)                    # area at or below z
[1] 0.6461698

> 1 - pnorm(0.375)                # area above z
[1] 0.3538302

> pnorm(z)                        # for all of the values stored in z at once
[1] 0.1907870 0.6461698 0.9479187 0.3085375

**the inverse z function**

> qnorm(.9)                       # the z with 90% of area at or below it
[1] 1.281552

-------------------------------------------------------------------------------
Single sample z-test.

Ain't built in -- must be calculated by hand.

-------------------------------------------------------------------------------
Single sample t-test.

> the.data                                  # just to be sure it's still there
[1] 7 7 7 5 5 4 4 4 4 4 4 4 3 3 3 3 3 2 1

> t.test(the.data, mu=5)

        One Sample t-test

data:  the.data 
t = -2.557, df = 18, p-value = 0.01981
alternative hypothesis: true mean is not equal to 5 
95 percent confidence interval:
 3.274232 4.831031 
sample estimates:
mean of x 
 4.052632 

> t.test(the.data, mu=5, alternative="greater")

        One Sample t-test

data:  the.data 
t = -2.557, df = 18, p-value = 0.99
alternative hypothesis: true mean is greater than 5 
95 percent confidence interval:
 3.410155      Inf 
sample estimates:
mean of x 
 4.052632

> t.test(the.data, mu=5, alternative="less")

        One Sample t-test

data:  the.data 
t = -2.557, df = 18, p-value = 0.009904
alternative hypothesis: true mean is less than 5 
95 percent confidence interval:
     -Inf 4.695109 
sample estimates:
mean of x 
 4.052632 

-------------------------------------------------------------------------------
Independent t-test.

> x1 = c(18, 25, 17, 20, 23)
> x2 = c(20, 30, 22, 25, 28, 30)

**pooled variance**

> t.test(x1, x2, var.equal=T)

        Two Sample t-test

data:  x1 and x2 
t = -2.2395, df = 9, p-value = 0.05188
alternative hypothesis: true difference in means is not equal to 0 
95 percent confidence interval:
 -10.51953398   0.05286732 
sample estimates:
mean of x mean of y 
 20.60000  25.83333 

**unpooled variance (the default)**

>  t.test(x1, x2)

        Welch Two Sample t-test

data:  x1 and x2 
t = -2.2903, df = 8.995, p-value = 0.04776
alternative hypothesis: true difference in means is not equal to 0 
95 percent confidence interval:
 -10.40273450  -0.06393217 
sample estimates:
mean of x mean of y 
 20.60000  25.83333 

**one-tailed (R always subtracts group 1 - group 2)**

> t.test(x1, x2, var.equal=T, alternative="less")

        Two Sample t-test

data:  x1 and x2 
t = -2.2395, df = 9, p-value = 0.02594
alternative hypothesis: true difference in means is less than 0 
95 percent confidence interval:
       -Inf -0.9497217 
sample estimates:
mean of x mean of y 
 20.60000  25.83333 

**the formula interface (a more sophisticated way)**

> all.scores = c(x1, x2)               # combines x1 and x2 into one vector
> all.scores
 [1] 18 25 17 20 23 20 30 22 25 28 30
> grp = c("x1", "x2")                  # the group names
> n = c(5, 6)                          # the groups sizes
> groups = rep(grp, n)                 # create the labels
> groups
 [1] "x1" "x1" "x1" "x1" "x1" "x2" "x2" "x2" "x2" "x2" "x2"
> t.test(all.scores ~ groups)          # "all.scores by groups"

        Welch Two Sample t-test

data:  all.scores by groups 
t = -2.2903, df = 8.995, p-value = 0.04776
alternative hypothesis: true difference in means is not equal to 0 
95 percent confidence interval:
 -10.40273450  -0.06393217 
sample estimates:
mean in group x1 mean in group x2 
        20.60000         25.83333 

**a test for homogeneity of variance (better than Hartley F-max)**

> bartlett.test(list(x1,x2))

        Bartlett test of homogeneity of variances

data:  list(x1, x2) 
Bartlett's K-squared = 0.1994, df = 1, p-value = 0.6552

> bartlett.test(all.scores ~ groups)   # also works with formula interface

        Bartlett test of homogeneity of variances

data:  all.scores by groups 
Bartlett's K-squared = 0.1994, df = 1, p-value = 0.6552

Also...

> var.test(x1, x2)                     # significance test for two variances

        F test to compare two variances

data:  x1 and x2 
F = 0.636, num df = 4, denom df = 5, p-value = 0.6818
alternative hypothesis: true ratio of variances is not equal to 1 
95 percent confidence interval:
 0.08608992 5.95601427 
sample estimates:
ratio of variances 
         0.6360225 

> var.test(all.scores ~ groups)        # the formula interface also works

-------------------------------------------------------------------------------
Dependent (related samples) t-test.

> before = c(18, 17, 20, 19, 22, 24)
> after = c(20, 22, 19, 21, 25, 25)
> t.test(before, after, paired=T)

        Paired t-test

data:  before and after 
t = -2.4495, df = 5, p-value = 0.05797
alternative hypothesis: true difference in means is not equal to 0 
95 percent confidence interval:
 -4.09887128  0.09887128 
sample estimates:
mean of the differences 
                     -2 

Note: R always subtracts first group - second group. One-tailed tests can be
specified as in the independent t-test with the option alternative=.

-------------------------------------------------------------------------------
ANOVA (oneway, between subjects)

> x1                                   # still there (if not, re-enter it)
[1] 18 25 17 20 23
> x2                                   # still there
[1] 20 30 22 25 28 30
> x3 = c(35, 27, 27, 30, 40, 33)       # a new level of X
> all.scores = c(x1, x2, x3)           # combined into a single data vector
> grp = c("x1", "x2", "x3")            # the group names
> n = c(5, 6, 6)                       # the group sizes
> groups = rep(grp, n)                 # labels for each score
> results = aov(all.scores ~ factor(groups))
> summary(results)
            Df Sum Sq Mean Sq F value   Pr(>F)   
groups       2 358.20  179.10  9.5691 0.002402 **
Residuals   14 262.03   18.72                    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Notes: the formula interface is mandatory for the aov() function. To get the
ANOVA table, store the output of the aov() function and then use the summary()
function to see the table. The function oneway.test() also does a oneway ANOVA,
but the full ANOVA table is not produced. R can get very snotty if you don't
correctly label the factor. If it is coded numerically, this is required!

> TukeyHSD(results)                    # only post hoc test available
  Tukey multiple comparisons of means
    95% family-wise confidence level

Fit: aov(formula = all.scores ~ factor(groups))

$`factor(groups)`
           diff        lwr      upr     p adj
x2-x1  5.233333 -1.6231312 12.08980 0.1493412
x3-x1 11.400000  4.5435354 18.25646 0.0017968
x3-x2  6.166667 -0.3707158 12.70405 0.0656473

Advantage of the aov() function--a post hoc (Tukey) test can be done.
Advantage of the oneway.test() function--it can correct for nonhomogeneity.

> oneway.test(all.scores ~ groups)

        One-way analysis of means (not assuming equal variances)

data:  all.scores and groups 
F = 9.4638, num df = 2.000, denom df = 9.299, p-value = 0.005727

-------------------------------------------------------------------------------
Correlation.

> x = rnorm(100, 50, 10)          # 100 normally distributed random numbers
> y = rnorm(100, 75, 20)          # 100 more
> plot(x, y)                      # scatterplot
> cor(x, y)
[1] 0.00620442                    # Pearson's r is the default
> cor(x, y, method="spearman")    # Spearman rho (don't capitalize it!)
[1] -0.002076208
> cor.test(x, y)                  # correlation t-test

        Pearson's product-moment correlation

data:  x and y 
t = 0.0614, df = 98, p-value = 0.9511
alternative hypothesis: true correlation is not equal to 0 
95 percent confidence interval:
 -0.1904458  0.2023759 
sample estimates:
       cor 
0.00620442

Note: one-tailed tests are also possible by using the alternative= option.

-------------------------------------------------------------------------------
Regression.

> lm(y ~ x)                       # linear regression requires formula interface

Call:
lm(formula = y ~ x)

Coefficients:
(Intercept)            x  
   74.43864      0.01112 

> my.lm.analysis = lm(y ~ x)      # storing the results gives more output
> summary(my.lm.analysis)

Call:
lm(formula = y ~ x)

Residuals:
    Min      1Q  Median      3Q     Max 
-38.663 -14.562  -0.173  13.702  50.507 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 74.43864    9.07285   8.205 9.27e-13 ***
x            0.01112    0.18097   0.061    0.951    
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1 

Residual standard error: 17.45 on 98 degrees of freedom
Multiple R-Squared: 3.849e-05,  Adjusted R-squared: -0.01017 
F-statistic: 0.003773 on 1 and 98 DF,  p-value: 0.9511 

-------------------------------------------------------------------------------
Chi-square goodness of fit.

> hair.color                           # still there (if not, re-enter it)
 [1] "red"    "red"    "red"    "red"    "red"    "red"    "red"    "red"   
 [9] "black"  "black"  "black"  "black"  "black"  "black"  "black"  "black" 
[17] "black"  "black"  "black"  "black"  "black"  "black"  "black"  "black" 
[25] "black"  "black"  "black"  "black"  "black"  "black"  "brown"  "brown" 
[33] "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown" 
[41] "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown" 
[49] "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown"  "brown" 
[57] "brown"  "brown"  "brown"  "brown"  "blonde" "blonde" "blonde" "blonde"
[65] "blonde" "blonde" "blonde" "blonde" "blonde" "blonde" "blonde" "blonde"
[73] "blonde" "blonde" "blonde" "blonde" "blonde" "blonde"

> chisq.test(table(hair.color))

        Chi-squared test for given probabilities

data:  table(hair.color) 
X-squared = 12.8718, df = 3, p-value = 0.004922

> chisq.test(c(22,18,30,8))            # also works from raw frequencies

        Chi-squared test for given probabilities

data:  c(22, 18, 30, 8) 
X-squared = 12.8718, df = 3, p-value = 0.004922

Note: the default is equal expected frequencies. If expected frequencies are
unequal, enter them as proportions or probabilities.

> expected = c(1/4, 1/4, 1/3, 1/6)
> sum(expected)                        # must sum to 1, of course
[1] 1
> observed = c(22, 18, 30, 8)          # observed must be frequency counts
> chisq.test(observed, p=expected)

        Chi-squared test for given probabilities

data:  observed 
X-squared = 2.9744, df = 3, p-value = 0.3956

-------------------------------------------------------------------------------
Chi-square test of independence.

If the data have already been crosstabulated, this is easy. Otherwise, you'll
need to learn to use the xtabs() and table() functions for crosstabulation.

                             variable one
                       dems     repubs    other
               male     22        35       12
variable two
               female   28        30       18

> row1 = c(22, 35, 12)
> rwo2 = c(28, 30, 18)            # so I can't spell, so sue me!
> crosstabs = rbind(row1, rwo2)
> crosstabs
     [,1] [,2] [,3]
row1   22   35   12
rwo2   28   30   18
> chisq.test(crosstabs)

        Pearson's Chi-squared test

data:  crosstabs 
X-squared = 1.9713, df = 2, p-value = 0.3732

Note: for 2x2 tables, R does the Yates correction by default. To prevent this:

> chisq.test(crosstabs, correct=F)

-------------------------------------------------------------------------------
Getting help.

> help(function.name)             # opens a somewhat helpful help page
> help(t.test)                    # ?t.test is a shortcut

> help.search("distribution")     # looks for anything to do with quoted terms

Note: the R manuals are included with the download in both PDF and html format.
Look for them in the root R directory.

-------------------------------------------------------------------------------
Reading in a dataframe from a csv file.

The best way I've found to handle large data files is to enter them into a
spreadsheet and then save them in comma separated format. The file should have
column names, one column per variable, and one row per case, and NOTHING else.
If you drop a copy of it into your working directory, you can read it into a
dataframe as follows:

> dataframe.name = read.csv("filename.csv")

It's best to keep the names of dataframes in memory SHORT, so maybe...

> df = read.csv("filename.csv")

Then the following functions are available:

> names(df)                       # get the names of the variables
> dim(df)                         # get the size of the dataframe
> summary(df)                     # summarize all the variables
> mean(df)                        # find the mean of all the numerical variables
> str(df)                         # gives a lot of info about the dataframe

The easiest way to work with the variables in the dataframe is to use the $
notation:

> mean(df$scores)                 # find the mean of the variable named scores

Statistical tests can be done by specifying the name of the dataframe in a
data option, but only if the formula interface is used:

> t.test(scores ~ groups, data=df)

-------------------------------------------------------------------------------
Housekeeping.

> ls()                            # shows the names of objects you've created
> remove(object.name)             # deletes the named object; rm() also works

Note: it's best to keep your workspace cleaned up by deleting unused objects.

> dir()                           # get a dir listing of the working directory
> getwd()                         # get the name of the working directory
> setwd()                         # set (change) the working directory

Note: in Windows it's best to use the pulldown menus to change directories
rather than attempt to navigate through the file system. It's best not to
clutter up the root R directory with a lot of saved work files. Make a new
directory in My Documents (in Windows) and switch to it when you start R.

> save(the.data, file="thedata.sav")

Note: this is the easiest way to save data, as a data vector in a proprietary
file format. The file will be saved in the working directory. To read it back
in at some later work session:

> load(file="thedata.sav")

Entire dataframes can be stored this way as well:

> save(df, file="df.sav")
> rm(df)
> load(file="df.sav")

There are many other commands for saving and loading data files, too numerous
to mention here.

-------------------------------------------------------------------------------

