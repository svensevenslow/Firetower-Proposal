# Firetower-Proposal


**TEAM LOCATION:** Chandigarh, India

**TIME ZONE:** GMT+5:30 (Indian Standard Time)



**PERSONAL DETAILS OF TEAM MEMBERS**


**Name :** Kainaat Singh

**GitHub:** [svensevenslow](https://github.com/svensevenslow)

**Name:** Muskan Sharma

**Github :** [muskan98](https://github.com/muskan98)


**PERSONAL DETAILS OF COACHES**


**Name:** Anhad Jai Singh

**Github :**[ffledgling](https://github.com/ffledgling)

**Name:** Akshay Arora

**Github:** [akshayarora2009](https://github.com/akshayarora2009)


**ABSTRACT**

Firetower is a tool which makes development easier by allowing the developer to run and re-run  any command from the terminal. Firetower reflects changes in the running program immediately after code is saved in the editor. The purpose of this project is to make Firetower more robust, increase compatibility and improve the overall user experience.


**OBJECTIVES**

Provide editor hooks in various other editors such as sublime, atom and gedit to facilitate the use of Firetower.
Allow multiple instances of Firetower per working directory.
Test cross-terminal compatibility for Firetower with popular terminal emulators such as xterm, gnome-terminal, guake, iTerm, Windows Shell.
Make parameter parsing more robust by fixing argument parsing and providing short hand flags for long-form optional arguments.


**PROJECT PROPOSAL**

As we have seen, Firetower is a tool that makes developers more efficient by eliminating repetitive work.

The first order of  business would be to make Firetower available to a wider audience and to achieve this goal it is necessary that Firetower is compatible with a wider set of editors. The choice of editors is fluid but we can draw inspiration from the stackoverflow developer survey of 2015[1] and pick popular ones such as Sublime Text, Atom.io etc. (Github Issue [#3](https://github.com/mweitzel/firetower/issues/3), [#4](https://github.com/mweitzel/firetower/issues/4)).
As part of preliminary research, we’ve found that sublime does not provide native save hooks, but this functionality is available via a [sublime-hooks plugin](https://github.com/twolfson/sublime-hooks)  which gives event level bindings to other sublime plugins. This can be used to run firetower -r command when a file is saved.

Often developer workflows are more complex than running a single command repeatedly. Adding the ability to run multiple instances of Firetower per working directory (Github Issue [#5](https://github.com/mweitzel/firetower/issues/5)) allows developers with more complex workflows to utilize Firetower and become more efficient.  

Based on our preliminary study of the code as well the suggestions in the relevant Github issue, this  does not currently work because the Firetower file is not unique to each instance of Firetower. This means multiple instances of firetower in the same working directory tend to step on each others’ toes. Possible solutions to this problem are to either allow the programmer to set a unique name at the time of first run or assigning a unique name by default, possibly using something like a PID. When attempting to restart all instances of firetower for a directory, we’d likely iterate through all .*.firetower files and do whatever is necessary for each of them.

After improving both compatibility and flexibility, we’d like to improve the overall user experience for users when they use Firetower. There are two parts to this.

The first, standardizing the command line by bringing it more in-line with how other UNIX tools behave, thereby making Firetower’s command parsing more robust.
Presently firetower does not work properly when it receives incompatible multiple arguments, for example running a command like firetower -h -c makes Firetower print the help but does not make it run the command. No error is printed to indicate that these sets of arguments are mutually exclusive. Going through the code, we gather that this error occurs because we are exclusively referring to “$1”, the first argument, to parse short-form flags (-c -h -r -s)  and do not take into consideration any other arguments in the code. We should modify the code in such a way that this does not happen. Some arguments like -r and -s are not meant to  work together and there should be some conditions/checks added in the code to handle such cases and the program should exit while generating an error or printing the help message.

Another problem with the command line parsing in Firetower is that it expects the arguments to the program to be in a very specific order that is at times counter intuitive to regular UNIX tool users. (Github Issue [#6](https://github.com/mweitzel/firetower/issues/6)) For example:

firetower -c “echo foo bar” --directory=/tmp  # Works
firetower --directory=/tmp -c “echo foo bar”  # This does not

From a logical stand-point there should be no difference between the two. Looking at the code, this seems to be caused by the same “$1” issue.

Lastly, it would be nice to have short-forms of some existing long-form command line arguments. (Github Issue [#7](https://github.com/mweitzel/firetower/issues/7)) Such as:

 -p for --preserve-scrollback 
 -d dir_name for --directory=dir_name

The other side of improved user experience is better cross-terminal compatibility. As part of the project, we’ll attempt to check terminal compatibility of Firetower with commonly used terminals such as xterm, gnome-terminal, guake, iTerm, Windows Shell based on time constraints.


**TIMELINE**

We have arranged the work in successive weeks in increasing order of difficulty so that we can slowly ease into the more complex work while giving us a chance to familiarize ourselves with the codebase. This should help maintain efficiency and productivity.


**SCHEDULE**

|Week Number(s)|Work Allotted|
|---|---|
|1,2|Explore Sublime, Atom’s plugin frameworks. Figure out a way to leverage them to run with Firetower by either writing a plugin, extending the user configuration files or using existing plugins.|
|3,4|Allow multiple instances of Firetower per working directory resolve issues such as restarting all process or just certain ones by referring to them .|
|5|First catch up and review period.Use this time to get feedback about methodology and approach.Use this time to recalibrate expectations, redefine goals and restructure timeline incase we fall behind due to unforeseen circumstances.|
|6,7|Check Firetower compatibility with different terminals.|
|8,9,10|Make argument parsing more robust. Taking care of cases with conflicting arguments.Allowing anyorder of arguments to be accepted.Add short-form flags for optional arguments|
|11 |Second catch up and review period.|
|12|Resolve  any remaining issues. Get final approval of mentor and completion of documentation.|



Delays and glitches are inevitable. Two catch up weeks have been scheduled.One near the half way mark to  restructure our approach if required and complete any pending work.The second catch up period is scheduled to ensure everything is working efficiently and project is completed as scheduled.


**PRIOR EXPERIENCE**

**Kainaat Singh**

I am currently a first year student in college.I have been programming in C for the past 6 months. Linux is my primary operating system for the same duration and I use vim as my text editor. I am interested in learning about UNIX-like systems and have actively started learning bash. I am also familiar with HTML and CSS and occasionally use gedit for my editing needs.

**Online presence:**

**Codechef:** [svensevenslow](https://www.codechef.com/users/svensevenslow)

**CodeForces:** [svensevenslow](http://codeforces.com/profile/svensevenslow)

**Hackerearth:**[kainaat.singh](https://www.hackerearth.com/@kainaat.singh)

**Hackerrank:**[kainaat_singh](https://www.hackerrank.com/kainaat_singh)

**Muskan Sharma**

I have some experience with C. I also dabble  in Java, HTML, CSS and Javascript occasionally. I work primarily on Linux and I’ve been using Sublime as my text editor for the past few months. I am interested in learning more about UNIX-like systems.

**Online presence:**

**Codechef:** [a1girl0shell](https://www.codechef.com/users/a1girl0shell)

**Hackerearth:** [muskan98](https://www.hackerearth.com/@muskan98)

**Hackerrank:**[muskanbck](https://www.hackerrank.com/muskanbck)

**ACADEMICS**

We are currently in the first year  of college and are both pursuing a Bachelor’s degree in Computer and Engineering at PEC University of Technology, Chandigarh, India. 


**PRIOR COMMITMENTS**

We have no prior commitments for the duration of the program. During this period we have our summer break in college.


**WORK SPACE**

We both have a workspace available in our college and have regular interaction as we are classmates. Akshay Arora is a senior in our college and will be able to help us in-person on a daily basis. Anhad Jai Singh is a software engineer in Gurgaon (India) and remains constantly available via hangouts for day to day input and via occasional visits to the city.


**COMMUNITY LEARNING**

We are both part of the Computer Science society in our college. Workshops are held regularly to discuss programming concepts. We are encouraged to take part in programming contests as well as in development work. Our peer group helps in creating the environment required for competitive programming and open source work. We participate in programming contests that are held locally in our college.


**WHY US?**

We are  first year students eager to learn new things and would really like to gain practical knowledge and experience outside the scope of our curriculum by working on a real world project. We find ourselves fascinated by Linux and would thus like to improve our understanding of its  fundamentals. We’ve have been using Ubuntu for the past 6 months and have recently taken to learning bash and forcing ourselves to use vim. This project seems to be the perfect opportunity for us to learn and grow.


**WHY RAIL GIRLS SUMMER OF CODE ?**

The work and projects are very interesting. Community learning has contributed in a big way to the development of our programming skills and understanding of computer languages. We want to start giving back to the Free and Open Source community that has given us so much both in terms of software, experience and guidance. Thus we would love to take part in this summer of code.


**REFERENCES**

[1] http://stackoverflow.com/research/developer-survey-2015

[2] https://github.com/twolfson/sublime-hooks
