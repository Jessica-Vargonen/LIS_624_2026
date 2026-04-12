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

25) `grep -Eio "^@(A|B)[A-Z]*" savedrecs.bib | sort` this gives the words after the @ 

26) `grep -oi "^@[a-z]*" savedrecs.bib | sort | uniq -c` adding the c gives me the type count

27) `head -n20 savedrecs.bib` will give me the first 20 line of the file, head will auto give 10 lines but you can put in any number

28) `grep -i "journal" savedrecs.bib` will give the lines with journal, can put any word in the "" to search for

29) `grep -i "^journal =" savedrecs.bib | cut -d"=" -f2 |\sed 's/ {//' | sed 's/},//' | \sort | uniq -c | sort -nr` will list the journal titles

30) `grep -o "Times-Cited = {[0-9]*" savedrecs.bib | \awk -F"{" 'BEGIN { printf "Total Citations: "} \ { sum +=2; } \END { print sum }'` to show the number of times that it has been cited

31) `grep -iw "li" savedrecs.bib` to find Li in the files

32) `grep -i "^author =" savedrecs.bib` to give all of the authors

33) `grep -i "^author =" | -iw "li" savedrecs.bib` trying to get the author lines with Li in them, didn't work

34) `grep -i "author.*li" savedrecs.bib` closer

35) `grep -iw "^author.*li" savedrecs.bib` did it!

# Managing Software

### Steps

1) `apt search tldr`: 

2) `sudo apt install tldr`: installed

3) `tldr grep`: directory does not exist 

4) `sudo apt --purge remove tldr`: removed tldr

5) `sudo apt autoremove`: removed tldr, freed up 27.8 MB disk space

6) `sudo apt clean`: to remove cached packages

7) `sudo apt install tldr-py`: installed

8) `tldr grep`: no such command 

9) `tldr -h`

10) `sudo apt --purge remove tldr-py`: removed, freed up 42 kB

11) `apt search bsd games`

12) `sudo apt install killbots` to install game called killbots

13) `cd /usr/games` to open the directory

14) tried to open killbots and it doesn't work on my system so I removed it

# Library Search

### Steps

1) `apt search yaz`

2) `apt show yaz`

3) `sudo apt install yaz`

4) `man yaz-client` to access the manual

5) `man bib1-attr` to see what attributes are available

6) `yaz-client` to start yaz program

7) `open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY` open Kentucky's library catalog

8) `find @and @attr 1=4 "information" @attr 1=21 "library science"`
    * find is the command that sends a search request
      
    * @and is the operator signifying a Boolean AND search of the next two attributes
      
    * @attr 1=4 instructs the query to search for the term in the Title field
    
    * "information" is the term for the Title search
    
    * @attr 1=21 instructs the query to search for the term in the subject heading field
    
    * "library science" is the second search term for the subject heading search
  
9) `show 1` to show first record changing the number will change the record shown

10) `f @and @attr 1=21 "library science" @attr 1=21 "philosophy"` to look for library science and philosophy in 650 field

11) `f @attr 1=1 "mcmurtry, larry"` to find name

12) `f @attr 1=1016 "c programming language"` to search in the any field

13) `yaz-client -m records.marc` to append bibliographic records to a file, records.marc is the file name

14) `open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY` to open again

15) `find @and @attr 1=4 "information" @attr 1=21 "library science"`

16) `show 1` `show 2` `show 3` `quit`

17) `head records.marc` to see a very unreadable file, marc record

18) `yaz-marcdump -o json records.marc > records.json` json is the output file, records.marc is the input file, records.josn is the output file 

19) `head records.json` to see that previous command converted it to a json file

20) `less records.json` to see file

21) `jq . records.json > records-formatted.json` jq to allow us to examine the files in a better way

22) `jq '.fields[] | select(has("650")) | .["650"].subfields[] | select(has("a")) | .a' records-formatted.json`

23) `jq '.fields[] | select(has("650")) | .["650"].subfields[] | select(has("x")) | .x' records-formatted.json | sort | uniq -c | sort` to sort

24) `jq '.fields[]' records-formatted.json` to select all fields

25) `jq '.fields[] | select(has("650"))' records-formatted.json` to select 650 fields

26) `yaz-marcdump -o marcxml records.marc > records.xml` to convert to xml file

27) `yaz-client` `set_marcdump records.new` `open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY` `find @and @attr 1=4 "technology" @attr 1=21 "library science"` `show 1 + 132`

28) `yaz-marcdump -o json records.new > records_new.json` create json file

29) `jq '.fields[] | select(has("650")) | .["650"].subfields[] | select(has("a")) | .a' records_new.json |\
sort | \
sed 's/\.//g' | \
awk '{ print tolower($0) }' | \
sort | \
uniq -c | \
sort -n` 

### Issuses Encountered:

 * I didn't really run into any issues when going through searching with grep, managing software, and library search. 

 * The only thing was trying to figure out how to search for a specific author when using grep. I was able to figure it out by looking up on the internet how to do it. I got a parctial answer and was able to figure it out from there. 

### Things I Learned:

 * I learned how to use grep to search and not be afriad to look for answers on the internet, I didn't find exactly what I was looking for but it gave me a jumping off point. 
    
