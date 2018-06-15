
# Deptree:

<h2 style="color: black;"> Automate OSS Compliance Work in Yocto<sup style="font-size: 0.6em;">@fa[registered]</sup> Projects</h2>

---

## FOSSology 

- FOSSology<sup style="font-size: 0.6em;">@fa[trademark]</sup>  is a powerful tool, but many processes must be run manually, file-by-file, package-by-package
- luckily, there are some CLI tools

---

## Yocto

- are you all familiar with Yocto?
- if you want to bake, you need recipes
- hw manufacturers do not provide ad-hoc linux distros but Yocto recipes
- only a fraction of OSS source code fetched by Yocto ends up in firmware
- manually finding (hundreds of) relevant packages and uploading them to FOSSology: a crazy task

---

### Technical Context

- Linux Embedded project with custom/proprietary code written in C/C++
- dependencies: only static and dynamic linking
- don't touch the compiling machine! 

---

### Legal Context

- proprietary/custom packages ("own packages") and dependencies of own packages deserve a more in depth analysis than "mere-aggregation" packages
- conflicts with OSS (Copyleft) licenses are more likely to happen with proprietary/custom packages (no public scrutiny)

---

### How it works, in practice (1)

- Snapshot of Yocto build dir, copied to a dedicated FOSSology machine (with Deptree)
- Automatic [BAT](http://www.binaryanalysis.org/) scan
- Automatic detection of dynamic deps for each binary file
- Automatic detection of each binary file's package

---

### How it works, in practice (2)

<li style="font-size:xx-large">Mark "own" packages</li>
<li style="font-size:xx-large">Automatic detection of dependencies of own packages and "mere-aggregation" packages</li>
<li style="font-size:xx-large">Automatic upload of all packages to FOSSology, already organized in folders by project -> version -> category (own/deps-of-own/mere-aggregation)</li>
<li style="font-size:xx-large">Automatic schedule of FOSSology scan/bulk agents for all packages (include reuse of previous clearing decisions)</li>

---

### How it works, in practice (3)

- license clearing of deltas with respect to previous versions of the same project
- manually spot and mark static dependencies
- Any legal issues?
- Automatic sync of FOSSology results with Deptree 
- present results in a simple and meaningful way

---
### Let's see it in action

---
### TODO (1)

<ul>
    <li style="font-size:xxx-large">continuous integration in the build process</li>
    <ul>
        <li style="font-size:xx-large">implementation of a full CLI interface</li>
    </ul>
    <li style="font-size:xxx-large">modularity (building block approach) and independency from any specific tool</li>
    <ul>
        <li style="font-size:xx-large">define main building block types that are always needed to implement an automatic OSS Compliance process (regardless of the specific technical environment)</li>
        <li style="font-size:xx-large">implement a db of packages, licenses and SPDX data</li>
    </ul>
</ul>

---
### TODO (2)

- Yocto-specific building blocks:
    - automatic snapshot and copy of yocto build dir on FOSSology machine
    - automatic detection of static dependencies
    - automatic mapping of irrelevant files

---
### TODO (3)

- license mapping at binary level (and not only at package level)
- enable implementation of company's internal OSS policies

- a better name?

---
@title[Copyright and License]
<div class="bottom">
@fa[copyright fa-red] 2018 - Alberto Pianon; Carlo Piana (some rights reserved)   
Creative Commons by-ND-NC 4.0 Unported Licence

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.

<p>produced with [Gitpitch](https://gitpitch.com/) and [Reveal.js][81aa3153]</p>

Fossology and Yocto are trademarks of the [Linux Foundation](https://www.linuxfoundation.org/)


</div>

  [81aa3153]: https://revealjs.com/ "Reveal"
