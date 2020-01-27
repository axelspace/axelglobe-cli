# Changelog

## [0.9.0alpha2](https://github.com/Axelspace/axelglobe-cli/milestone/1?closed=1)

### :warning: Breaking changes

 No breaking changes

### :tada: Features

- [#1](https://github.com/Axelspace/axelglobe-cli/issues/1): Add `undownloaded` command. (Please try `$ axelglobe undownloaded --help`.)
- [#2](https://github.com/Axelspace/axelglobe-cli/issues/2): Add `read-download-histories` command. (Please try `$ axelglobe read-download-histories --help`.)

### :wrench: Fix

- Fix configuration parser parse error message.

### :+1: Misc

- Mitigate required constraints of `update-view` command's options (`title`, `bounds`, `notes` and `receive-notification`).
  - before

  ```bash
  $ axelglobe update-view --help
  axelglobe update-view
  
  Update a view
  
  Options:
    --version               Show version number                          [boolean]                                                
    -h, --help              Show help                                    [boolean]                                                
    --id                    The view id you want to update.    [string] [required]                                                
    --title                 The title represents the view.     [string] [required]                                                
    --bounds                The bounds of the area of interest. You can specify                                                   
                            this option with the GeoJSON or EWKT format.                                                          
                                                               [string] [required]                                                
    --notes                 The notes which will be useful when you see the view.                                                 
                                                            [string] [default: ""]                                                
    --receive-notification  The notification flag. When you specify `true` for                                                    
                            this option, you can receive from AxelGlobe some                                                      
                            notifications related with the view.
                                                        [boolean] [default: false]                                                
  ```

  - after

  ```bash
  $ ./axelglobe update-view --help
  axelglobe update-view
  
  Update a view
  
  Options:
    --version               Show version number                          [boolean]                                                
    -h, --help              Show help                                    [boolean]                                                
    --id                    The view id you want to update.    [string] [required]                                                
    --title                 The title represents the view.                [string]                                                
    --bounds                The bounds of the area of interest. You can specify                                                   
                            this option with the GeoJSON or EWKT format.  [string]                                                
    --notes                 The notes which will be useful when you see the view.                                                 
                                                                          [string]                                                
    --receive-notification  The notification flag. When you specify `true` for                                                    
                            this option, you can receive from AxelGlobe some                                                      
                            notifications related with the view.         [boolean]                                                
  ```

## 0.9.0alpha1

### :warning: Breaking changes

 No breaking changes

### :tada: Features

- Add `create-view` command.
- Add `read-views` command.
- Add `read-view` command.
- Add `update-view` command.
- Add `delete-view` command.
- Add `request-download` command.
- Add `read-download-history` command.
- Add `--help` option.
- Add `--help` option to each command.

### :wrench: Fix

 No major fixes.

### :+1: Misc

 No major updates.
