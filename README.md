 [![Code of Conduct](https://img.shields.io/badge/%E2%9D%A4-code%20of%20conduct-blue.svg?style=flat)](https://github.com/edgi-govdata-archiving/overview/blob/master/CONDUCT.md)
 
# ECHO-Watershed
This repo centers on a Jupyter Notebook designed to draw on EPA's ECHO database to understand who is polluting what and where in watersheds across the United States. We acheive this by accessing data related to the Clean Water Act. More information on the Clean Water Act can be found here: https://docs.google.com/presentation/d/1g6ZN3B5jvs3F1VAigiUtNNezjXdJnzuELfo9Deo9Y2w/edit?usp=sharing

The notebook asks users to select a common geographic area—zipcode(s)—and finds the USGS watershed boundaries, known as a Hydrologic Unit Code or HUC code, that intersect with the zipcode(s). The rest of the notebook gathers information about facilities that report under the Clean Water Act in the watersheds.

## Demo
Watch a demo of the notebook made by @mraisle: https://www.youtube.com/watch?v=gR5jVqb43os

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
