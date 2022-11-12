# Common Headers For Jupyter notebook

python {```
import os
import shutil
from pathlib import Path
import pandas as pd
import numpy as np
import parquet
from skimpy import skim, clean_columns

from IPython.display import display, HTML, display_html, Markdown, Image, Math, Latex
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity='all'

pd.options.display.max_rows = 1000
pd.options.display.max_colwidth=120
pd.options.mode.chained_assignment = None
pd.options.mode.chained_assignment = None
```
