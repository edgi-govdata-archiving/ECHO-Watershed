{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Watersheds\n",
    "\n",
    "This notebook examines ECHO data on federal level mapping of watersheds.\n",
    "and RCRA_ENFORCEMENTS.\n",
    "\n",
    "From ECHO_EXPORTER:\n",
    "<ul>\n",
    "    <li>RCRA_IDS - to match facilities/violations in RCRA_FACILITIES and RCRA_VIOLATIONS</li>\n",
    "    <li>FAC_DERIVED_CD113 - 113th congressional district</li>\n",
    "    <li>FAC_LAT and FAC_LONG - latitude and longitude</li>\n",
    "    <li>RCRA_PERMIT_TYPES</li>\n",
    "</ul>\n",
    "\n",
    "RCRA Permit Types include:\n",
    "<ul>\n",
    "    <li>TSDF = Treatment, Storage and Disposal facility</li>\n",
    "    <li>LQG = Large Quantity Generator</li>\n",
    "    <li>SQG = Small Quantity Generator</li>\n",
    "    <li>CESQG = Conditionally-Exempt Small Quantity Generator</li>\n",
    "</ul>\n",
    "\n",
    "From RCRA_ENFORCEMENTS we use:\n",
    "<ul>\n",
    "    <li>ENFORCEMENT_DESC - a description of the enforcement action </li>\n",
    "    <li>ENFORCEMENT_AGENCY - which agency executed the enforcement</li>\n",
    "    <li>ENFORCEMENT_ACTION_DATE</li>\n",
    "</ul>\n",
    "\n",
    "A state and congressional district must be chosen using the dropdown\n",
    "widgets that are provided."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "---"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## How to Run\n",
    "* If you click on a gray **code** cell, a little “play button” arrow appears on the left. If you click the play button, it will run the code in that cell (“**running** a cell”). The button will animate. When the animation stops, the cell has finished running.\n",
    "![Where to click to run the cell](https://github.com/edgi-govdata-archiving/EEW-Image-Assets/blob/master/Jupyter%20instructions/pressplay.JPG?raw=true)\n",
    "* You may get a warning that the notebook was not authored by Google. We know, we authored them! It’s okay. Click “Run Anyway” to continue. \n",
    "![Error Message](https://github.com/edgi-govdata-archiving/EEW-Image-Assets/blob/master/Jupyter%20instructions/warning-message.JPG?raw=true)\n",
    "* **It is important to run cells in order because they depend on each other.**\n",
    "* Some cells, like the one shown below, will create a dropdown menu after you run them. Be sure to make a selection (for example, click to change NY to LA) before running the next cell.\n",
    "![Dropdown menu](https://github.com/edgi-govdata-archiving/EEW-Image-Assets/blob/master/Jupyter%20instructions/dropdown.JPG?raw=true)\n",
    "* Other cells will simply print information when you run them, like this one:\n",
    "![Simple cell](https://github.com/edgi-govdata-archiving/EEW-Image-Assets/blob/master/Jupyter%20instructions/cell-simple.JPG?raw=true)\n",
    "* Run all of the cells in a Notebook to make a complete report. Please feel free to look at and **learn about each result as you create it**!"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "---"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Let's begin!"
   ]
  },
