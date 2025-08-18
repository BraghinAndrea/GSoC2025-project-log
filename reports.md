## Daily reports and project update

# Day One: June 2nd - May the coding begin! 💪
 ### Achievements:

 - Literature review - [LS-DYNA Keyword manual](https://ftp.lstc.com/anonymous/outgoing/web/ls-dyna_manuals/R15/LS-DYNA_Manual_Volume_I_R15.pdf) - selection of geometry-related features to be implemented.
 - *Element_Discrete_Sphere implementation in k_parser.h and k_parser.cpp, to be tested.
 - *Element_Seatbelt implementation testing on [THUMS model](https://www.toyota.co.jp/thums/).
  
### Issues:
  *Element_Seatbelt can be use for different purposes, it can represent a muscle ligament for example. Its geometrical properties can still be tuned and drawn with no additional requirement. For something like *Element_Seatbelt_Slipring, however, further analysis has to be carried on about its possible multipurpose applications between 2 Element_Seatbelts because its geometry may depend on the application.
  
# June 3rd:
### Achievements:
Further testing on *Element_Seatbelt on various keyword files. 
By creating a 3-point seatbelt in LS-PrePost significant findings arised: the software allows the user to chose two different ways for creating a seatbelt part. A simpler "string", let's say 1D, version an a so-called "mixed" 2D version with a higher number of customizable features and dimensions.
A single seatbelt part contains multiple arbs, each is linked to specific nodes so the overall shape of the part is easily obtainable. 

<img width="500" alt="1Dseatbeelt" src="https://github.com/user-attachments/assets/12081b49-de0d-4b04-91d2-63ed6bf857d2" /> <img width="500" alt="2Dseatbelt" src="https://github.com/user-attachments/assets/5148ae54-e90a-4cf5-95c5-46a5fb9f7c7e" />

1D seatbelt conversion is partially successfull and drawn in mged, substantial code refinments are still needed:

<img width="500" alt="1Dbeltmged" src="https://github.com/user-attachments/assets/ea93ce25-6792-49c2-9115-702c2b099103" />

### Issues:
Above-mentioned muscle ligaments appear to be 1D seatbelt parts with null thickness, it is necessary to discern the two during conversion. Code still needs substantial editing and revision. 

#### References
LS-DYNA dummy model inspired by [YT Video](https://www.youtube.com/watch?v=yte6Do91E7A&ab_channel=SankarRaj).

# June 4th:
### Achievements:
Improvements in k-g.cpp . Seatbelt geometry gets now written in BRL-CAD database following LS-PrePost coordinate system. Nodes coordinates are used as reference points for arbs elements.

<img width="500" alt="1Dbeltmged" src="https://github.com/user-attachments/assets/a6988daf-f15e-4357-98ef-6a784a1e703c" />

### Issues:
Dimensions of the seatbelt might need to be adjusted by tuning the scalar factor. In some cases it might be necessary to use shell elements following [LS-DYNA Keyword manual](https://ftp.lstc.com/anonymous/outgoing/web/ls-dyna_manuals/R15/LS-DYNA_Manual_Volume_I_R15.pdf) .

# June 5th:
### Achievements:
Worked on k-g.cpp, kparser.cpp and kparser.h for *Element_Seatbelt and *Section_Seatbelt.
### Issues:
Seatbelt loop is currently outside the main converter loop. Better access to Kdata is needed, a common iterator has to be found.

# June 6th:
### Achievements:
Finalizing first implementation for *Element_Seatbelt and *Section_Seatbelt. Opened a [Pull request](https://github.com/BRL-CAD/brlcad/pull/189#issue-3124559994)
### Issues:
Code might benefit from further improvements upon potential mentors' feedbacks.

# June 7th:
### Achievements:
Working on mentors' advice after the previous PR
### Issues:
PR handling and presentation need to be refined

# June 8th:
### Achievements:
Discrete sphere literature review and study. Created a LS-PrePost test model.
<img width="500" alt="Sph" src="https://github.com/user-attachments/assets/9ee3d37d-640d-40a7-81f8-dafb382ebdbb" />
### Issues:

# June 9th:
### Achievements:
Working on mentors' advice after the previous PR. Code cleaning
### Issues:

# June 10th
### Achievements:
Improved [Pull Request](https://github.com/BRL-CAD/brlcad/pull/190)'s quality following mentors suggestions.

### Issues:
Struggled with Element_seatbelt implementation in k-g.cpp main loop. Feedbacks might be needed.

# June 11th
### Achievements:
Worked on implementating Discrete_Sphere

### Issues:
Choosing the appropriate coordinate system for the spheres

# June 12th
### Achievements:
Worked on Seatbelt PR upon mentor's suggestions merging Seatbelt in k-g.cpp main loop.

# June 13th
### Achievements:
Worked on Discrete_Sphere implementation

# June 14th - June 29th
Break period

# June 30th
### Achievements:
Successfully merged the Seatbelt for loop inside the main loop in k-g.file
Preparing PR

# July 1st
### Achievements:
Created [pull request](https://github.com/BRL-CAD/brlcad/pull/193) for seatbelt implementation after successfully integrate it in the main loop. Test on keyworkd file was successful.

# July 2nd
### Achievements:
Worked on perfecting PR upon mentor suggeggestions

# July 3nd
### Achievements:
Worked on perfecting PR upon mentor suggeggestions addressing redoundacies and some logic.

# July 4th
### Issues:
Unable to convert element_seatbelt when composed by shell elements. Debugging

# July 5th
### Issues:
Unable to convert element_seatbelt when composed by shell elements. Debugging

# July 6th
### Issues:
Unable to convert element_seatbelt when composed by shell elements. Debugging

# July 7th
### Achievements:
Found bug in k_parser.cpp preventing the conversion of shell elements.

Successfully converted dummy keyword file containing both types of element_seatbelt.

<img width="500" alt="07July" src="https://github.com/user-attachments/assets/a313ff10-6a4c-4396-b0c5-78806db93559" />

# July 8th
### Achievements:
Refinement of seatbelt implementation after mentors' feedback. Opened new PR at the [following link](https://github.com/BRL-CAD/brlcad/pull/194)
k-g converter can now handle different types of seatbelt features from keyword files both with different element_seatbelt and element_shell.

# July 9th
### Achievements:
Formatting and spacing editing in [PR-194](https://github.com/BRL-CAD/brlcad/pull/194).

Worked on Element_Discrete_Sphere too.

# July 10th
### Achievements:
Progress toward Discrete_Sphere implementation, parsersing is working
### Issues:
Further testing is needed. Could not locate any funtion for drawing SPH, Geometry-wise. 

# July 11th
### Achievements:
Successfully converted Element_Discrete_Sphere from keyword file.

<img width="500" alt="07July" src="https://github.com/user-attachments/assets/7bbec6c0-054e-47bf-9ebf-e7fa4fbb5a2b" />
<img width="500" alt="07July" src="https://github.com/user-attachments/assets/9639db9a-8d84-46f2-9375-f7a90fd77a5b" />

### Issues:
Code cleanup and geometry.cpp implementation are needed.

# July 12th
### Schievement:
Improved the code for the element_discrete_sphere in k-g converter. First implementation is available at [PR195](https://github.com/BRL-CAD/brlcad/pull/195)

### Issues:
The newly created pr has to follow the merging of the previous Seatblet PR in case of acceptance. The code will then need to be updated, in particular k-g.cpp, k_parser.cpp and k_parser.h

# July 13th
Further testing on Discrete Sphere implementation. Literature review

# July 14th - August 17th
Break Period as scheduled

# August 18th
Updated [PR195](https://github.com/BRL-CAD/brlcad/pull/195) following mentor's suggestions.

