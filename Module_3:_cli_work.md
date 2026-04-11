# Searching with grep

### Steps

1) Open edit and input table information to be searched.

2) `grep "Chrome" operating-systems.csv` to search for Chrome in table
     * got one result: Chrome OS, Proprietary, 2009
  
3) `grep "chrome" operating-systems.csv` got no results because it's case senstive

4) `grep -i "chrome" operating-systems.csv` by adding -i it ingnores the case of the letters

5) `grep -vi "chrome" operating-systems.csv` by adding -vi it gives everything but chrome and ingnores the case

6) `grep -vi "^os" operating-systems.csv` by adding ^ it gets rid of lines that start with what is in the ""

7) `grep -vi "year$" operating-systems.csv` by adding $ it means the end of the line of what is in ""

8) `grep -ic "proprietary" operating-systems.csv` by adding c it counts the lines with what is in ""

9) `grep -vic "year$" operating-systems.csv` by putting everything together we can count the lines not including the header

10) `wc -l operating-systems.csv` will give a line count

11) `wc -w operating-systems.csv` will give a word count

12) `wc -c operating-systems.csv` will give a charater count

13) `grep -Ei "(bsd|atari)" operating-systems.csv` by adding E it searches for what is in the "()"
    what is in the (|) is a boolean or

14) `grep -iw "os" operating-systems.csv` by adding w it searches for what is in "" exactly

15) `grep -i "linux" -A2 operating-systems.csv` by adding A2 it will list the two lines after what is in ""     

16) `grep -i "linux" -B2 operating-systems.csv` by adding B2 it will list the two lines before what is in ""

17) `grep -i "linux" -C2 operating-systems.csv` by adding C2 it will list before and after

18) `grep -i -m1 "proprietary" operating-systems.csv` by adding m1 it will stop after the first listing of ""

19) `grep -in "proprietary" operating-systems.csv` by adding n it will give the line number

20) `grep -Eiw "[a-z]{5}" operating-systems.csv` by adding the berackets in "" we do a charater search

21) `grep -Eiw "[0-9]{4}" operating-systems.csv` this is for number searches

22) `grep -Eiw "m.{3}s" operating-systems.csv` "letter it starts with.{number of letters in between} ending letter"

23) upload bibtex file from web of science

24) `grep "^@" savedrecs.bib` This will give all of the material types ie atricle, inproceedings

25) `grep -Eio "^@(A|B)[A-Z]*" savedresc.bib | sort` this gives just the word article

26) 
