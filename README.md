# Getting an Ocean Optics USB4000 working with Labview

As the title says, here's what I did to get a USB4000 working with Labview

1. Be sure the spectrometer is working on your machine with Oceanview (the stock software).

2. Download the NI [Ocean Optics Driver](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=7833BD4A31DA1274E04400144FB7D21D)

3. The problem I had is that when I ran the Labview example code, there was no VISA resource ID for the spectrometer.  It
also did not appear under NI MAX.


