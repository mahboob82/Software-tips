# How can you start CMD with a multiple panes layout?

## First way:
### Create a shortcut on desktop
Layout in mind: Three panes: 1 on the left and 2 on the right (vertical)
        
Steps: 
1. Right click anywhere on the desktop
2. Go to New > Create a shortcut
3. Copy and paste the following command
   ``` {cmd}
    C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe -d C:\Users\mahboob\Documents ; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github
   ```  
4. OR,
 ``` {cmd}
   C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe ; new-tab -p "Command Prompt"; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project; split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github
   ```
5. Go to next
6. Give a name of the shortcut
7. Try the shortcut. Yes, there you are.

### Important
  1. This path_str must not be more than 260 character. Windows shortcuts are limited to only 260 chars.
  2. Do not put a semicolon at the end of the path_str. Otherwise, it will add an extra CMD tab at the end which is annoying.
  3. After exe path put an extra space before semicolon such as "\wt.exe ; "
  4. ```Option 3``` path_str do not add an extra cmd tab
  5. ```Option 4``` path_str does add an extra cmd tab
  6. Explanation of the option 5 path_str

```diff
-# exe path
      C:\Users\mahboob\AppData\Local\Microsoft\WindowsApps\wt.exe ;
-# adds a new tab and sets its path to Documents folder
      new-tab -p "Command Prompt" -d C:\Users\mahboob\Documents;
-# Then splits the pane on right horizontally and sets path to R-project folder
      split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\R-project ;
-# Again splits the pane on right but vertically and sets path to Github folder
      split-pane -p "Command Prompt" -d C:\Users\mahboob\Documents\Github      
```

## Second way

### Manual shortcut
1. Open a cmd prompt
2. Horizontal split: ``` alt+shift+plus ```    (plus over equal key, not number pad)
3. Vertical split:  ``` alt+shift+minus ```    (minus over dash key, not number pad)
4. Manually cd to your desired directories.

* You can move from one to another pane by:
        left to right:  ```alt+left/right```
        top to bottom:  ```alt+down/up```
        
 * Resize:  ```alt+shift+left/right```  or ```alt+shift+up/down```
        






