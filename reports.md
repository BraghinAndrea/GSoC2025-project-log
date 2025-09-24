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

# August 19th
Creating new PR after PR194 with ElementSeatbelt was merged containing ElementDiscreteSphere too. Tested on keywords containing Seatbelt and DSph separately. Further testing is needed.
# August 20 
Working on the open PR, I have problems building the code. some link error. most likely related to missing changes I didn't push.
I'm also exploring what to do next, 1- exploring the idea to standarize the element recognition in k-g.cpp because the use of node number looks like it will creat some conflicts. 2- a thing to do on the side is to fix all the errors that appears when converting the Yaris model. 
# August 21
Fixed the errors related to the *Part_Contact command, the option Contact increases number of cards but it doesn't seem to affect the geometry.
Fixed the errors related to (Too short SECTION_BEAM in k-file) by limiting the size to only the attributes handeled in the code. also working on the error Unexpected SECTION length in k-file for the Section_Shell in the Yaris model. it seems that multiple sections are defined under one *section_shell keyword. 
still having problems with building the open PR.
# August 22
Working on Unexpected SECTION length in k-file. I'm unsure how to handle the error, because the section lines read variable handles only 3 cases 0 1 2, but when there are multiple sections defined under the same keyword the section lines read can take much larger values. additionally the number of cards for each section depends on the options of the keyword Section_shell. on the side I'm still planning the standarization of element recongintion. 
# August 23
Working on Unexpected SECTION length in k-file. I'm exploring the idea of adding a variable that holds the number of cards included in each section_shell. becuase other wise there is no way to know that we finished reading the first section_shell.
# August 24 
Working on Unexpected SECTION length in k-file. adding the new variable seems to solve the problem but it's quite complicated to specify it's value, considering that different options creat different number of cards and different elemForm also changes the number of cards. for the current model adding the variable numberOfCardsInSection is solving the problem for section shell. facing the same problem for section_solid. I have to find a general solution for such problem.
# August 25
Risolved Unexpected SECTION length in k-file for section_shell and section_solid. Working on Unexpected Part length. I implemented a simple solution for unexpected Part length I think it will need more work. I will fix one more error and submit changes for feed back from mentors.
# August 26 
Working on the error unexpected command section_discrete. still trying to figure out how to standarize the element recognition. 
# August 27 
submitted the PR and wating for mentor review. Reading documentation for understanding what to do next and make sure what I did is correct.
# August 28 
Solved the building error for the descreet sphere PR. and resarching the documentaion to improve the Unexpected length Error implimentation.  
# August 29 
opend PR for discreet sphere and working on Unexpected Section length error, trying to creat test cases to understand how to implement the code <img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/9d2f4186-e62b-488d-be41-e5dc848ee2ac" />
it seems that the Title option comes at the end, I will try to create files with multiple options and see if LS-DYNA opens them if I change the order of options. 
I did some tests For LS-PrePost , the commands SECTION_SHELL_EFG_TITLE and SECTION_SHELL_TITLE_EFG are the same, but when saving the key word file again LS-PrePost uses this format SECTION_SHELL_EFG_TITL.
It will take a while to creat all possible cases for testing working on it 
# August 30
I have created testing files. for several cases but facing problems converting them. Getting some assersion error I don't know what is the problem. 
Found the error it's realted to the modifications I did in the privous PR, fixing and will continue to test 
# August 31
Spent some more time testing for further investigation that I believe are needed
# September 1st
Addressing mentor suggestions following the merging of the previous PR for Discret sphere. Multiple unnamed could be an issue, a clever way of assigning a value different for blank is needed.
Did further documentation research about different SECTION_SHELL_"type"
# September 2nd
Continued SECTION_SHELL_"" implementation.
Correction in sphere.h with small PR [here](https://github.com/BRL-CAD/brlcad/pull/199)
# September 3rd
Worked on different Section Shell integration and card number variables handling in the parser.
Needs different test files, multiple variable are in need of testing for different use case scenarios.
# September 4th
Focused on refining the parser logic for Section Shell handling. Encountered some difficulties aligning card numbering with different use cases, so additional adjustments will be needed.
# September 5th
Attempted to run tests on the recent parser changes. Some inconsistencies appeared in variable assignments that still need careful checking. Planning to revisit the test files and adjust the implementation to resolve the issues.
# September 6th
Further testing and development for card counting approach in k_parser.cpp. Waiting for mentor feedback, confirming the soundness of the proposed approach when for example under just one section_shell multiple cards appear. 
# September 7th
Focused on testing `k_parser.cpp` with different options under `*SECTION_SHELL`. Verified behavior when multiple cards and variations appear, ensuring the parser correctly distinguishes and assigns values. Some cases still require refinement, particularly in handling optional versus mandatory fields with different options.
# September 8th
Literature review on CARD1[ELFORM] for *SECTION_SHELL, when ELFORM = 101,102,103,104 or 105 additional cards are generated and need to be handled by parser.cpp. Created keyword files for different sections on toroidal example shape.
<img width="500" height="500" alt="Toroid" src="https://github.com/user-attachments/assets/e146bbf0-0b61-45b7-a241-7008a7e13220" />
# September 9th
Facing difficulties in handling the parsing when ELFORM = 101,102,103,104 or 105 and ICOMP = 1, encountering the Unexpected Section length error. Trying to figure a solution out.
# September 10th
Tried introducing boolean operators for keeping track of ELFORM and ICOMP values. Having some problem organizing the parsing of variable number of cards in *SECTION_SHELL
# September 11th
Further development, debugging and testing with boolean operators. The logic turned out to be not as reliable as I hoped for. It seems redundand, I will try another way, ideally independent from the number of cards for the same section.
# September 12th
Working on number of card-independent parsing approach for shell sections
# September 13th
Similiar issues as before were encountered when the value of Elforms doesn't get stored so the unexpected section length error still occurs. meaning the independency from card number wasn't achieved.
# September 14th
Revert to boolean operators-based section_shell parsing in k_parser.cpp
# September 15th
Further testing. Updated the [pull request](https://github.com/BraghinAndrea/brlcad/commit/26b8cc5bdabcb8bc6b2471f1bbc15bd6dfbe90ce) seeking mentors' feedback
# September 16th
Worked k_parser.cpp implementing *SECTION_SHELL option "EFG" following mentor's advice. Updated the above-mentioned PR. It now reads title correctly and adjusts the number of cards for EFG option
# September 17th
Worked on updating k_parse.cpp to discard non-geometry cards using the default case for cleaner parsing as suggested. Needs testing
# September 18th
Updated k_parser.cpp. Included THERMAL, XFEM and MISC options. Changed the default logic in switch statement. Updated the [pull request](https://github.com/BraghinAndrea/brlcad/commit/f00e69b34d862a33c925656da99dd6c4ff3582f2).
# September 19th
Testing with different keyword files, multiple SECTION_SHELL with and without titles or options. Some issues arise whit multiple sections in a file, each one with a title. 
# September 20th
Changed NumberOfCardInSection to NumberOfCards for better readability and meaning. Still some issues related to right number of card for each configurations, kept testing and debugging. 
# September 22nd
Worked towards parsing section title and options indepently from order. Still struggling with combination of different section_shell_option with and without title
# September 23rd 
Could parse the combined keyword for Thermal and Xfem option with titles but when two sections of the same kind are one after the other in the .k file, the second doesn't get recognised. Debugging and testing continues. 
# September 24th
Arrived to a version that appears to be more reliable. Kept testing and updated the [PR](https://github.com/BraghinAndrea/brlcad/commit/a0012380ee2ee42585b9e900a892ef76e91de551)
