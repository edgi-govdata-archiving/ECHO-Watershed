 [![Code of Conduct](https://img.shields.io/badge/%E2%9D%A4-code%20of%20conduct-blue.svg?style=flat)](https://github.com/edgi-govdata-archiving/overview/blob/master/CONDUCT.md)
 
# ECHO-Watershed
This repo centers on a Jupyter Notebook designed to draw on EPA's ECHO database to understand who is polluting what and where in watersheds across the United States. We acheive this by accessing data related to the Clean Water Act. More information on the Clean Water Act can be found here: https://docs.google.com/presentation/d/1g6ZN3B5jvs3F1VAigiUtNNezjXdJnzuELfo9Deo9Y2w/edit?usp=sharing

The notebook asks users to select a common geographic area—zipcode(s)—and finds the USGS watershed boundaries, known as a Hydrologic Unit Code or HUC code, that intersect with the zipcode(s). The rest of the notebook gathers information about facilities that report under the Clean Water Act in the watersheds.

## Demo
Watch a demo of the notebook made by @mraisle: https://www.youtube.com/watch?v=gR5jVqb43os

## Tutorial
### In brief
This guide provides a hands-on example of one use-case scenario for the Environmental Enforcement Watch (EEW)’s Watershed Notebook for analysis of US EPA data on enforcement of and compliance with environmental protection laws. See the full tutorial guide here: https://docs.google.com/document/d/1fOL1O30cAXS7iOZMItSekG8E8KIUfH-EaYG601W-ncM/edit#heading=h.23ipeq9w0oqj

### Getting Set Up
The Notebook is available to anyone freely here: https://github.com/edgi-govdata-archiving/ECHO-Watershed/blob/main/ECHO_Watershed.ipynb

A Notebook is short for Jupyter Notebook, a popular data science tool that mixes together “cells” of computer programming code with cells of output and cells of text instructions and context. In this guide we rely on the Google Colab platform to run the Notebook, though advanced users can run it on any platform of their choosing (e.g. Binder, CoCalc, or a local machine) by downloading the .ipynb file from our GitHub repo.

You and/or your students (really, any user) will need to log into a Google account in order to run the Notebook here: https://colab.research.google.com/github/edgi-govdata-archiving/ECHO-Watershed/blob/main/ECHO_Watershed.ipynb Please note that the Notebook does not store any information you enter. We at EDGI won’t see it unless you share it with us.

### Other notes
- Some cells of the Notebook can take a while to run. If you’re trying to get data for many large areas, be patient!
- You don’t necessarily need to run each and every cell to accomplish what you’re trying to do. 

### Scenario: Educators 
You’re a University teacher leading a discussion about environmental justice. You might start by encouraging students to investigate the polluting facilities in their own neighborhoods or near campus.

#### Begin! 
Here we load some helper code to get us going in our analysis of water pollution and polluters. You'll know this is completed when a small "Done!" appears at the bottom of the gray cell (right before Step 2). 

#### Run some stuff.
This cell must be run to bring in some utility functions. Like Step 1, we're just looking for a "Done!" at the bottom of this gray cell.

#### Where do you want to search?
The first piece of information students will need to enter is a zip code, or multiple zip codes. Again, this might be for the campus area or from where they grew up. Not everyone knows what USGS (United States Geological Survey) Hydrologic Unit Code (HUC) they live in, but they probably know their five digit zip code. The Notebook returns all the watersheds that at least partially traverse the zip code(s).

Let’s look closely at the Boston area in Massachusetts. We’ll enter 02150, which covers the city of Chelsea, as well as 02130, which covers the Jamaica Plain neighborhood: 
![image](https://user-images.githubusercontent.com/6888951/134581168-12e786f4-fc8b-4d1b-95be-fc7c9419c5b0.png)

NOTE: Computers aren’t smart. Be sure to remove any spaces between your zip codes so that the program recognizes them both. 
NOTE: You can just proceed to the next cell after entering the zip codes - the program will store your entry for later use so there’s no need to re-run this cell. Doing so will actually reset your input. 

Watersheds are curious beasts. They come nested together in different sizes, a bit like Matryoshka dolls. HUCs with eight digits—like 18090203—cover more area than 10 digit ones. Each eight digit HUC will have several 10 digit ones nested within them. In the figure at the right, the Death Valley-Lower Amargosa HUC 8 watershed is broken into more than a dozen 10 digit watersheds, including 1809020303, Marble Canyon.
![image](https://user-images.githubusercontent.com/6888951/134581233-90053c5e-24b5-4f26-a7ee-0ec16f91b2c1.png)

If you want to search for as wide of a range of facilities as possible, choose an eight digit HUC as your unit of analysis. If you need to narrow in on an area, start with the 10 digit HUC. You can always go back and change your selection, re-running the cells of code. 

For our two zip codes, let’s show facilities in the 8 digit HUC(s) that intersect with them:
![image](https://user-images.githubusercontent.com/6888951/134581291-2a80d84c-ebf4-4fc1-b729-e7e30bd944d3.png)

NOTE: You can just proceed to the next cell after choosing the HUC size - the program will store your entry for later use so there’s no need to re-run this cell. Doing so will actually reset your input.

#### Get the data!
This step pulls the data we need for the selected zipcodes and watershed level (HUC8) we selected from the copy of the ECHO database.
We are going to go get data about industrial facilities in these areas. We utilize records from the EPA's Environmental Compliance and History Online, or ECHO, database. EDGI keeps our own copy of this database that is updated every week by our partners at Stony Brook University. 
![image](https://user-images.githubusercontent.com/6888951/134581344-4b55b907-994d-42c4-834e-ed93983304c4.png)

Note that it may take some time for this cell to finish depending on how many facilities there are! You will see “Done!” when the data is loaded.

#### Show me the data!
Where exactly are these facilities though? How many fall within the zip codes themselves and how many are further upstream in the watershed? We can map them! 
![image](https://user-images.githubusercontent.com/6888951/134581374-6b9fc465-f6ee-4be5-a446-7143afab2d86.png)

The number of facilities in each watershed (there’s just one HUC8 that encompasses our two example zip codes) is shown in the circles. As we zoom in on the map, we start to see the actual locations of specific facilities.

![image](https://user-images.githubusercontent.com/6888951/134581443-4090cd0e-4009-4ab8-8f1e-f5c1153f90fe.png)
![image](https://user-images.githubusercontent.com/6888951/134581460-1d560762-a99f-46ec-8b50-f267ef6dd32e.png)
![image](https://user-images.githubusercontent.com/6888951/134581472-9a400adc-717f-4f9d-8817-b98b09e1e042.png)

Clicking on each orange circle pulls up the name of the facility in that location. 

The next cell of code shows us the facilities in this watershed that have been the most non-compliant with the Clean Water Act over the past 13 quarters, or a little over three years. (Pro-tip: if you want to see more than just 20 facilities ranked in terms of non-compliance, you can click in the cell and change 20 to some other number and then re-run it!)

![image](https://user-images.githubusercontent.com/6888951/134581519-5290cb02-6740-4b10-8bb4-724c20c45e47.png)

#### Explore! 
That’s it! We’ve accomplished what we set out to do - we found the location of polluting facilities in a given area. We don’t need to run this part of the Notebook unless we want to learn more about these facilities’ compliance with environmental protection laws. 
You might have students do internet searches on the facilities from Step 5 to learn more about them.

#### Looking at Discharge Monitoring Reports 
We’ve accomplished what we set out to do - we found the location of polluting facilities in a given area. We don’t need to run this part of the Notebook unless we want to learn more about what these facilities’ have reported releasing into the watershed. 

#### Share your work!
If you proceed further into the Notebook, you can download the datasets you create in 6.c. and 7.c. 

Under "File" in the top-left corner of the Colab window, select "Print" and choose "Save as PDF" This will download a static PDF copy of the Notebook to your computer.

- Email, tweet, and otherwise let the world know about your findings!
- Tell us what you found, whether anything that went wrong, or if you would like to arrange a 1:1 workshop.
- Send an email to environmentalenforcementwatch@gmail.com or reach us on Twitter @EEW_Network


## Default branch - 'main'
The 'master' branch is no longer the repo's primary branch in line with EDGI's policy decided here: https://github.com/edgi-govdata-archiving/overview/issues/241

> If someone has a local clone, they can update their locals like this:
```
$ git checkout master
$ git branch -m master main
$ git fetch
$ git branch --unset-upstream
$ git branch -u origin/main
$ git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```
> The above steps accomplish:
> - Go to the master branch
> - Rename master to main locally
> - Get the latest commits from the server
> - Remove the link to origin/master
> - Add a link to origin/main
> - Update the default branch to be origin/main

(From @jywarren at Public Lab: https://github.com/publiclab/plots2/issues/8077)

## License & Copyright

Copyright (C) <year> Environmental Data and Governance Initiative (EDGI)
This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, version 3.0.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

See the [`LICENSE`](/LICENSE) file for details.
