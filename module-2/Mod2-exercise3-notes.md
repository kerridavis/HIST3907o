#Module 2, Exercise 3

##APIs

API = application programming interface.

Results often come back in JSON format, which is machine-readable.

We'll be searching for data on [http://search.canadiana.ca/](http://search.canadiana.ca/)

Search term: Ottawa

Date range: 1800-1900

Results: 56,845 results for Ottawa

address in browser shows:

http://search.canadiana.ca/search?q=Ottawa&field=&df=1800&dt=1900

This is a type of API. Everything after /search is a command.

Now we go to [http://search.canadiana.ca/support/api](http://search.canadiana.ca/support/api)


When I add "/&ftm=json" to the end of the search results url, I get a new set of results.

Results: 110,930 results for Ottawa.

So... looks like I've got more results now.

To get individual item records, there's a field called "oocihm". Each individual record in the set of results should have its own oocihm number.

To retrieve these numbers, we write a program.  And by "we", Shawn means "Ian Milligan already wrote it".  Available here: [http://ianmilligan.ca/api-example-sh/](http://ianmilligan.ca/api-example-sh/)

I'm instructed to take note of "curl", "jq", "sed", "awk".

Curl = a program for downloading webpages

jq = for dealing with json

sed and awk = searching within and cleaning up text.

Extra reading to help make sense of all this:  [http://williamjturkel.net/2013/06/15/basic-text-analysis-with-command-line-tools-in-linux/](http://williamjturkel.net/2013/06/15/basic-text-analysis-with-command-line-tools-in-linux/ "Basic Text Analysis with Command Line Tools in Linux")

Now, for the nitty-gritty part of the exercise.  Note, I'm using a Windows 7 computer, so I'm following the Windows instructions in the Workbook.

(Ugh.  More software to download and install.)

1) Need: gitbash.  Therefore must download and install git.

2) We now need jq.  Download and install.

Fun fact: I wasn't sure if I had a 64 bit or 32 bit system.  I needed to know which version of jq to download.  Turns out I have a 64 bit system. Good to know.

Installing jq was a bit underwhelming - it didn't ask me any questions, there was just a split second of the little black box with white text.  I guess that was it?

3) I need to download CoreUtils

(This is a lot for my poor little 2010 Dell Studio!)

Shawn notes that I need to tell my computer that this CoreUtils thing now exists.  Control Panel/Systems and Securities/ System / Advanced System Settings.  Then right click and select "Properties". Then Select Advanced.

"Environment Variables" button.

under "System Variables", highlight "Path", click Edit.... Just see workbook for the details.

4) Now I need to download wget. Must download it to C:Windows directory.

Windows tells me that I need to be an administrator to add something to the Windows directory. Will this totally ruin my machine?!?
 
I'm taking a break for the evening (10:25pm is past my bedtime).

Back to it.

I'm still having trouble with wget.  Can I proceed without it? Let's find out!

I think I figured out copying wget into the Windows directory.  Had to go on YouTube to get tips. 

Changed the program in the canadiana.sh file to search for items between 1800 and 1900.

**Original Code:** pages=$(curl 'http://eco.canadiana.ca/search?q=montenegr*&field=&so=score&df=1914&dt=1918&fmt=json' | jq '.pages')

**Changed Code:** pages=$(curl 'http://eco.canadiana.ca/search?q=montenegr*&field=&so=score&df=1800&dt=1900&fmt=json' | jq '.pages')

Still not any results in Gitbash though.  I'm getting errors to the effect of "wget: command not found".




















