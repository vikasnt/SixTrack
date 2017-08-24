###Project Description-
My GSoC organization was CERN SFT and the project I chose was Sixtrack.
Sixtrack is a software package written in Fortran to compute the trajectory of elementary particles in 6-D phase space as they pass through circular accelerators (like LHC) and achieve high energies in a controlled manner via combination of Electric and Magnetic fields. Currently, the two most pressing issues in Sixtrack which require developments are:
 1) As the energy range and intensity at which future accelerator will work is reaching unprecedented values, Sixtrack also needs to consider effects of some elements involved which were either negligible or were using simple approximation earlier.
 2) Updating the code to lift limits related to what Sixtrack can currently do.

### Project Goals
After discussion with mentors in the Community Bonding Period, We decided on the following goals for the GSoC timeline-

1. Makefile - Issue tracker - https://github.com/SixTrack/SixTrack/issues/37. Sixtrack originally used a script to build executable from source code which still works fine. A makefile was also created but due to a few bugs, the makefile was not working as it should.The new build system will replace the old and arcane dependency resolution system (the script) with something more general and maintainable. This makes it easier to support multiple platforms, and also to incorporate external libraries in a clean way. We agreed that cleaning makefile, as well as getting it working for multiple platforms should be done first. After debugging the code, we finally managed to get it working correctly. Also, we added support for 64-bit executable while earlier only 32-bit executable was possible (which was also one of the limitations of Sixtrack).
Pull request - https://github.com/SixTrack/SixTrack/pull/73 , https://github.com/SixTrack/SixTrack/pull/76 and also https://github.com/SixTrack/SixTrack/commit/03e69ac75bd52e9f7123f1aca7cda8d542078169

2. File system- Issue tracker - https://github.com/SixTrack/SixTrack/issues/77. The Output from Sixtrack is used in a few other packages, and adhering to a standard output format is necessary, which is also explained in Sixtrack Manual. Sixtrack output is saved in binary files(to save size) and currently the code only writes maximum 32 files,each storing data from 2 particles at max. Again, as the physical limit of particle accelerators is pushing its limits to explore previously unimaginable flux and energy ranges, Sixtrack also needs to work with more particles in order to remain as useful to the scientific community in future as it is today. Since the old format is at its limit, after discussion we decided to add another feature to Sixtrack where we will work with a single binary file which can store as many particle data as needed. This is only half part of the puzzle (and the easier half if I have to guess) since upgrading a lot of variables etc is also required to accommodate the new particle limit which will mean updating a large portion of a very big code base and possibly lots of debugging.
Also, effort is required to validate the new system which means writing a few tests script as well as editing older ones to accommodate the changes. This goal is also complete in terms of the working code, although some more testing is required before merging with master branch can be done.
Pull Request - https://github.com/SixTrack/SixTrack/pull/82

3. Solenoid implementation - Issue - https://github.com/SixTrack/SixTrack/issues/4. Sixtrack already has the thin lens approximation for Solenoid element but a possible bug was found in it. We decided to finish this assuming it was a simple bug and shouldn't take much time but after carefully examining the code and Physics involved, some complications were found. After some brainstorming, we are pretty close to debugging the code. Some irregularities in the Sixtrack manual vs Physics of Solenoid in accelerator vs code implementation have been found, and only a few things are left to be cleared up(possibly in a week worth of time). 

4. RF implementation - Issue - https://github.com/SixTrack/SixTrack/issues/5. This was the last goal which we were supposed to finish, but due to 3rd problem blowing up in the time taken, as well as some extra time wasted in completing older stuff, I only arrived at this around the last 10 days of GSoC. We have decided to pick it up after finishing the 3rd goal and I intend to work on this after GSoC deadline ends.


### Authors and Contributors
GSoC participant - Vikas Gupta <@vikasnt> 

Mentors - Kyrre Ness Sjøbæk <@kyrsjo> and Riccardo De Maria <@rdemaria>

I would like to thank Google as well as CERN SFT and my mentors for this wonderful opportunity.

Finally, I would like to thank Kyrre Ness Sjøbæk @kyrsjo for guiding as well as helping out so many times while working on Sixtrack.

