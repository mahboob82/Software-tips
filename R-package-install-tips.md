# Step 1
1. Direct install: First try installing directly by this
    
    ``install.packages('furrr', repos='https://cran.yu.ac.kr/', dependencies=TRUE)``

2. Local install: Go to CRAN website.  

[https://cran.r-project.org/](https://cran.r-project.org/)

or [https://cran.yu.ac.kr/](https://cran.yu.ac.kr/)

Go to : Softwares > Packages > list

3. If failed, download a package of interest manually and save it into any folder and issue the command below:
  ``install.packages('C:/Users/User/Downloads/abc_2.1.zip', repos=NULL, type='source')``


Unable to open Repo:

or 

Software not available for this R version:


apt install gfortran
apt install cmake
aptt install make
apt install libxml2_dev
apt install libssl_dev

install.packages("relaimpo", dependencies=TRUE, repos="http://CRAN.R-project.org")

install.packages("tidyverse", dependencies=TRUE, repos="http://CRAN.R-project.org")

install.packages("curl", dependencies=TRUE, repos="http://CRAN.R-project.org")

install.packages("httr", dependencies=TRUE, repos="http://CRAN.R-project.org")

install.packages("lme4", dependencies=TRUE, repos="http://cran.yu.ac.kr")
install.packages("nlme", dependencies=TRUE, repos="http://CRAN.R-project.org")
