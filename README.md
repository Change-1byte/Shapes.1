# Shapes.1
the input and calculation "engine" for a drafting program
This is the first in a series of seven assignments (Assignments 1-4, 9 two parts, 11) that will end with an object-oriented, GUI-based Windows program by the end of the semester. It begins as a console program, using coding techniques you've learned in prerequisite courses -- no object-oriented design (yet). Then as we learn new features of object-oriented programming, we'll refine and develop this original version until it takes full advantage of all that we'll learn in this course.

For most of the series we'll be writing console programs. Once we learn enough about object-oriented syntax and design, we'll be ready to move to a GUI (graphical user interface) version of the program. Unfortunately there is not a common library for GUI programming in the standard C++ library. Instead there are add-ons included with some IDEs or supplied by 3rd parties for expanding your C++ installation to do GUI. A real nice option is "Qt" because it's free and works cross-platform. But there are licensing issues that make it not a desirable choice for a course like this.

So since the DVC computer labs are equipped with Windows 10 workstations with Microsoft Visual Studio, that's what we'll be using for the programming assignments that involve GUI -- Assignments 10 to 12. Prepare to either install a version of Visual Studio (2015 or later) on your Windows PC (Win7 or later), or if that's not going to be possible (or if you only have a Mac), be prepared to spend some time in our computer lab in those weeks.

The Shapes Program
This program is the input and calculation "engine" for a drafting program we're writing (like SketchUp or AutoCad). While we'll never actually get there by the end of this course, it's the direction we're going and gives focus to our development efforts.

Here is the specification for the Shapes program at this early stage of development.
REQUIREMENTS: Write a C++ program named Shapes.1.cpp to calculate area, perimeter, surface area, and volume of common 2D and 3D shapes. The calculations for 8 shapes include: (reference: Geometric Formulae Review (Links to an external site.) (http://www.purplemath.com/modules/geoform.htm))

area and perimeter of a 2D square
area and perimeter of a 2D rectangle
area and perimeter of a 2D circle
area and perimeter of an 2D equilateral triangle
surface area and volume of a 3D cube (a 2D square with a 3rd dimension)
surface area and volume of a box (a 2D rectangle with a 3rd dimension)
surface area and volume of a cylinder (a 2D circle with a 3rd dimension)
surface area and volume of a prism (a 2D equilateral triangle with a 3rd dimension)
NOTE: The "perimeter" of a circle is more commonly referred to as "circumference", but we're calling it perimeter.

INPUT: The program input shall be from a text file named Shapes.input.txt, to be located in the same folder as the executable. The file shall consist of an unspecified number of lines. Each line of the file will specify one shape object, or be blank. The line format consists of (1) an object type in uppercase (SQUARE, RECTANGLE, CIRCLE, TRIANGLE, CUBE, BOX, CYLINDER, or PRISM), and (2) the dimensions of the object as follows: (**How to parse one line string into multiple string tokens? You may share your idea in the discussion, C++ Programming Basics, Q&A. One hint, we may parse the line string into a string vector using parseString() function from the reading page, Text Parsing, Reading.)

for square, 1 dimension: "side"
for rectangle, 2 dimensions: "length" and "width"
for circle, 1 dimension: "radius"
for triangle, 1 dimension: "side"
for cube, 1 dimension: "side"
for box, 3 dimensions: "length", "width", and "height" for cylinder, 2 dimensions: "radius" and "height"
for prism, 2 dimensions: "side" and "height"

INPUT FILE FORMAT: A line of input may consist of up to 4 (four) usable "tokens", each separated by one or more spaces or tab characters.

Ignore any tokens past the fourth token, if they exist. The first token is the object name (for example, "SQUARE"). The second through fourth tokens are dimensions. Some calculations need only one dimension (CIRCLE, SQUARE, CUBE, and TRIANGLE); others need two (RECTANGLE, CYLINDER, and PRISM) or three (BOX). There may be blank lines, which are to be ignored.

HINT: If the number of tokens found in a parsed input line is (for example) 2, then only token[0] and token[1] exist. token[1] is the first dimension and there is no second dimension. So if the #of tokens > n, then token[n] exists. Otherwise it does not. Using the size() member function from the vector to know the #of tokens

The last line if the file marks the end of the file with uppercase EOF.

It is possible for an invalid object to be specified, or for the wrong number of dimensions to be supplied. Here is a sample input file (which includes a blank line, and one pair of dimensions separated by more than one space):

SQUARE 14.5
SQUARE                          <-- USE ZERO FOR THE MISSING "side" DIMENSION
RECTANGLE 14.5    4.65          <-- IGNORE THE MULTI-SPACE SEPARATION BETWEEN DIMENSIONS
CIRCLE 14.5
CUBE 13
BOX 1 2 3
                                <-- IGNORE THIS BLANK -- SKIP OVER IT
SPHERE 2.4                      <-- IGNORE THIS UNKNOWN SHAPE
CYLINDER 1.23                   <-- USE ZERO FOR THE MISSING 2ND DIMENSION
CYLINDER 50 1.23
TRIANGLE 1.2 3.2                <-- IGNORE THE EXTRA 2ND DIMENSION, 3.2
EOF 

** The driver program should be able to process blank lines, missing values or invalid data. To test your program, you may use the same input text file, Shapes.input.txt Download Shapes.input.txt

** After the testing, make sure to compare your output with the sample output (Go to "Files" -> "Assignment Sample outputs" folder)

OUTPUT: Write results to two different sources -- the console screen and a TXT text file. Ref: chapter 10 of the optional, Burns textbook.

CONSOLE OUTPUT FORMAT. Output the object name, its dimensions (1, 2, or 3 of them), and calculated results on one line. If the object is not recognized as one of the 8 allowable object types, produce output to this effect: "SPHERE invalid object". If the object is recognized, but there are not enough dimensions provided, use the default value of zero (0) for each missing dimension. The results for the above input should be as follows. Note the identifications of the dimensions and the calculated values. The dimensions and calculated results may appear in any order:

SQUARE side=14.5 area=210.25 perimeter=58.00
SQUARE side=0 area=0.00 perimeter=0.00
RECTANGLE length=14.5 width=4.65 area=67.43 perimeter=38.30
CIRCLE radius=14.5 area=660.52 perimeter=91.11
CUBE side=13 surface area=1014.00 volume=2197.00
BOX length=1 width=2 height=3 surface area=22.00 volume=6.00
SPHERE invalid object
CYLINDER radius=1.23 height=0 surface area=9.51 volume=0.00
CYLINDER radius=50 height=1.23 surface area=16094.37 volume=9660.39
TRIANGLE side=1.2 area=0.62 perimeter=3.60
 

FILE OUTPUT FORMAT. Output to a TXT file named Shapes.output.txt in exactly the same format as the console output. But unlike the console output, skip invalid shapes -- only output valid shapes. 

ROUNDING: Format the calculated results to 2 digits after the decimal. Set the precision to 2. But echo the input values without formatting. Set the precision back to 6.

DO use the parsing function provided in this module.

DO figure out how to handle missing dimensions -- there's more than one way.

DO use the formatting code blocks modeled in this module.

DO open your outputted TXT file in a text editor to see if it is formatted the same as the console output.

DO include commented and cout'ed identification as modeled in Module 2.

Submit Shapes.1.cpp for grading. Do NOT submit any TXT files.
