# Documentation

# Overview:

This program allows the user to load an SVG file, view detailed counts of elements in the file, add new elements through a interactive menu, and export the updated SVG as both SVG and JSON files.

Key capabilities:

- Parse SVG file into an object model
- Display counts of all SVG elements and attributes
- Add new SVG shapes and elements through user menu.
- Dynamically update the SVG object model
- Output updated SVG as both SVG and JSON formats
- Provide a clean interface for SVG manipulation.

The core classes and files:

- `Structure`: Primary class holding parsed SVG data
    - Contains vectors of shapes, attributes, and other SVG elements
    - Central repository for all SVG information
    - Updated as new elements are added.
- `Menu`: Displays interactive menus for viewing data and adding elements
    - Provides options to user and guides workflow.
- `ConvertingFilestoVectors`: Parses input SVG file into a Structure
    - Uses XML parser to load SVG and extract elements.
    - Populates Structure with shapes, attributes, etc.
- `Creator`: Contains functions to create new SVG elements
    - Methods for each shape type to add to Structure.
    - Options for user input of attributes
- `GenerateOutputFile`: Writes Structure object to output SVG file.
    - SVG file reflects all additions and changes to Structure.
    - Key class for SVG export
- `SvgtoJson`: Converts final SVG file to JSON format.
    - Outputs machine-readable JSON version of SVG
    - Useful for web and mobile applications
- `SecondOptionSwitch`: Displays count details of selected elements.
    - Provides granular view into Structure contents.
    - Counts by element and attribute types.

# Detailed Program Flow:

1. **Get SVG filename** from user
2. **Load and parse** SVG file using `ConvertingFilestoVectors`
    - Populates `Structure` with all SVG data
3. **Display main menu** loop offering options:
    - View detailed SVG element/attribute counts
    - Add new elements through interactive menu
    - Export updated SVG and convert to JSON
4. **View counts:** Show specific element/attribute counts
    - User selects type(s) to count from menu
    - `SecondOptionSwitch` displays totals from `Structure`
5. **Add new element:** Guide user through shape creation
    - Menu options for shape type, attributes
    - `Creator` class constructs new element
    - Added to `Structure` for central management
6. **Export SVG and JSON:** Write out updated files
    - `GenerateOutputFile` writes `Structure` to SVG file
    - `SvgtoJson` converts new SVG to JSON
    - Provides updated SVG in two formats
7. **Exit** when user finishes workflow

# Key Classes and Functions:

**`Structure` Class**

- `Deque<Element> shapes`: Stores all SVG shape elements to maintain order
- `Deque<string> elements`: All shape elements
- `Deque<Other>`: Other SVG elements like `<text>`, `<image>` etc.
- Getter methods to access internal data

**`ConvertingFilestoVectors` Class**

- `convertingFilestoVectors()`: Main parsing function
    - Loads SVG with PUGIXML parser
    - Extracts elements and attributes
    - Populates Structure object
- Helper methods for parsing details

**`Creator` Class**

- `createNewXxx()`: Methods for each shape type
    - Accept user input for attributes
    - Return constructed shape element
- `createNewXxxAsSingleAttribute()`: Create shape from single string

**`GenerateOutputFile` Class**

- `createOutputFile()`: Writes Structure to SVG file
    - SVG contains all new elements added
    - Returns true if file written successfully

**`SvgtoJson` Class**

- `svgtojson()`: Converts SVG file to JSON
    - Leverages SVG parser library
    - Outputs JSON file

**`SecondOptionSwitch` Class**

- `check1()`: Displays counts of selected element/attribute types
    - Extracts data from Structure based on menu option
    - Prints totals for each selected type

**`Menu` Class**

- `displayMenu()`: Shows main menu options
- `displayCountMenu()`: Menu for count types
- `displayAddElementMenu()`: Menu for adding new elements

**`main()` Function**

- Controls overall program flow
- Initializes classes
- Calls key functions in sequence
- Manages SVG load, update, and export

# File Structure:

