# Getting an Ocean Optics USB4000 working with Labview (Windows 10)

As the title says, here's what I did to get a USB4000 working with Labview

1. Be sure the spectrometer is working on your machine with Oceanview (the stock software). Leave it plugged in as
you go through these steps.

2. Download and install the NI [Ocean Optics Instrument Driver](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=7833BD4A31DA1274E04400144FB7D21D)

3. The problem I had is that when I ran the Labview example code for the USB4000 (part of the instrument driver), 
there was no VISA resource ID for the spectrometer.  It also did not appear under NI MAX.

4. The issue is that Windows by default uses WinUSB to communicate with USB4000.  Labview and VISA need to use their own
driver for this, called the STS USB driver.  You can download it [here](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=A4A691E2F9B24D8EE0440021287E6A9E).

5. I had a lot of trouble installing this driver.  

* The NI Package Manager wouldn't do it, as it needed some 
dependent package (labview-ng-driver), which is impossible to find.

* You have to navigate to the STS driver (that is, the actual file for it), and install it manually. 
    * In Windows 10, you can try going to the "Update Driver" button for the Ocean Optics device.  Navigate so you can 
    tell it you 'have a disk' (as in a driver disk), and point it to the STS file.  This didn't work for me, as Windows claimed it wasn't a appropriate driver.
    * I had to navigate to the STS driver .INF file directly and right click on it, then select the `install` option.
    * Windows may complain the driver isn't digitally signed.  To get around this, restart the computer
    while holding down the [Shift] key.  Under the 'troubleshooting' option, select 'Start up options' and #7 will disable this digital
    signature checks (until the next boot).

6. Once installed, you have to now switch the driver associated with the USB4000 from the WinUSB
driver to this STS driver. You can do this by going to the device manager (hold down Windows key + X)
and sift through the drivers until you find the Ocean Optics driver.  A selection box should allow you
to select which driver you want to use (WinUSB or STS)---choose STS.

Once the drivers were switched, the VISA resource ID will come up both in the Windows device manager, NI MAX and
in the Labview code.  I think actually once I got the STS driver to install, it took over the older
WinUSB automatically and I saw it in the device manager tree (I never had to make the driver switch happen).

When I saw the USB4000 spectrum come up live in Labview, it was a pretty sweet moment!

Thank you Norm H. at Ocean Optics for your help with this.



