# Step 1 in R console
Install IRKernel

```R
install.packages('IRkernel')
```
set specification
```R
IRkernel::installspec()
IRkernel::installspec(user = FALSE)
```

.libPaths() to check the default library path 

```
.libPaths()
# [1] "C:/Users/mahboob/AppData/Local/R/win-library/4.2"
# [2] "C:/Program Files/R/R-4.2.2/library" 
```

# Step 2. Windows part

Now copy this path and to to system variable
shortcut:
Windows+R
```
sysdm.cpl    # Go to edit environment variables
```

Create a new key at the bottom panel

Add keyname:
R_LIBS_USER

Add paths
C:/Users/mahboob/AppData/Local/R/win-library/4.2;C:/Program Files/R/R-4.2.2/library

Now restart jupyter. all is supposed to work fine




# Further help:
https://www.drdataking.com/post/how-to-add-existing-r-to-jupyter-notebook/
https://developers.refinitiv.com/en/article-catalog/article/setup-jupyter-notebook-r


