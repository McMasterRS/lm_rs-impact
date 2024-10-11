---
layout: default
title: Software Hash Identifiers
parent: Digital Object Identifier
nav_order: 1
---

# Software Hash Identifier (SWHID)

Similar to DOIs, Software Hash Identifiers (SWHIDs, also known as Software Heritage Identifers) are persistent, intriinsic identifiers developed by [Software Heritage Network](https://www.softwareheritage.org/). Software Heritage is a non-profit, long term archive for software source code. It does not only store software artifacts, but also the full version control history.  

SWHIDs are organized using a tree-like filesystem hierarchy and include special nodes to track revisions, releases, full version control systems, and all branches. Unlike DOIs, which track changes of the software projects or releases as a whole, SWHIDs is developed to track all individual components within a software project.  

## SWHID Syntax

A SWHID consists of two separate parts, the core identifer and an optional list of qualifiers. The core identifier identifies any software artifacts or objects, while the qualifiers allow specification of the context where the object is meant to be seen and points to a subpart of the object itself.  

### Core Identifier

The core identifier is composed of 4 fields separated by colons `:`.

Example: `swh:1:dir:93711e958cdde0b729ab948d3a904399dae0c890`. 

- `swh` is the identifier prefix. 
- `1` is the version of the identifier scheme. 
- `dir` indicates the type of object ot be directories, there are also `cnt` (contents), `rev` (revisions), `rel` (releases) and `snp` (snapshots). 
- `93711e958cdde0b729ab948d3a904399dae0c890` is the indicates the intrinsic identifiers, which is a string of hex encoded lowercase ASCII characters computed from the content and relevant metadata of the object. 

### Qualified Identifiers

A qualifier may be a *fragment qualifier*, which identifies subparts of a software artifact, or a *context qualifier*, which provides additional context on the software artifact.  

Each qualifier is specified as a key-value pair, using an `=` character as a separator. Qualifiers are separated from the core identifier and from each other by using a `;` character.  

Example:  

```
swh:1:dir:93711e958cdde0b729ab948d3a904399dae0c890;
origin=https://github.com/McMasterRS/WARIO;
visit=swh:1:snp:0369ad5f0f4b74eb586fbd130ca47e2cb6ac8034
```

- `swh:1:dir:93711e958cdde0b729ab948d3a904399dae0c890` is the core identifier as discussed previously. 
- `origin` declares the origin of the software. 
- `visit` indicates the snapshot of the repository where the software artifact can be observed, this fragment qualifier is only valid when the `origin` qualifier is present. 

## How to Get a SWHID?

SWHIDs are automatically generated when your source code or software artifacts are archived within the Software Heritage archive.  

If your software source code is hosted on a public repository, such as GitHub, you can manually submit it to Software Heritage using their [web interface](https://www.softwareheritage.org/features/). Additionally, Software Heritage periodically crawls and harvests source code from various public repositories, ensuring that a wide range of software is automatically archived.  

Once Software Heritage captures a snapshot of your source code, it is securely preserved in their extensive archive. At this point, a SWHID is generated and available on the Software Heritage's archive browser.  

## Reference

- [SWHID.org Specification v1.1](https://www.swhid.org/specification/v1.1/0.Introduction/)
- [Archiving and Referencing Source Code with Software Heritage](https://arxiv.org/abs/2004.00514)
