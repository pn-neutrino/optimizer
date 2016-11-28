
Neutrino : Optimizer component
==============================================
[![Build Status](https://travis-ci.org/pn-neutrino/optimizer.svg?branch=master)](https://travis-ci.org/pn-neutrino/optimizer) [![Coverage Status](https://coveralls.io/repos/github/pn-neutrino/optimizer/badge.svg?branch=master)](https://coveralls.io/github/pn-neutrino/optimizer)

Optimize the composer autoload by using Phalcon\Loader.

## How use :

```php
$composerOptimizer = new \Neutrino\Optimizer\Composer(
    '{path to optimized loader file}',
    '{path to vendor/composer}',
    '{path to your base application path}',
);
```

### Optimize Memory

```php
$composerOptimizer->optimizeMemory();
```

Memory optimizer use composer dumpautoload without " --optimize ". 

This significantly reduces the size of the autoload_classmap.php file and therefore the size of the generated file.
This implies that the classes will not have a direct path to their file, and thus an additional processing on the part of the autoloader (Phalcon \ Loader).

### Optimize Process

```php
$composerOptimizer->optimizeProcess();
```

Process optimizer use composer dumpautoload with " --optimize ". 

This allows to load the autoload with the link each used. 
This generates a huge array that will accelerate the loading process of the class.