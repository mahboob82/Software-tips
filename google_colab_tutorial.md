# Tutorial on google-colab usage:

## Set up colab and google drive communication

> First check your current directory in colab. You'll probably be on `content` foloder.

```python
!pwd

# output
"\content"
```

> At the beginning, after a new notebook is created, the '\content' directory will be almost empty. 
> A simple ``!ls -la '.'`` will produce something similar to below:
```
total 16
drwxr-xr-x 1 root root 4096 Nov 15 14:31 .
drwxr-xr-x 1 root root 4096 Nov 17 04:22 ..
drwxr-xr-x 4 root root 4096 Nov 15 14:30 .config
drwxr-xr-x 1 root root 4096 Nov 15 14:31 sample_data
```

> Now, you would want to mount to the google drive of of google account. 
> By default, google-colab will save your newly created python notebooks to your google drive. 
> You could find the notebook under ``Colab Notebooks`` directory on your drive account.
> However, you cannot save your personal files in your drive directly.
> For doing that you have to mount to your drive explicitely.

> Let's create a mount point named 'drive'. It can be anything. Just chose a name you like.
> At first mountpoint creation, colab doesn't know which account to use for.
> So, give proper permissions for your target account.

```python
from google.colab import drive
drive.mount('/content/drive')
```

> `!ls -la '.'`

```diff
total 20
+ drwxr-xr-x 1 root root 4096 Nov 17 04:36 .
+ drwxr-xr-x 1 root root 4096 Nov 17 04:22 ..
+ drwxr-xr-x 4 root root 4096 Nov 15 14:30 .config
- drwx------ 5 root root 4096 Nov 17 04:36 drive
+ drwxr-xr-x 1 root root 4096 Nov 15 14:31 sample_data
```

> Let's see what's inside the `drive` via `!ls -la 'drive'`
```
total 16
dr-x------  2 root root 4096 Nov 17 04:36 .file-revisions-by-id
drwx------ 16 root root 4096 Nov 17 04:36 MyDrive
dr-x------  2 root root 4096 Nov 17 04:36 .shortcut-targets-by-id
drwx------  5 root root 4096 Nov 17 04:36 .Trash-0
```

> The `MyDrive` location has all your previously uploaded google-drive files. 
> It would also have 'Colab Notebooks'

```
total XX
...
drwx------ 2 root root 4096 Feb 20  2021 'Colab Notebooks'
...
```

>Let's make a new folder `dfs` inside `MyDrive`
```
!mkdir 'drive/MyDrive/dfs'
!ls -la 'drive/MyDrive'
```

## Save a dataframe from your colab environment to your google drive

> Suppose you have a dataframe `mydata` which you want to save into `dfs` folder.
> I will use the `titanic` dataset from seaborn pacakge. 
> Get a list of all datasets using `sns.get_dataset_names()`

```python
import seaborn as sns
import seaborn as sns
sns.get_dataset_names()
```

```python
mydata = sns.load_dataset("titanic")
mydata.head()
```

```
survived	pclass	sex	age	sibsp	parch	fare	embarked	class	who	adult_male	deck	embark_town	alive	alone
0	0	3	male	22.0	1	0	7.2500	S	Third	man	True	NaN	Southampton	no	False
1	1	1	female	38.0	1	0	71.2833	C	First	woman	False	C	Cherbourg	yes	False
2	1	3	female	26.0	0	0	7.9250	S	Third	woman	False	NaN	Southampton	yes	True
3	1	1	female	35.0	1	0	53.1000	S	First	woman	False	C	Southampton	yes	False
4	0	3	male	35.0	0	0	8.0500	S	Third	man	True	NaN	Southampton	no	True
```

> Remember,  you are still in "\content" folder. And your save destinations is 
> `./drive/MyDrive/dfs/`

```python
mydata.to_csv("./drive/MyDrive/dfs/titanic.txt", index=None, sep='\t')
```
> Now, confirm if file is there or not?
``` python
!ls -la ./drive/MyDrive/dfs
```

Output:

```
total 56
-rw------- 1 root root 57018 Nov 17 05:35 titanic.txt
```
> Check for 
```python
!head ./drive/MyDrive/dfs/titanic.txt | column -t
```

```python
survived  pclass  sex     age   sibsp  parch   fare     embarked  class  who    adult_male  deck         embark_town  alive  alone
0         3       male    22.0  1      0       7.25     S         Third  man    True        Southampton  no           False
1         1       female  38.0  1      0       71.2833  C         First  woman  False       C            Cherbourg    yes    False
1         3       female  26.0  0      0       7.925    S         Third  woman  False       Southampton  yes          True
1         1       female  35.0  1      0       53.1     S         First  woman  False       C            Southampton  yes    False
0         3       male    35.0  0      0       8.05     S         Third  man    True        Southampton  no           True
...
```

## Read data from local computer
> Open a file browser on google colab and select files for upload using widget appears below the cell.
```python
from google.colab import files
uploaded =files.upload()
```
> You can see which files are upload via looping over the `uploaded` dictionary. 
> Don't access the 'value' which might slow down the process if file is big.

```python
for k in uploaded.keys():
  print(k)
```
Suppose outputs are:
```
file1.txt
file2.txt
```
> We can easily access the file using any pythonic methods. 
> To demonstrate, I will use pandas to read file1.txt

```python
mydf = pd.read_csv('file1.txt')
```

> Now I can follow `mydf` into my google-drive following steps above.

-- Happy computing

### END OF TEXT.



