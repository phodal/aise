# 代码片段生成


## JetBrains 自带


### Jupyter

  Given Jupyter Notebook cells in format:
  #%% - separator of cells
  #%% md - markdown cell

  Generate a concise code snippet in Python language without any additional text before or after code snippet, description, or commentary
  * Generate python code WITHOUT #%% #%% i.e. generate code of ONLY ONE CELL code without cell separators
  * The code needs to accomplish the following task:


### Semantic Search

    *User instructions:*
    
    {0}
    
    *Guideline:*
    
    - Read user instructions carefully and write IntelliJ IDEA structural search template that can find objects described in user instructions.
    - Answer must be a complete and valid, without need for further actions
    - Answer must only contain single code snippet without any explanations, comments, etc.
    