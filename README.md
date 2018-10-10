l2munger
========

This utility allows the simple modification of a level II NEXRAD file.  It 
supports changing the timestamp and NEXRAD location within the file.

This allows you to move archived files in time and space, which makes for
a nice way to do case studies as users will not easily recognize the case.

Here is how you use it:

    ./l2munger <new_site_id> <timestamp> <speedup_factor> <old compressed file> <speedup_factor>

so for example to move some data from 2012 for KLIX to Des Moines:

    ./l2munger KDMX 2014/02/05 10:00:00 1 KLIX20121201_011448_V06

This code requires that your level II NEXRAD file not be compressed, either
externally by compress, gzip, or bzip and internally by bzip.  If your file is
internally bzip compressed, then this python script should remove that compression.

    python debz.py <input_filename>  <output_filename>


So behold, an example workflow to get Hurricane Harvey over Iowa on January 1.

    wget https://noaa-nexrad-level2.s3.amazonaws.com/2017/08/25/KBRO/KBRO20170825_195747_V06
    python debz.py KBRO20170825_195747_V06 KBRO20170825_195747_V06.uncompressed
    ./l2munger KDMX 2017/01/01 12:00:00 1 KBRO20170825_195747_V06.uncompressed

    $ ls -l KDMX20170101_120000
    -rw-rw-r-- 1 akrherz akrherz 52163576 Aug 25 15:05 KDMX20170101_120000

![GR2 Screenshot](/images/kdmx_20170101_1159_BR_0.4.png?raw=true "GR2 Screenshot")
