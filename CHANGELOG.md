# Changelog

## 0.9.0alpha5

### :warning: Breaking changes

 No breaking changes.

### :tada: Features

 No feature updates.

### :wrench: Fix

- Increase heap memory size to deal with a large size of file.

### :+1: Misc

- Update libraries


## [0.9.0alpha4](https://github.com/Axelspace/axelglobe-cli/milestone/2?closed=1)

### :warning: Breaking changes

 **We will change how we deliver AxelGlobe products to a two step process, allowing you to access our data sooner.**

- In the first pass we will do a basic requirements check to release the image quickly.
- In the second pass we will do a more in depth check to verify the image quality.

 After the image passes the first checking step, the images will be available to download.

 If you wish to **only view images which have passed the second level quality check**, **you need upgrade axelglobe-cli to 0.9.0alpha4**.
 Once you upgrade to `0.9.0alpha4`, you can filter out the fast validation images by turning on the "Quality Control" setting on each command.
 Please check the below updates on each command in detail.

### :tada: Features

- [#6](https://github.com/Axelspace/axelglobe-cli/issues/6): Quality control flag for `request-download` command
  - If you execute `axelglobe request-download --help`, you can see the usage of `quality-control` option in detail.

```diff
axelglobe request-download

Request to create bundles to download

Options:
      --version                  Show version number                   [boolean]
  -h, --help                     Show help                             [boolean]
      --view-id                  The view id which has AOI you want to request
                                 to download.                [string] [required]
      --dates                    The captured date for the AOI you want to
                                 request to download.      [array] [default: []]
      --latest                   The latest flag. When you specify `true` for
                                 this option, the server will try to find the
                                 latest tiles AxelGlobe can provide for you.
                                                      [boolean] [default: false]
+      --quality-control          The quality-control flag. If you wish to only
+                                 view images which have passed the second level
+                                 quality check, you can filter out the fast
+                                 validation images by turning on the
+                                 quality-control option.
+                                                       [boolean] [default: true]
      --max-cloud-rate           The maximum limit of the cloud rate you can
                                 accept.                [number] [default: null]
      --min-off-nadir-angle      The minimum limit of the off-nadir angle you
                                 can accept.            [number] [default: null]
      --bundle-type              The type of the product bundle. You can use
                                 this option for specifying the purpose of the
                                 product bundle.
                    [string] [choices: "VISUAL", "ANALYTIC"] [default: "VISUAL"]
      --bundle-compression       The compression format of the product bundle.
                                     [string] [required] [choices: "TAR", "ZIP"]
      --product-format           The type of the product. You can use this
                                 option for specifying image format.
           [string] [required] [choices: "GEO_TIFF_NO_COMPRESSION", "JPEG_2000"]
      --product-data-projection  The data projection of the product.
                                      [string] [choices: "UTM"] [default: "UTM"]
      --resampling-algorithm     The resampling method of the image processing.
            [string] [choices: "NEAREST_NEIGHBOR"] [default: "NEAREST_NEIGHBOR"]
      --poll-and-download        The flag whether trying to polling and download
                                 as soon as bundles are ready to download. When
                                 you specify `true` for this option, you can
                                 poll the requested download history status
                                 until the status turns to be ready to download.
                                                      [boolean] [default: false]
      --polling-interval-sec     Try to poll and download every this seconds.
                                 This option is valid if you specify `true` for
                                 the 'poll-and-download' option. The lower limit
                                 is '180'.               [number] [default: 180]
      --max-polling-count        The maximum polling count you want to try to
                                 polling. This option is valid if you specify
                                 `true` for the 'poll-and-download'. The upper
                                 limit is '20'.            [number] [default: 2]
      --download-dir             The path to the directory you want to download
                                 a bundle into. This option is valid if you
                                 specify `true` for the 'poll-and-download'
                                 options.                [string] [default: "."]
      --overwrite                The overwrite flag. When you specify `true` for
                                 this option and the same file name exists on
                                 the download directory, you can force download
                                 with overwriting the previous file. This option
                                 is valid if you specify `true` for the
                                 'poll-and-download' option.
                                                      [boolean] [default: false]
```

- [#7](https://github.com/Axelspace/axelglobe-cli/issues/7): Quality control flag for `undownloaded` command
  - If you execute `axelglobe undownloaded --help`, you can see the usage of `quality-control` option in detail.

```diff
axelglobe undownloaded

Search the tiles you have not downloaded yet

Options:
      --version              Show version number                       [boolean]
  -h, --help                 Show help                                 [boolean]
      --view-id              The view id which has AOI you want to request to
                             download.                       [string] [required]
      --start-date           The search start date. e.g. 2020-01-01
                             If you don't specify both 'start-date' and
                             'end-date', this will be set as 30 days before the
                             midnight of UTC current time.
                             If you don't specify 'start-date' and specify
                             'end-date', this will be set as 30 days before the
                             'end-date'.
                                                                        [string]
      --end-date             The search end date. e.g. 2020-01-10
                             If you don't specify both 'start-date' and
                             'end-date', this will be set as the midnight of
                             UTC current time.
                             If you don't specify 'end-date' and specify
                             'start-date', this will be set as 30 days after
                             the 'start-date'.
                                                                        [string]
      --max-cloud-rate       The maximum limit of the cloud rate you can accept.
                                                        [number] [default: null]
      --min-off-nadir-angle  The minimum limit of the off-nadir angle you can
                             accept.                    [number] [default: null]
+      --quality-control      The quality-control flag. If you wish to only
+                             retrieve undownloaded images which have passed the
+                             second level quality check, you can filter out the
+                             fast validation undownloaded images by turning on
+                             the quality-control option.
+                                                       [boolean] [default: true]
```

### :wrench: Fix

 No major fixes

### :+1: Misc

- Update libraries

## 0.9.0alpha3

### :warning: Breaking changes

 No breaking changes

### :tada: Features

- Support download analytic products. (Please try `$ axelglobe request-download --help`.)
  - You can request to download analytic products like the followings.

  ```bash
  $ axelglobe request-download --view-id '${SOME_VIEW_ID}' \
  --dates '2019-11-20' \
  --max-cloud-rate 7 \
  --bundle-compression 'TAR' \
  --product-format 'GEO_TIFF_NO_COMPRESSION' \
  --bundle-type 'ANALYTIC'
  ```

  - The diff of `$ axelglobe request-download --help` between `0.9.0alpha2` and `0.9.0alpha3` is like the followings.

  ```diff
  $ axelglobe request-download --help

  axelglobe request-download

  Request to create bundles to download

  Options:
    --version                  Show version number                       [boolean]
    -h, --help                 Show help                                 [boolean]
    ...
    --bundle-type              The type of the product bundle. You can use this
                               option for specifying the purpose of the product
                               bundle.
  -                                [string] [choices: "VISUAL"] [default: "VISUAL"]
  +                    [string] [choices: "VISUAL", "ANALYTIC"] [default: "VISUAL"]
  ```

### :wrench: Fix

 No major fixes

### :+1: Misc

 No major updates

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
