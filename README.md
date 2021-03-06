# SCPD Scraper

This program downloads scpd videos for a given class in the order
that they happened as a wmv, then converts them to a mp4. Each time 
the script is run, it will update to download all of the undownloaded
videos. 

This script is modified from the one by Ben Newhouse [https://github.com/newhouseb](https://github.com/newhouseb).

Unfortunately, there are lots of dependencies to get it up and running

1. BeautifulSoup for parsing or [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)
2. Mechanize for emulating a browser or [http://wwwsearch.sourceforge.net/mechanize/](http://wwwsearch.sourceforge.net/mechanize/)
3. mimms for downloading video streams [sudo apt-get install mimms] or using MacPorts for Mac [http://www.macports.org/](http://www.macports.org/)
4. (optional- To convert to mp4) Handbrake CLI, for converting to mp4: [http://handbrake.fr/downloads2.php](http://handbrake.fr/downloads2.php)
5. (optional- Prevents scraper from crashing when notes are being used) html5lib parser for BeautifulSoup http://www.crummy.com/software/BeautifulSoup/bs4/doc/#installing-a-parser

Here are the commands for the required steps above:

    sudo easy_install beautifulsoup4
    sudo easy_install mechanize
    sudo port install mimms
    
Usage: 
    python scrape.py [yourUserName] [optional flags] "Interactive Computer Graphics" "Programming Abstractions" ...


The way to use it is to keep a folder of videos, and once you have watched them, move them
into a subfolder called 'watched'. So it also won't redownload files that are in the 'watched' subfolder.


#Flags
Any of the following flags (besides "--help") can be used in conjunction with listed coursenames
give information on usage:
	--help
download all new videos from courses held in subdirectories whose names match the courses:

	--all
organize videos by downloading them to folders whose names match the courses:

	--org
convert lecture videos to mp4:

	--mp4
download the newest lectures first:

	--priority=new

#Example Calls
To download all videos in Interactive Computer Graphics and Programming Abstractions:

	python scrape.py claytons --all "Interactive Computer Graphics" "Programming Abstractions"

To download all videos as detailed by subdirectories as well as all videos in Interactive Computer Graphics and convert them to mp4:

	python scrape.py claytons --all --org --mp4 "Interactive Computer Graphics"

To download a single course to the root directory:

	python scrape.py claytons "Interactive Computer Graphics"
