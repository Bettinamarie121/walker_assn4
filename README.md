# walker_assn4
# Assn4_Walker.sh

#! /bin/bash#! /bin/bash

#This script creates and executes a possible_votersnew.txt script that extracts and
#sorts a subset of voters’ data from possible_voters.txt

#cut field 2 from possible_voters.txt and make a new file “age.txt” with voters age
cut -f2 possible_voters.txt | grep -v Age >age.txt
#grep -v shows only the lines that do not match

#make a header file for eligibility
echo "Eligible?" > header.txt

#annotate voters age.txt with “yes or no” based-on age greater than 17
while read line
        do if [ $line -gt 17 ]
        then echo "yes"
        else echo "no"
fi              #closes this loop
done < age.txt>>header.txt
#to append yes/no to header.txt and “done” to close loop

#paste possible_voters.txt first then header.txt
#want header.txt data to be added to the end and not the beginning of
#possible_votersnew.txt

paste possible_voters.txt header.txt > possible_votersnew.txt

#header for first 10 of possible_voters.txt and possible_votersnew.txt can be on
#same line
head possible_voters.txt possible_votersnew.txt

#Count the number of eligible voters
#set variable to string of commands/statement

NUM=$(grep "yes" possible_votersnew.txt| wc -l)
echo 'There are '$NUM' eligible voters!'
#Note there are single quotes around the value of the variable “$NUM and the
#statement

