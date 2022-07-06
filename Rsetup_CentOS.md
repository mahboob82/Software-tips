# An R setup Tutorial for unpreviledged Linux users (CentOS-7)


## How to install R packages in my HOME directory (when Base R is installed system-wide):

* Now that I have R core is installed on the system root, you can install your desired packages in your HOME directory, without changing the default environment. 

### Install R packages in User's $HOME/R directory

#### Step 1: 
Suppose the username is "mahboob". So, create a directory named ``R`` under ``/home/mahboob/``:
 
``` bash
 	[mahboob@localhost ~]$ mkdir ~/R
```
 
#### Step 2:
1. Create an ``.Renviron`` file in ``mahboob`` directory

``` bash
[mahboob@localhost ~]$ touch ~/.Renviron
```

2. Open ``.Renviron`` file using 'vi' editor

``` bash
[mahboob@localhost ~]$ vi ~/.Renviron
```
3. Put the following code in the file (don't forget to put your ``username`` here)
```R
.libPaths(new = "/home/mahboob/R/x86_64-pc-linux-gnu-library/4.2/")
```
4. exit out the file by pressing ESC and saving the file by

```
:wq
```


### Step 3: 

1. Create an ``.Rprofile`` file in ``mahboob`` directory

``` bash
[mahboob@localhost ~]$ touch ~/.Rprofile
```

2. Open ``.Renviron`` file using 'vi' editor
``` bash
[mahboob@localhost ~]$ vi ~/.Rprofile
```
3. Put the following code in the file
```
options(repos=structure(c(CRAN="https://cloud.r-project.org")), dependencies=TRUE)
```
4. exit out the file by pressing ESC and saving the file by

```
:wq 
```


Now you are set to install packages in a R session

### A SIMPLE INSTALLATION EXERCISE:

Suppose, you want to install a package named ``fortunes``. Note: it's a fun package.

1. Open an regular `` R `` session in the terminal and try to load the package, just to make sure that the package is not there yet.
``` 
[mahboob@localhost ~]$ R 
....
....

> library(fortunes)
Error in library(fortunes) : there is no package called ‘fortunes’
>
```
2.  Now issue the package install command on R console

```
> install.packages("fortunes")
Installing package into ‘/home/mahboob/R/x86_64-pc-linux-gnu-library/4.2’
(as ‘lib’ is unspecified)
trying URL 'https://cloud.r-project.org/src/contrib/fortunes_1.5-4.tar.gz'
Content type 'application/x-gzip' length 192938 bytes (188 KB)
==================================================
downloaded 188 KB

* installing *source* package ‘fortunes’ ...
** package ‘fortunes’ successfully unpacked and MD5 sums checked
** using staged installation
** R
** inst
** byte-compile and prepare package for lazy loading
** help
*** installing help indices
  converting help for package ‘fortunes’
    finding HTML links ... done
    fortunes                                html
** building package indices
** installing vignettes
** testing if installed package can be loaded from temporary location
** testing if installed package can be loaded from final location
** testing if installed package keeps a record of temporary installation path
* DONE (fortunes)

The downloaded source packages are in
        ‘/tmp/Rtmp4FegVz/downloaded_packages’
>
```

3. Great! Now load and test it.
```
> library("fortunes")
> fortune()

Before we get too carried away with this thread could you all please consider
how the sd function calculates its result? [...] I'll tell you, it takes the
square root of the variance. How is the variance calculated for a numeric
vector? First you calculate the mean *using floating point arithmetic* in which
it is not necessarily true that N * k / N == k [...] Most of those tests [for
numerical accuracy] end in a check using the all.equal function which checks if
the relative difference is less than a threshold. That's about the best that
you can do with floating point arithmetic.
Here endeth the sermon.
   -- Douglas Bates (after a discussion why sd(rep(0.001, 15)) is not
      necessarily exactly 0)
      R-help (March 2004)


>
```

### How do I uninstall this package?
1. It's also very simple. Just try:
```
> remove.packages("fortunes")
Removing package from ‘/home/mahboob/R/x86_64-pc-linux-gnu-library/4.2’
(as ‘lib’ is unspecified)
>

```


### So, where are my packages installed?

* In my case, package will be installed at:
``/home/mahboob/R/x86_64-pc-linux-gnu-library/4.2/`` path.
* Why? Because, I have already mentioned this path in my ``~/.Renviron`` file to do so.
* Now check if the path is loaded or not. Just type ``>.libPaths()`` in your R console.

```
<R-CONSOLE>
# In my case it was:
> .libPaths()
[1] "/home/mahboob/R/x86_64-pc-linux-gnu-library/4.2"
[2] "/opt/R/4.2.0/lib/R/library"
>
```
* Note: I already know that the 2nd path is under root user, I can't install there as a normal user. 
* Also, R will choose the first path in the path-list by default. 



### Troubleshooting

This example is a very simple one. In reality, you could find issues in compiling code or dependencies issue for a larger package. I personally found issues with GCC compiliers or CMAKE related issues. In CentOS 7, it is possible that your compiliers are older version. 

So, in case if you have an issue with older C++11 compiler, or required C++14 flags, please try the following approach:

*  https://github.com/stan-dev/rstan/issues/892

1. Exit out from your R session.
2. Create a new directory ``.R`` and make a ``Makevars`` file inside it.

``` bash
[mahboob@localhost ~]$ mkdir .R
[mahboob@localhost ~]$ touch ~/.R/Makevars
```

3. Copy the following code below in that file and save the file

```
# CONTENT OF Makevars

KEFLAGS = -j8

## C++ flags
CXX=g++
CXX11=g++
CXX14=g++
CXX17=g++

CXXFLAGS=-O3 -march=native -Wno-ignored-attributes
CXX11FLAGS=-O3 -march=native -Wno-ignored-attributes
CXX14FLAGS=-O3 -march=native -Wno-ignored-attributes
CXX17FLAGS=-O3 -march=native -Wno-ignored-attributes

CXXPICFLAGS=-fPIC
CXX11PICFLAGS=-fPIC
CXX14PICFLAGS=-fPIC
CXX17PICFLAGS=-fPIC

CXX11STD=-std=c++11
CXX14STD=-std=c++14
CXX17STD=-std=c++17

## C flags
CC=gcc
CFLAGS=-O3 -march=native

## Fortran flags
FC=gfortran
F77=gfortran
FFLAGS=-O3 -march=native
FCFLAGS=-O3 -march=native

```
4. Now Go back to your R session and rerun the installation.
5. Most probably you're problem will be solved.
6. However, if you find any compiling errors "C99" during other package installations, then quit R session and try renaming the the to something else to keep the file out of R's scope. It is possible that your compiling problem will be solved.





