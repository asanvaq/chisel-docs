---
myst:
  html_meta:
    description: "Explanation of the three slice design approaches in Chisel: grouping by content type (bins, libs), function (crypto, internet) or tier (minimal, core)."
---

(slice_design_approaches)=

# Slice design approaches

There are three approaches to design slices: **grouping by type of content**,
**grouping by function** and **grouping by tier**. Depending on the package,
one of these approaches might be more suitable. It is up to the user to choose
a preferred approach.

Whichever the approach, the slices do not have to cover all the contents of a
package. It is fine to leave out files that no slice needs, such as manual pages
or examples.

```{note}
These approaches can be combined in one slice definitions file. For example,
the
[`systemd` slice definitions file](https://github.com/canonical/chisel-releases/blob/ubuntu-26.04/slices/systemd.yaml)
uses tier slices (`standard`, `dev`), function slices (`journal`, `login`,
`dbus-services`) and a content type slice (`config`).
```

(slice_design_approaches_content)=

## Grouping by type of content

This means putting all the binaries together in one slice, all the libraries
together in another slice, and so on. A good example is the
[`dpkg` slice definitions file](https://github.com/canonical/chisel-releases/blob/ubuntu-26.04/slices/dpkg.yaml).

In this case, the best practice is to create:

  In this case, the best practice is to create:
  - a `bins` slice which contains all the binaries
  - a `libs` slice which contains all the libraries
  - a `config` slice which contains all [configuration files](#create_sdf_inspect_pkg_conffiles)
  - a `scripts` slice which contains ASCII executable scripts, e.g. Python,
    Perl scripts
  - other slices analogously (e.g. `data`, `modules`, `services`, etc)
  
  You may split the above slices into more granular ones, but you should
  reserve the above as a catch-all for their respective types
