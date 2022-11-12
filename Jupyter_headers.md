# Common Headers For Jupyter notebook

```python
import os, sys
import glob
import shutil
import subprocess
from pathlib import Path
import pandas as pd
import numpy as np
import parquet
from skimpy import skim, clean_columns
from functools import reduce
from rich import print as rprint

from IPython.display import display, HTML, display_html, Markdown, Image, Math, Latex
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity='all'

pd.options.display.max_rows = 1000
pd.options.display.max_colwidth=120
pd.options.mode.chained_assignment = None
pd.options.mode.chained_assignment = None


## Utils header
import warnings
# warnings.filterwarnings('ignore')

# display(HTML("<style>.container { width:100% !important; }</style>"))
# display(HTML(data="""
# <style>
#     div#notebook-container    { width: 95%; }
#     div#menubar-container     { width: 65%; }
#     div#maintoolbar-container { width: 99%; }
# </style>
# """))

editor_path = r"C:\Program Files (x86)\Notepad++\notepad++.exe"

```
