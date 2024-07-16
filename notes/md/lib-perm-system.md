<h1 align="center">Gex programming language</h1>

<p align="center">
  <img style="width: min(15vw, 15vh);" src="../../img/gex3.svg">
</p>

<div align="center">
    <h2 align="center">-&nbspLibrary permision system&nbsp-</h2>
    permisions for <strong>accessing libraries</strong>
    and permisions for <strong>libraries to access system</strong>
    <h3>
        Note: this only works with fully gex modules
        and gex libraries, that use types and classes,
        that gex interpreter can pass permisions to.
    </h3>
</div>

## Why?
**For safety**, gex language has permision system for gex modules to limit their access to system (resources)  
**such as file system and use of external libraries**.

## Where can I find default gex language permisions and how to modify them?
1. When using gex interpreter **as a system binary**, permisions can be dumped by using `--dump-perms` flag.

   But when using **embeded gex**, then (if you have access to stdout) you can dump permisions to stdout (dy default: console) by using `__dump_perms()` function

2. To overwrite gex permisions for gex script run by **system binary**, `--perms` flag should be used with path to file containing permisions.
   And to do the same thing with **embeded gex**, we use `gex::load_perms_from_file()` function in C++ gex api with path to permisions

## Types of permisions
- looping permisions
  - iterating throuth list of values  
    
    
