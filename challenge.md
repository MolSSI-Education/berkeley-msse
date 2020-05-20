---
title: Programming Challenges
layout: default
---

## Programming Challenges

Before you arrive at the bootcamp, we'd like to make sure you arrive with some Python skills. We will not be starting by teaching an introduction to programming, so it is important that you be able to program in Python before you arrive. This page outlines some programming challenges you can try to test your Python programming skills.

MolSSI is offering an introductory level Python Scripting webinar series the first If you are unsure of how to proceed, or are unable to complete the challenges outlined here, please sign up for our June webinar series! This program is taught live and is free to all participants. See more information [here](https://molssi.org/2020/05/18/june-webinar-series-fast-track-python-data-and-scripting/).

For these challenges, you will need to download some [data](https://education.molssi.org/python_scripting_cms/data/data.zip). This link is a zip folder which contains files you will work with for this challenge.

### Challenge 1: File parsing

In the challenge materials, there is a file called 03_Prod.mdout. This is a file output by the Amber molecular dynamics simulation program.

If you open the file and look at it, you will see sections which look like this:
```
 NSTEP =      100   TIME(PS) =      20.200  TEMP(K) =   296.43  PRESS =  -300.8
 Etot   =     -4585.1049  EKtot   =      1129.2368  EPtot      =     -5714.3417
 BOND   =         1.5160  ANGLE   =         6.9846  DIHED      =        11.7108
 1-4 NB =         4.3175  1-4 EEL =        49.9911  VDWAALS    =       882.6741
 EELEC  =     -6671.5358  EHBOND  =         0.0000  RESTRAINT  =         0.0000
 EKCMT  =       583.7810  VIRIAL  =       786.8823  VOLUME     =     31270.0410
                                                    Density    =         0.6104
 Ewald error estimate:   0.3214E-03
 ------------------------------------------------------------------------------
 ```
Your assignment is to parse this file and pull out the values associated with the `Etot` keyword. Write a new file containing a list of the total energies. Name your file `Etot.txt`. When you open it, it should look like this:

```
-4585.1049
-4573.5326
-4548.1223
-4525.341
-4542.8995
-4550.9376
-4543.8652
-4570.4109
-4550.4225
-4585.2078
...
```
`...` indicates that you will have many more rows. We’ve only shown the first 10 here.

### Challenge 2: File parsing and molecular geometry calculation

In the lesson materials, there is a file in the data folder called “water.xyz”. This is a very simple, standard file format that is often used to distribute molecular coordinates. The first line of the file is the number of atoms in the molecule, the second line is a title line (or may be blank), and the coordinates begin on the third line. The format of the coordinates is

```
Atom_Label  XCoor   YCoor   ZCoor
```
and the default units (which are used in this example) are angstroms.

Write a code to read in the information from the xyz file and determine the bond lengths between all the atoms. There is a numpy function to take the square root, numpy.sqrt(). To raise a number to a power, use `**`, as in `3**2 = 9`. Your code output should look something like this.

```
O to O : 0.0
O to H1 : 0.969
O to H2 : 0.969
H1 to O : 0.969
H1 to H1 : 0.0
H1 to H2 : 1.527
H2 to O : 0.969
H2 to H1 : 1.527
H2 to H2 : 0.0
```

### Challenge 3: Creating a command line program

For this challenge, you will return to your solution from Challenge 1.

Create a command line script using `argparse` which can take in an `mdout` file from Amber, pull out total energy for each time step, and write a new file containing these values. The script should take a file name (03_Prod.mdout) and output a file with the names `filename_Etot.txt`. You can use your script from Challenge 1 as a starting point for this homework. In contrast to the first challenge, truncate the last two values from your script (these are an average value and a fluctuation value) from the file you write. Add an additional optional argument to your script which allows the user to output a plot of the total energy using `matplotlib`. The names of the plot files should be `file_name.png` where the name of the file was `file_name.mdout`.

Call your script analyze_mdout.py. You should be able to call the script in the following way:
```
$ python analyze_mdout.py 03_Prod.mdout
```
When you call help, you should get the following output:
```
$ python analyze_mdout.py --help
usage: This script parses amber mdout files to extract the total energy. You can also use it to create plots.
      [-h] [--make_plots] path

positional arguments:
 path          The filepath to the file to be analyzed.

optional arguments:
 -h, --help    show this help message and exit
```
 