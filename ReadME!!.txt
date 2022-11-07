

--------------------- Setting up Visual Studio for Computer Graphics (glut, glu, glew, glfw, gl) ---------------------------------


-- Last Updated: 1st October 2022 --------------------------------------------------------------------
-- The version of all the included files were those available by 1st October 2022 --------------------

Pre-Reqs:
	1) Visual Studio + "Desktop Application in C++" mode/package (can be done while downloading visual studio or by modifying and adding this option from the visual studio installer).
	2) Dependancies Folder (included in this config file)
	3) MingW. (can be done through msys)
	

1) Build a Solution in Visual Studio ( at the time of installation i had vc 2022 community edition ) by adding an empty c++ project,
name it however you like, i named it "Computer Graphics" and let's assume you did too.

2) Now "Right Click" on your soluton in the explorer tab of visual studio and then click on the option "Open Folder in File Explorer"
	
	-> You should be in a folder "Computer Graphics" with the same name parent folder "Computer Graphics"
	-> Click on the Parent Folder "Computer Graphics"

3) Copy the "Dependancies" folder from this config folder to the parent folder "Computer Graphics"

4) Go back to visual studio and right click on your solution in the explorer tab, this time clicking on "Properties"

---------> following steps, 5 to 9 are are local to this properties window.

5) Now in "Configuration Properties>General>C++LanguageStandared" choose the latest option you have.

6) In "Congifuration Properties>VC++ Directories>General>Include Directories" copy and paste the following line without the apostrophies

"$(SolutionDir)Dependancies\freeglut\include;$(SolutionDir)Dependancies\glfw-3.3.8.bin.WIN64\include;$(SolutionDir)Dependancies\glew-2.1.0\include;$(IncludePath)"

-> click on Apply.

7) In "Congifuration Properties>VC++ Directories>General>Library Directories", copy and paste the following line without the apostrophies

"$(SolutionDir)Dependancies\freeglut\lib\$(Platform);$(SolutionDir)Dependancies\glfw-3.3.8.bin.WIN64\lib-vc2022\$(Platform);$(SolutionDir)Dependancies\glew-2.1.0\lib\Release\$(Platform);$(LibraryPath)"

-> click on Apply.

8) In "Linker>Input>Additional Dependancies" , copy and paste the following line without the apostrophies

"freeglut.lib;glfw3.lib;Opengl32.lib;opengl32.lib;User32.lib;Gdi32.lib;Shell32.lib;glew32.lib;glew32s.lib;glu32.lib"

-> click on Apply

9) In "Build Events>Post-Build Events>Command Line", copy and paste the following without the brackets

{ copy "$(SolutionDir)Dependancies\freeglut\bin\$(Platform)\freeglut.dll" "$(OutDir)"
copy "$(SolutionDir)Dependancies\glfw-3.3.8.bin.WIN64\bin\$(Platform)\glfw3.dll" "$(OutDir)"
copy "$(SolutionDir)Dependancies\glew-2.1.0\bin\Release\$(Platform)\glew32.dll" "$(OutDir)"   }

-> click on Apply

Do the following steps for testing the test codes provided in this config file

10) Add folder in your solution, named "src" or "source" (or whatever you like) from within visual studio.
11) Add a cpp file into this folder and name it whatever your heart desires.
12) Copy and paste any one of the test code provided in this config file into the cpp file.
13) Click on Build tab and click on "Rebuild Solution".
14) Check to see for no errors.
15) If no errors, then in Build Tab click on "Rebuild Computer Graphics" else go to step 17.
16) If no errors, then you can now run to see your program work fine else go to step 17.

Repeat step 10 to 16 for all the test codes

Ngl, this should work without errors and if not, sorry for your luck, it worked for me. I hope you find a solution.

17) In case of an error of such types do the following

	Type 1: "Could not open x.lib file" x being the name of any lib file"
	Remove the name of that lib file from "Linker>Input>Additional Dependancies"

For any others error , first search in on google and then if google betrays you then don't try contacting me.