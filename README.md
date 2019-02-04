# Robocrystallographer

[![PyPI version](https://img.shields.io/pypi/v/robocrys.svg?colorB=blue)](https://pypi.org/project/robocrys/)
[![Codacy Grade](https://img.shields.io/codacy/grade/47f851408d364efa9a8cdf0ed844cd8b.svg)](https://www.codacy.com/app/utf/robocrystallographer)
[![Codacy Coverage](https://img.shields.io/codacy/coverage/47f851408d364efa9a8cdf0ed844cd8b.svg?colorB=brightgreen)](https://www.codacy.com/app/utf/robocrystallographer)
[![CircleCI](https://img.shields.io/circleci/project/github/hackingmaterials/robocrystallographer/master.svg)](https://circleci.com/gh/hackingmaterials/robocrystallographer)



Robocrystallographer is a tool to generate text descriptions of crystal
structures. Similar to how a real-life crystallographer would analyse a
structure, robocrystallographer looks at the symmetry, local environment, and
extended connectivity when generating a description. The package includes
utilities for identifying molecule names, component orientations,
heterostructure information, and more...

## Usage

Robocrystallographer can be used from the command-line or from a python API.
The package integrates with the [Materials Project](https://materialsproject.org)
to for allow generation of structure descriptions directly from Materials Project
ids. For example, to generate the description of SnO<sub>2</sub> 
([mp-856](https://materialsproject.org/materials/mp-856/)), one
can simply run:

```bash
robocrys mp-856
```

Alternatively, a structure file can be specified in place of a Materials Project id.
Robocrystallographer supports the same file formats as 
[pymatgen](http://pymatgen.org), including the Crystallographic Information 
Format (CIF), and common electronic structure package formats such as POSCAR files.
More information can be found on the 
[command-line interface page](https://hackingmaterials.github.io/robocrystallographer/cli.html).

### Python interface

The two core classes in robocrystallographer are:

- `StructureCondenser`: to condense the structure into an intermediate JSON
  representation.
- `StructureDescriber`: to turn the condensed structure into a text description.

A minimal working example for generating text descriptions is simply:

```python
from robocrys import StructureCondenser, StructureDescriber

condenser = StructureCondenser()
describer = StructureDescriber()

condensed_structure = condenser.condense_structure(structure)
description = describer.describe(condensed_structure)
```

Where `structure` is a pymatgen Structure object. Both classes have many
options for customising the output of the structure
descriptions. More information is provided in the 
[module documentation](https://hackingmaterials.github.io/robocrystallographer/modules).

### Intermediate JSON format

The format of the intermediate JSON representation is detailed on the
[condensed structure format page](https://hackingmaterials.github.io/robocrystallographer/format.html).


### Example output

An example of the output generated by robocrystallographer for SnO<sub>2</sub> ([mp-856](https://materialsproject.org/materials/mp-856/)) is given below:

<p align="center">
<img alt="SnO2 crystal structure" src="https://raw.githubusercontent.com/hackingmaterials/robocrystallographer/master/docs/_static/rutile.jpg" height=
"200px">
</p>

```
 SnO2 is Rutile structured and crystallizes in the tetragonal P4_2/mnm space
 group. The structure is three-dimensional. Sn(1) is bonded to six equivalent
 O(1) atoms to form a mixture of edge and corner-sharing SnO6 octahedra. The
 corner-sharing octahedral tilt angles are 51°. All Sn(1)–O(1) bond lengths
 are 2.09 Å. O(1) is bonded in a trigonal planar geometry to three equivalent
 Sn(1) atoms.
```

## Installation

Robocrystallographer can be installed using pip:

```bash
pip install robocrys
```

Robocrystallographer requires Python 3.6+. The 
[OpenBabel](http://openbabel.org/wiki/Python) 
package is required to determine molecule names. This is an optional 
requirement but its use is recommended for best
results. If you are using the [Conda](https://conda.io/) package management
system, OpenBabel can be installed using:

```
conda install -c openbabel openbabel
```

## What’s new?

Track changes to robocrystallographer through the 
[Changelog](https://hackingmaterials.github.io/robocrystallographer/changelog.html).

## Contributing

Robocrystallographer is in early development but we still welcome your
contributions. Please read our [contribution guidelines](https://hackingmaterials.github.io/robocrystallographer/contributing.html)
for more information. We maintain a list of all
contributors [here](https://hackingmaterials.github.io/robocrystallographer/contributors.html).

## License

Robocrystallographer is released under a modified BSD license;
the full text can be found 
[here](https://hackingmaterials.github.io/robocrystallographer/license.html).
