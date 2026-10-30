---
myst:
  html_meta:
    description: "Explanation of the two slice design approaches in Chisel: grouping by content type (bins, libs) or by functionality (minimal, core, standard)."
---

(slice_design_approaches)=

# Slice design approaches

There are two approaches to design slices: **grouping by content** and **grouping by function**. Depending on the package, one of these approaches might be more suitable. It is up to the user to choose a preferred approach.

## Grouping by type of content

 This means putting all the binaries together in one slice, all the libraries together in another slice, and so on.
 A good example is the [`dpkg` slice definitions file](https://github.com/canonical/chisel-releases/blob/ubuntu-24.04/slices/dpkg.yaml).

  In this case, the best practice is to create:
  - a `bins` slice which contains all the binaries
  - a `libs` slice which contains all the libraries
  - a `config` slice which contains all [configuration files](#create_sdf_inspect_pkg_conffiles)
  - a `scripts` slice which contains ASCII executable scripts, e.g. Python,
    Perl scripts
  - other slices analogously (e.g. `data`, `modules`, `services`, etc)
  
  You may split the above slices into more granular ones, but you should
  reserve the above as a catch-all for their respective types