![Untitled](Documentation%203e14db849a464392b00df46e9b7cecda/Untitled.png)

# Output:

```cpp
PS D:\C++\SVG_Parser\Home_SVG_Parser> cd 'd:\C++\SVG_Parser\Home_SVG_Parser\output'
PS D:\C++\SVG_Parser\Home_SVG_Parser\output> & .\'main.exe'
Please Enter your file name like (../FOLDERNAME/FILENAME) :../TestFiles/test.svg
Your File has been Loaded.. 

***************************************
              SVG PARSER
***************************************
        1.Count Number of Elements: 
        2.Add new element: 
        3.Create a new SVG and JSON File 
        4.EXIT
Enter an Option to proceed further: 1
===========COUNT MENU===========
        1.Display RECTANGLE count
        2.Display CIRCLE count
        3.Display ELLIPSE count
        4.Display LINE count
        5.Display POLYLINE count
        6.Display POLYGON count
        7.Display PATH count
        8.Other tag:
        9.Display ALL count
        10.EXIT
Select an option to display the count of an element/elements:
9
Number of Rectangles : 0
Number of Circles : 0
Number of Ellipse : 0
Number of Line : 0
Number of Polyline : 0
Number of Polygon : 0
Number of Path : 0
Number of Groups:1
Other tag:0

***************************************
              SVG PARSER
***************************************
        1.Count Number of Elements:
        2.Add new element:
        3.Create a new SVG and JSON File
        4.EXIT
Enter an Option to proceed further: 2
SELECT AN OPTION TO ADD NEW ELEMENT
        1. RECTANGLE
        2. CIRCLE
        3. ELLIPSE
        4. LINE
        5. POLYLINE
        6. POLYGON
        7. PATH
        8. NEW TAG
        9. EXIT
Select an option to add a new element:
1
Enter option 1 to enter attribute values:
Enter option 2 to enter the entire attribute:
2
Enter the attributes of rectangle:
width="100" height="100" fill="red"         

***************************************
              SVG PARSER
***************************************
        1.Count Number of Elements:
        2.Add new element:
        3.Create a new SVG and JSON File
        4.EXIT
Enter an Option to proceed further: 1
===========COUNT MENU===========
        1.Display RECTANGLE count
        2.Display CIRCLE count
        3.Display ELLIPSE count
        4.Display LINE count
        5.Display POLYLINE count
        6.Display POLYGON count
        7.Display PATH count
        8.Other tag:
        9.Display ALL count
        10.EXIT
Select an option to display the count of an element/elements:
9
Number of Rectangles : 1
Number of Circles : 0
Number of Ellipse : 0
Number of Line : 0
Number of Polyline : 0
Number of Polygon : 0
Number of Path : 0
Number of Groups:1
Other tag:0

***************************************
              SVG PARSER
***************************************
        1.Count Number of Elements:
        2.Add new element:
        3.Create a new SVG and JSON File
        4.EXIT
Enter an Option to proceed further: 3
Enter the name for the SVG file (e.g., MyFile.svg): Test
Your file has been saved as OutputFile.svg
Your JSON file has been saved as output.json.
Both SVG and JSON files have been created. Exiting...
PS D:\C++\SVG_Parser\Home_SVG_Parser\output>
```

Why we chose PugiXML 

Link = [xml parsing - What XML parser should I use in C++? - Stack Overflow](https://stackoverflow.com/questions/9387610/what-xml-parser-should-i-use-in-c)

![Untitled](Documentation%203e14db849a464392b00df46e9b7cecda/Untitled%201.png)

# Steps to run the program.

1. Start
2. Main.cpp ⇒ Run ⇒ user Input ⇒ `../TestFiles/test.svg`
3. Select the choice accordingly.
4. Stop

# Conclusion:

In summary, this program provides a comprehensive interface for SVG manipulation through parsing SVG into an object model, allowing dynamic updates, and outputting the modified SVG in multiple formats. The combination of classes handles each step from loading, editing, and exporting the SVG file.
