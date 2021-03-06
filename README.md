CBM Firmware Repository
=======================

The CBM firmware repository collection contains the source code for
all firmware used in the CBM experiment.

Repository Access
-----------------

Read access is open to all CBM collaborators.

Commits should only be performed by the person responsible for the
respective design or component, or by his or her
representative. Contributions from other developers are welcome and
should be handled via pull requests.

Firmware structure
------------------

The Firmware is structured into `cores` and `designs`. Purpose of this
structure is to provide defined interfaces between sub-projects with a
minimal set of rules.

A core is a major building block that is used by several different
designs. This does not include minor cores like FIFOs or RAM blocks,
which may be part of a core or a design. For each core an interface
documentation and an example design should be provided.

A design is a major firmware design project. A design may include
cores as well as other sources.

For each component (design/core) a separate git repository may
exist. A repository may also contain several components if they are
closely related. Cores can be included into design repositories via
the `git submodule` functionality.


Build results
-------------

Each firmware component must support fully automated builds. A file
named `autobuild` should exist executing all necessary steps for a
build.

Builds for cores should result in synthesized netlists and matching
constraints. Designs containing the respective core include these
netlists/constraints during their build flow.

Builds for designs should result in FPGA bitfiles and PROM files if
applicable.


General guidelines for the contents of the CBM firmware repositories
--------------------------------------------------------------------

- **Include all sources and scripts**  
  To ensure that a firmware image can be modified and rebuilt at a
  later time, all sources and scripts required to build the firmware
  image should be included in the repository.

- **No generated or unused files**  
  Files that can be automatically generated only clutter the
  repository and should not be committed. The same applies to source
  code files that are not used in the project.

- **No binary files**  
  In general, large binary (i.e., non-text) files should not be
  committed as they are not handled well by version control.

- **Use only temporary branches**
  Stick to the standard use of branches. In general, branches should
  be temporary and merged with the master at some point. Tags can be
  used to label specific versions.


Source Code Quality
-------------------

The repositories are meant as a platform for source code exchange
between the groups involved and as an archive for CBM. The code
uploaded into the repository master branch should meet the quality
standards generally associated with **production** or **testing
level** code. It should not contain early development code or code
that does not compile/synthesize.
