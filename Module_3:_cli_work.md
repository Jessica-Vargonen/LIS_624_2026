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

10) `wc -l` will give a line count

11) `wc -w` will give a word count

12) `wc -c` will give a charater count  
