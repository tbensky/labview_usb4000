# Getting an Ocean Optics USB4000 working with Labview

As the title says, here's what I did to get a USB4000 working with Labview

1. Be sure the spectrometer is working on your machine with Oceanview (the stock software).

2. Download and install the NI [Ocean Optics Driver](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=7833BD4A31DA1274E04400144FB7D21D)

3. The problem I had is that when I ran the Labview example code for the USB4000, there was no VISA resource ID for the spectrometer.  It
also did not appear under NI MAX.

4. The issue is that Windows by default uses WinUSB to communicate with USB4000.  Labview and VISA need to use their own
driver for this, called the STS USB driver.  You can download it [here](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=A4A691E2F9B24D8EE0440021287E6A9E).

5. I had a lot of trouble installing this driver.  

* The NI Package Manager wouldn't do it, as it needed some 
dependent package (labview-ng-driver), which is impossible to find.

* You have to navigate to the STS driver, and install it manually. 
 * In Windows 10, the "Update Driver" button couldn't do it, claiming it isn't a appropriate driver.
 * You navigate to the STS driver .INF file and right click on it, then select the `install` option.
 
* Windows may complain the driver isn't digitally signed.  

6. 


