NetCDF ZARR Specification
====================================

# Abstract

*This document specifies how a variant of Zarr will be
supported by the netcdf-c library.*

*Distribution of this document is currently restricted to Unidata.*

# Introduction {#nczarr_intro}

The Unidata NetCDF group is proposing to provide access to cloud
storage (e.g. Amazon S3) by providing a mapping from a subset of
the full netCDF Enhanced (aka netCDF-4) data model to one or
more existing data models that already have mappings to
key-value pair cloud storage systems.

The initial target is to map that subset of netCDF-4 to the Zarr
data model. As part of that effort, we intend to produce a
set of related documents that provide a semi-formal definition
of the following.

1. An abstract representation of the NCZarr data model.
2. A description of the subset of the netCDF API that conforms
   to the NCZARR data model. This interface will be the basis
   for programatically reading and writing cloud data via the
   netcdf-c library.
3. A mapping of the NCZarr data model to some variant of the
   Zarr storage representation, This representation is a
   combination of a mapping to Json plus a mapping to an
   abstract key-value pair interface.
4. The internal architecture of the cloud support in the netcdf-c
   library.

The term "semi-formal" is used because rather than provide
complete mathematical or operational semantics, prose text will
be used to describe the context-sensitive features of the model.
Complete formalization to produce an operationally defined
specification is a possible future activity.

The approach to all of this is based on using modern compiler
technology. Compilers are centered around the notion of an
"abstract syntax tree" (aka AST).  The term "abstract
representation" will also be used as a synonym for AST.

The tree is constructed in a compiler by using some form of
parser to parse programs in the language into a tree containing
the essential elements of the program.  The nodes of the tree are
typed using some typing model such object-oriented classes.

In a compiler, and given the AST, the tree is processed
repeatedly to perform constext sensitive checking and to
annotate it with semantic information (such as linking type
references and type declarations).

Lastly, the tree is used to generate the final product.
Typically for a compiler, this is the code to execute.

This specification differs from compilers in a number of ways.

1. The AST is defined semi-formally using some typed language.
2. Instead of using a parser to construct the tree,
   an API is provided that effectively defines how to construct
   a legal instance of the tree. That is the purpose of document
   number 2 in the previous list.
3. The final step, code generation, is replaced by a mapping
   where each node in the abstract tree is mapped to a combination of
   key-value pairs and Json representations of the content of the
   node. It is this choice of mapping that ultimately connects
   the netcdf-c API to the Zarr formatted cloud storage.

# Copyright
_Copyright 2018, UCAR/Unidata<br>
See netcdf/COPYRIGHT file for copying and redistribution conditions._

# Point of Contact

__Author__: Dennis Heimbigner<br>
__Email__: dmh at ucar dot edu<br>
__Initial Version__: 11/28/2018<br>
__Last Revised__: 12/8/2018