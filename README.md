About WideImage library
================================

WideImage, an open-source PHP library for image manipulation
Copyright 2007-2011 Gasper Kozak

For documentation, please visit http://wideimage.sourceforge.net/


    This file is part of WideImage.
		
    WideImage is free software; you can redistribute it and/or modify
    it under the terms of the GNU Lesser General Public License as published by
    the Free Software Foundation; either version 2.1 of the License, or
    (at your option) any later version.
    
    WideImage is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Lesser General Public License for more details.
		
    You should have received a copy of the GNU Lesser General Public License
    along with WideImage; if not, write to the Free Software
    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

About WideImageBundle
================================

## Bundle Installation

This bundle is non-invasive to the original source code of WideImage.

It can be used within your symfony2 projects or any other that uses composer for package management.

## Bundle Installation with Composer (recommended)

If you are using a Symfony with composer, you need to update your composer.json file, add the entry in the require section and the repositories vcs entry set to our github repository

``` yml
    "require": {
        ...
        "wideimage/wideimage": "dev-master"
    }
    ...
    "repositories": [
        ...
        {
            "type": "vcs",
            "url": "https://github.com/ptrm04/WideImageBundle.git"
        }
    ]
```
Update your composer libraries :

``` bash
$ php composer.phar update
```
That's it, you can now use the WideImageBundle. There is no need to update your autoload.php when using composer.

## Using the Bundle

Once installed, all you need to do is create new WideImage_WideImage instances, a wee sample:

``` php
// ...
$wideImage = new \WideImage_WideImage();
$img = $wideImage->load($existing_image);
$img->resize(400,300)->saveToFile($resized_image);
// ...
```

**Using the vendors script**

Add the following lines in your `deps` file:

```
[wideimage]
    git=git@github.com:ptrm04/WideImageBundle.git
    target=bundles/wideimage
```

Download the bundle:

``` bash
$ php bin/vendors install
```

**Install using git submodules**

``` bash
$ git submodule add git=git@github.com:ptrm04/WideImageBundle.git vendor/wideimage
$ git submodule update --init
```

**Install by manually downloading the library**

Just download the files and put them under `vendor/wideimage` directory.

## Configure the Autoloader

Add the `WideImage_` prefix to your autoloader (not required if you have used composer to install this bundle):

``` php
<?php
// app/autoload.php

$loader->registerPrefixes(array(
    // ...
    'WideImage_'       => __DIR__.'/../vendor/wideimage/lib'
));
```