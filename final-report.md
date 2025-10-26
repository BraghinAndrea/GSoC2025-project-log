# GSoC 2025 — Final Report

## Organization: BRL-CAD

**Improving the k-File to BRL-CAD Converter & proposal for BRL-CAD database to k-File converter.**

Contributor: **Andrea Braghin**, Italy

Mentors: **Sean Morrison & Ali Haydar**

Period: June–October 2025

Repo (daily reports & plan): [GSoC2025-project-log](https://github.com/BraghinAndrea/GSoC2025-project-log/tree/main) 

## Abstract
This project is intended to improve the interoperability between LS‑DYNA and BRL‑CAD by enhancing the existing k‑g converter. 
The primary goal is to facilitate a seamless data exchange between LS‑DYNA keyword files and BRL‑CAD geometry databases, ultimately streamlining workflows for users who need to transition between advanced simulation and detailed geometric modeling.

## Scope

Extended the BRL-CAD k-g LS-DYNA keyword converter with new elements, sturdier parsing, and transformation support alongide error and small bugs fixing.
Drove multiple PRs from prototype → review → merge, with iterative fixes from mentors feedbacks.

## Key Deliverables

Considering BRL-CAD fundamental approach of creating a geometry from boolean operation on
primitives, one can transform any element or mesh in LS-DYNA to a BRL-CAD geometry.
Extensive work has been done by previous years’ contributors but a noticeable number of
elements, commands and sections was still in need of implementation. I adopted a sweeping
approach based on LS-DYNA documentation assessing the objects that can be converted to
geometry allowing the successful conversion of a noticeably larger number of .k files.

Addressing previous work suggestion found on the preferred organization communication channel on Zulip I started testing the conversion of Toyota veichles .k file found on [this page](https://www.dynaexamples.com/implicit/yaris-static-suspension-system-loading/) and THUMS crash body models [here](https://www.toyota.co.jp/thums/).

Many parts\elements weren't being converted as not yet implemented in the k-g converter. So the first period has been about implementing new key missing elements in order to expand the converter capabilities.

LS-DYNA documentation has been followed throughout the whole project and taken as reference point. Link to the developer manuals can be found at the end of this report.

### Seatbelt
The successfull implemented of *ELEMENT_SEATBELT and *SECTION_SEATBELT allows the converter to handle such instances. It is now able to detect the two possibile types of Element_Seatbelt that can be generated in LS-DYNA. The first being a 2d line and the latter a shell-based geometry. By leveraging the node numbering the parser can store valuable geometrical ingormations needed for the graphical representation.

The following pictures represents the LS-DYNA model and the shell-made seatbelt.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/9c0f0de9-0cdc-4adf-b1ec-858d1d1e56c7" /> 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/03b9e88b-a752-40fd-9747-85c2c96636f5" />

A test example with both seatbelt types generated at the same time was created and successfully converted as shown in mged below:

<img width="500" height="500" alt="07July" src="https://github.com/user-attachments/assets/3feacbf2-4299-468c-91b0-aff424e04c2c" />


The geometry was imported in BRL-CAD maintaining LS-PrePost coordinates and the relative code well integrated into the main k-g converter loop. in k-g.cpp

Relative pull request can be found [here](https://github.com/BRL-CAD/brlcad/pull/194).

### Discrete Spheres
The challange of implementing physical particles was accepted as the representation of *ELEMENT_DISCRETE_SPHERE can be an interesting aspect for BRL-CAD. *ELEMENT_DISCRETE_SPHERE can be used in various FEA models and the ability to convert it can result in a appealing software carachteristic.
Its implementation required new formulations that can be found at [this pull request history](https://github.com/BRL-CAD/brlcad/pull/198#event-19425863706).

An example of converted geometry for a box full with particles of various random dimensions can be found below: 

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/687b6c7c-ed0a-476a-b8f1-bcedd0510781" /> 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7e8b3beb-8433-4ebd-873d-2d3f21abf7b9" />

### Section Parsing improvements

SECTION_SHELL: Built a robust, card-counting approach that tolerates titles, option order, and multiple sections under a single keyword.
Various configurations of options for *SECTION_SHELL were considered based on LS-DYNA reference manual
Supported options: EFG, THERMAL, XFEM, MISC.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/18946862-8a76-45a7-a80d-d8f3b492faf8" />

SECTION_SOLID: resolved multiple “Unexpected … length” errors. The newly added NumberOfCards tracking has been expanded to SECTION_SOLID as well.
The new improved code helped converting all the .k file that previosly resulted in a partially converted vehicle as shown below:

<img width="500" height="500" alt="partial Yaris" src="https://github.com/user-attachments/assets/ad9e392e-8be5-4153-95e1-2ef5ff88a2c5" />

The improved k-g converter version can now handle it better with no evident missing part as follow in these pictures:

<img width="500" height="500" alt="image-1761508624236" src="https://github.com/user-attachments/assets/af68d434-1244-4e4f-920e-eca0cb23f36a" />
<img width="500" height="500" alt="image-1761508622235" src="https://github.com/user-attachments/assets/a5dc2e30-a584-4f86-a194-98bd94860964" />

History and [pull requests](https://github.com/BRL-CAD/brlcad/pull/203)
### Include/Transformations

Implemented *INCLUDE_TRANSFORM with *DEFINE_TRANSFORMATION following the *INCLUDE keyword already present.
This work is still in progress, a first draft pull request can be found [here](https://github.com/BraghinAndrea/brlcad/commit/396f59409f5e5e847038ad66cc79ef9e732299e3).

It seems now able to follow the *INCLUDE_TRANSFORM keyword and apply the transformations described through *DEFINE_TRANSFORMATION. An example can be seen below as the .k file calls for the conversion of both the car and the ground from two separate files. For testing purposes a 90° rotation was added and correctly caught from the the converter.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e73a3f3e-0204-4af8-a562-fb0db2270622" />
<img width="500" height="500" alt="transformation" src="https://github.com/user-attachments/assets/120134c6-ece8-49fe-821d-f61662277a44" />

Extensive work can still be done on formatting, transformations implementation and testing for *INCLUDE_TRANSFORM card.

## Milestones (high-level)

Jun 2–7: Seatbelt prototype, initial tests.

Jun 30–Jul Seatbelt integrated into main k-g.cpp loop, PR opened.

Jul 7–12: Fixed shell seatbelt bugs, Discrete Sphere parsing & PR added.

Aug 18–29: DSphere PR updated, major push on “Unexpected length” errors, created comprehensive test cases for *SECTION_SHELL.

Sep 16–24: Big upgrade to SECTION_SHELL (EFG/THERMAL/XFEM/MISC, titles, option order independence).

Oct 10–20: Implemented INCLUDE_TRANSFORM + DEFINE_TRANSFORMATION, followed up on SECTION_SOLID robustness.


## Acknowledgements
I would like to thank the whole Google Summer of Code organization for provind such a successfull program uplifting young developers and the open source community.
I had the opportunity to test myself, learn and ultimately grow as a person even. This project covered a long stretch of time in my case, I am greateful for the flexible scheduling I was allowed to follow.

Huge thanks to BRL-CAD and my mentors Sean and Ali for reviews, design discussions, and guidance.

Frankly this was not the GSoC I was hoping for but it became a companion throughtout difficulties, ups and downs. An important step in my journey I'll be always proud of.  


BRL-CAD — [GitHub repo](https://github.com/BRL-CAD/brlcad)

LS-DYNA documentation - [here](https://lsdyna.ansys.com/manuals/)

