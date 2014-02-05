l2munger
========

This utility allows the simple modification of a level II NEXRAD file.  It 
supports changing the timestamp and NEXRAD location within the file.

This allows you to move archived files in time and space, which makes for
a nice way to do case studies as users will not easily recognize the case.

Here is how you use it:

    ./l2munger <new_site_id> <timestamp> <old compressed file>

so for example to move some data from 2012 for KLIX to Des Moines:

    ./l2munger KDMX 2014/02/05 10:00:00 KLIX20121201_011448_V06


