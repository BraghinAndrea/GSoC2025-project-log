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
  
### Issues:
