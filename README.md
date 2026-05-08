# heavyset-bls
HeavySet Workout Routines that you can import into HeavySet 

# Text from HeavySet (Runloop) help article

**NOTE:** The source of this article comes from [The Wayback Machine](http://web.archive.org) which archived the now dead link https://intercom.help/runloop/en/articles/3385832-import-and-export-routines-as-plain-text on Jan 14, 2026.

---

As of HeavySet 2018.8 you are able to import routines written in plain text. 

Upon opening HeavySet the app will check your pasteboard for potential routines copied there. If it detects what could be routines you will be presented an alert showing the pasteboard content that could be routines and offers the option to install them. 

If this fails to detect your routines but you are sure they are copied to the pasteboard you can perform this step manually by tapping the Import button shown below.

***Image not available***
  
In the following video I demonstrate how to share routines from the app and how to import them back into the app.

***Video not available***

 
# Syntax

The syntax for importing via text is quite loose which allows us to option of writing our routines out in a text editor and then importing these into the app rather than use the editors. 

Below I will outline the details of the syntax. As example can be seen below:

```
## Full Body B

/3 Day Routine
#ff8800

A. Overhead Press, 3 sets, 8-12 reps, 3:30 rest 
B. Leg Curl, 3 sets, 8-12 reps, 3:00 rest 
C. Seated Calf Raise (Smith), 3 sets, 8-12 reps, 3:00 rest 
D1. Cable Bicep Curl, 3 sets, 8-12 reps, 1:20 rest 
D2. Pushdowns, 3 sets, 8-12 reps, 1:20 rest
```

# Workout name

The only requirement for plain text import is that a routine name must start with two hash symbols, a space, followed by the name. For example:

```
## Full Body
```

# Path

Routine path structure can be maintained. To do so you may optionally include a path after the routine name. Paths consist of the folder names separated by slashes. Paths must start with a slash. For example:

/Wendler 531/Week 1

Folder names that contain slashes will not work with this syntax, so bear that in mind.

# Color

Routine colors may also be added. Be sure to add a hexcode in the format #RRGGBB after the routine name but before the exercises.

# Exercises

Exercises are added as a list. Each line is split into parts separated by commas. The first part is used as the exercise name. The simplest form of this would be:

Squat
Bench Press
Deadlift

As the lines are split into parts after each comma this does mean exercise names may not contain commas when importing via text.

# Supersets

It is possible to create super sets using the text import. To create a superset you should include group names (a single letter with an optional number) before the exercise names. For example:

A1. Bench Press
A2. Barbell Row
B. Overhead Press

The group names are for user readability only. The group names are not sorted during import, so if you renamed the first group in the example as group C if would not be ordered before group B after import. The previous could be rewritten as follows and still import as the same routine:

C. Bench Press
C. Barbell Row
Overhead Press

# Exercise Parameters

You can add all the same exercise parameters via text import as you can within the editor. These are added to the exercises after a comma. Exercise parameters are case insensitive. For example:

`A. Bench Press, 3-4 sets, 10 reps, rest 1:30`

Valid options are:
- Sets
- Rep range
- Intensity
- RPE
- Tempo
- Rest
- Training max update.

## Sets

If an exercise parameter includes the word 'set' the importer will then look for a range within the text. Example ranges are as follows:

3 sets
3-4 sets
3+ sets

This import max sets: 3, min sets: 3 and max sets: 4, min sets: 3 respectively.

## Reps

If an exercise parameter includes the word 'rep' the importer will then look for a range within the text. Example ranges are as follows:

5 reps
8-12 reps
3+ reps

This import max reps: 5, min reps: 8 and max reps: 12, min reps: 3 respectively.

## Intensity

If an exercise parameter includes the text 'int' the importer will then look for a integer or decimal value. Valid intensity values could include:

80% intensity
92.5 int

## RPE

If an exercise value includes the text 'rpe', the importer will then look for an integer or decimal value. Valid RPE values could include.

RPE 8
8.5 rpe

## Tempo

If an exercise value includes the text 'tempo', the importer will then look for an integer value or 1-4 digits. Valid tempo values could include.

tempo 22
2013 Tempo

## Rest

If an exercise value includes the text 'rest', the importer will then look for an integer value optionally followed by a colon and another integer value. If no colon is detected then the value is considered to be seconds, if there is a colon the value is minutes:seconds. Valid rest values could include

90 seconds rest
1:30 rest
3 min rest

The last example would ignore the word min and consider the rest to be measured in seconds.

## Training max update method

Lastly, if the exercise parameter includes the word 'update' the importer will then look for a set of predefined values. These include:

- none
- manual
- manual_1rm
- manual_1rm_higher
- auto_1rm
- auto_1rm_higher

# Extended Syntax

From HeavySet version 2019.1 it's possible to add some addtional meta data to the import file that will allow some custom branding to be displayed with the imported routines. This is perfect for trainers that wish to provide their clients with routines and want to provide some additional information.

Non-upgraded users will only be able to perform routines that have been exported from HeavySet. Files that have been created by hand will appear locked. If you create your routines by hand and want non-upgraded users to try them you will need to import the routines into the app and export them again. You should add your meta data once this has been done.

The attributes can be added:
- Folder name (required)
- Image (aspect ratio of 4:1)
- Color
- Description text (may contain URLs)

The syntax must follow these rules:
- It must appear above the routines in the file.
- The meta data starts and ends with a line containing ---
- There must be a line starting folder: followed by the name of the base folder you want the routines to appear in.
- You may optionally have a line starting with image: followed by the URL of the image.
- You may optionally have a line starting with color: or colour: followed by a hexidecial colour code in the following format #RRGGBB
- Lines that do not start with the above keywords are added to the description text.

Here is an example:

```
---
folder: Runloop Full Body
image: https://www.runloop.com/images/heavyset/heavyset-background-4c06ed85.jpg

color: #3BF27F
Perform Mon/Wed/Fri. Stop each set one rep before failure. Increase weight 5% the following week once you exceed rep range.
More details: https://www.runloop.com
---
```

The result of which looks like this:

***Image not available***
