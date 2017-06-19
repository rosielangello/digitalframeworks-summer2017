So your data broke Excel. Maybe you got that error message about how it couldn't be loaded. Maybe excel crashed. Maybe you tried to write some kind of formula and waited...and waited...and waited.

Here are a five tools and suggestions that might help you find what you want, or at least get you pointed in the right direction. This list is by no means exhaustive.

## Look at the first few rows using `head`.

WHAT: Most unix like systems (which includes the backend of a mac) have this command, and it shows the first 10 lines of a dataset. TKTK PCs.

WHY: Looking at the first few lines, which, if you're lucky, include a header row, can help you determine whether you care about the data and whether there's anything funny going on. For example, if you were hoping to find a specific field and it's not there, maybe you can move on. Or if you were expecting aggregated data but are getting individual-level data, that might explain why it's so huge and giving you so much trouble!

HOW: On a Mac:

a) Save the dataset in a location you can easily find WITH NO SPACES IN THE FILENAME.
b) On a mac, open a terminal window (you can do this by searching for `terminal`)
c) Navigate to the directory containing your data (this is beyond the scope of this lesson, see tktk to learn more about how to do that)
d) Type `head datafilename` (where datefilename is the name of your actual data file).
e) Bonus skill: if 10 lines is not quite enough (or too much!), you can add the option -n followed by the number of lines you want. So for example, if I want to see 15 lines of a file called `rachels_awesome_data.csv`, I would type `head rachels_awesome_data -n 15`
f) Extra bonus skill: `tail` does the same thing as head, except for the last 10 lines.

On a PC: tktktk

## Open the file in a text editor

WHAT: Excel does a lot for you, but because of that takes up a lot of your computer's resources. Text editors require fewer resources and can help you open bigger files.

WHY: A text editor can let you get a better sense of what's in your data and gives you a lot more flexibilty than a few lines in your terminal.

HOW:

a) Get a decent text editor. There are a variety available, some for free, some cost money. I like SublimeText, which requires a license but you can use for free for a while without paying.
b) Open the file in the text editor. You can open the text editor and go to file>open or right-click the file and look for your text editor, or (on a mac) drag your file to the text editor.
c) Wait a moment if opening is still slow. If it takes a really long time this trick might not be for you, but many large datasets that fail in excel will open in less than a minute in SublimeText on a computer with decent resources.
d) Look at your data, scroll around, or search.
e) If it looks like there are weird characters that might be causing excel trouble, you can possibly find and replace them here, save, and then re-open in excel.
f) Bonus tip (for SublimeText): You can open a whole folder of data! under file>open, instead of navigating to a file, just click on the folder you want to open! You can then search the whole folder (it might skip really huge files, but will tell you if it does) using find>find in files.

## Use grep

WHAT: Grep is a very powerful and complicated search tool

WHY: Grep can search huge files, and if you're just looking to see if one thing is in your file, it might do what you need.

HOW: On a Mac:

a) Save the dataset in a location you can easily find WITH NO SPACES IN THE FILENAME.
b) On a mac, open a terminal window (you can do this by searching for `terminal`)
c) Navigate to the directory containing your data (this is beyond the scope of this lesson, see tktk to learn more about how to do that)
d) grep is an enormously powerful (and thus complicated) tool, and it is definitely possible to use without understanding everything it can do for you, so do not panic!
e) To do a simple search type `grep filename -e search_term`. So for example, if I want to search for `rachel` in a document called `people_I_know.txt`, I can type `grep people_I_know.txt -e rachel` and it will print out any lines it finds including `rachel`.
f) Bonus tip: If you want to know what line `rachel` is in, add -n to your search and it'll print the line number before the relevant line. For example: `grep people_I_know.txt -e rachel -n`
g) Tutorials: There are a million grep tutorials. I don't have a particular one to recommend, just google `grep tutorial` and pick one that looks nice if you want to learn more grep.

PC: tktk

## Use csvkit

WHAT: If your giant file is a csv (or similar, delimited file), csvkit will let you slice it up without actually opening it. It can also help you convert non-csv files into csv files.

WHY: If you want to look at a subset of data in the file, or do some sums or other aggregates but can't open the file and play with it manually.

HOW:

a) Make sure you have python installed (if you have a mac, you do, if you have a PC, install it.)
b) Install pip. Pip is a python installer that lets you easily install python libraries. There are other ways to install csvkit, but in general your life will be better with pip. Start by opening a terminal window and typing `which pip`. If it is not blank, you already have pip! Skip to the next step. Otherwise, download [this file](https://bootstrap.pypa.io/get-pip.py). Figure out where you downloaded it to, navigate there in your terminal, and run `python get-pip.py`.
c) Type `pip install csvkit`
d) csvkit is very powerful, and you can find the full documentation, with examples, [here](https://csvkit.readthedocs.io/en/1.0.2/). In the meantime, below are a few examples of things you could do with csvkit. (Assume for all of the examples below that your data is in a file called `data.csv`)
e) Use csvkit to see the headers of your file: `csvcut -n data.csv`
f) Use csvkit to move only some colums of your data to another file: `csvcut -c column_a,column_c data.csv > new.csv` where `column_a` and `column_b` are column names found in step e, and `new.csv` is the file that contains only columns a and b. If this file is much smaller, maybe you can now open it in excel!!!
g) Use csvkit to convert other data formats to csvs: `in2csv data.json > data.csv` where `data.json` is some json data, and `data.csv` is a new file containing your data converted to a csv.


## Get more firepower (or find someone who has it and can help you)

WHAT: If you really need more fine-grained access to a file that's too big or complex to open, you might need to move to a higher-powered solution. Options might include a relational database, a statistical program like SPSS or R, or custom code in a scripting language.

WHY: These methods give you much more control. Of course, they're also much harder.

HOW: Learning to use a database query language or a programming language is more than I can cover in this tipsheet. But hopefully you've learned enough about your dataset from these other tips that you can frame a good question or figure out what you need to learn to do in order to answer the original question that brought you to this dataset. Good luck!