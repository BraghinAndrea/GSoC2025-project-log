# GSoC 2025 — Final Report

## Organization: BRL-CAD

**Improving the k-File to BRL-CAD Converter & proposal for BRL-CAD database to k-File converter.**

Contributor:**Andrea Braghin**, Italy

Mentors: **Sean Morrison & Ali Haydar**

Period: June–October 2025

Repo (reports & plan): [GSoC2025-project-log](https://github.com/BraghinAndrea/GSoC2025-project-log/tree/main) 

## Abstract
This project is intended to improve the interoperability between LS‑DYNA and BRL‑CAD by enhancing the existing k‑g converter. 
The primary goal is to facilitate a seamless data exchange between LS‑DYNA keyword files and BRL‑CAD geometry databases, ultimately streamlining workflows for users who need to transition between advanced simulation and detailed geometric modeling.


## Scope

Extended the BRL-CAD k-g LS-DYNA keyword converter with new elements, sturdier parsing, and transformation support.

Drove multiple PRs from prototype → review → merge, with iterative fixes from mentors feedbacks.

## Key Deliverables

### Seatbelt
Implemented *ELEMENT_SEATBELT + *SECTION_SEATBELT.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/9c0f0de9-0cdc-4adf-b1ec-858d1d1e56c7" /> 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/03b9e88b-a752-40fd-9747-85c2c96636f5" />

Support for both 1D and 2D (shell-based) seatbelts.

Wrote geometry to BRL-CAD using LS-PrePost coordinates; integrated seatbelt loop into the main converter loop.

### Discrete Spheres
Implemented *ELEMENT_DISCRETE_SPHERE parsing and conversion.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/687b6c7c-ed0a-476a-b8f1-bcedd0510781" /> 
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7e8b3beb-8433-4ebd-873d-2d3f21abf7b9" />



### Section Parsing improvements

SECTION_SHELL: Built a robust, card-counting approach that tolerates titles, option order, and multiple sections under a single keyword.

Supported options: EFG, THERMAL, XFEM, MISC.

SECTION_SOLID: Improved resilience to optional-card formats.

Resolved multiple “Unexpected … length” errors; added NumberOfCards tracking.

### Include/Transformations

Implemented *INCLUDE_TRANSFORM with *DEFINE_TRANSFORMATION.
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e73a3f3e-0204-4af8-a562-fb0db2270622" />
<img width="500" height="500" alt="transformation" src="https://github.com/user-attachments/assets/120134c6-ece8-49fe-821d-f61662277a44" />


Validated on Toyota Yaris keyword sets; both *INCLUDE and *INCLUDE_TRANSFORM paths convert.



## Milestones (high-level)

Jun 2–7: Seatbelt prototype; initial tests; geometry output started.

Jun 30–Jul Seatbelt integrated into main loop; PR opened.

Jul 7–12: Fixed shell seatbelt bugs; Discrete Sphere parsing & PR added.

Aug 18–29: DSphere PR updated; major push on “Unexpected length” errors; created comprehensive test cases.

Sep 16–24: Big upgrade to SECTION_SHELL (EFG/THERMAL/XFEM/MISC, titles, option order independence).

Oct 10–20: Implemented INCLUDE_TRANSFORM + DEFINE_TRANSFORMATION; followed up on SECTION_SOLID robustness.





Keep iterating on the INCLUDE_TRANSFORM PR per mentor feedback (edge transforms, formatting guards).


## Acknowledgements

Huge thanks to BRL-CAD and my mentors Sean and Ali for reviews, design discussions, and guidance.

BRL-CAD — [GitHub repo](https://github.com/BRL-CAD/brlcad)

