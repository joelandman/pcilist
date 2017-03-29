This tool was created out of frustration with the set of tools available
for rapid determination of a system PCIe state, specifically the physical
maximum and actual speed and width of a PCIe port.  The lspci tool is
great for querying the kernel PCIe tree, but not so great at presenting useful
information in a summary format.  In fact, to get the useful information,
you have to tell it to be quite verbose.

This is important, if you are debugging a performance issue with a particular
function, and trying to understand why, in the face of an otherwise well
behaved system, performance appears to be suboptimal.  We've seen this now
sufficiently frequently that I want very much to find out if my subsystem is
in fact not operating at the correct speed/width.   

I wanted to see pci id, maximum and actual speed, maximum and actual
width, the kernel driver in use, and a description of the device according
to the driver.  So ... here it is.  


    landman@leela:~/work/development/pcilist$ sudo ./pcilist.pl

    PCIid   MaxWidth ActWidth MaxSpeed ActSpeed     driver       description
    00:00.0        4        0        5                           Intel Corporation Haswell-E DMI2 (rev 02)
    00:01.0        8        0        8      2.5         pcieport Intel Corporation Haswell-E PCI Express Root Port 1 (rev 02) (prog-if 00 [Normal decode])
    00:02.0        8        1        8      2.5         pcieport Intel Corporation Haswell-E PCI Express Root Port 2 (rev 02) (prog-if 00 [Normal decode])
    00:02.2        8        8        8        8         pcieport Intel Corporation Haswell-E PCI Express Root Port 2 (rev 02) (prog-if 00 [Normal decode])
    00:03.0        8        0        8      2.5         pcieport Intel Corporation Haswell-E PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
    00:03.2        8        8        8        5         pcieport Intel Corporation Haswell-E PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
    00:1c.0        1        0        5      2.5         pcieport Intel Corporation Wellsburg PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
    00:1c.4        4        1        5      2.5         pcieport Intel Corporation Wellsburg PCI Express Root Port #5 (rev d5) (prog-if 00 [Normal decode])
    02:00.0        1        1      2.5      2.5    snd_hda_intel Creative Labs SB Recon3D (rev 01)
    03:00.0        8        8        8        8          mpt3sas LSI Logic / Symbios Logic SAS2308 PCI-Express Fusion-MPT SAS-2 (rev 05)
    05:00.0        8        8        5        5            ixgbe Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
    05:00.1        8        8        5        5            ixgbe Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
    07:00.0        1        1      2.5      2.5                  ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 03) (prog-if 00 [Normal decode])
    80:02.0        8        8        8        8         pcieport Intel Corporation Haswell-E PCI Express Root Port 2 (rev 02) (prog-if 00 [Normal decode])
    80:03.0       16       16        8      2.5         pcieport Intel Corporation Haswell-E PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
    82:00.0       16       16        8      2.5           nvidia NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2) (prog-if 00 [VGA controller])
    82:00.1       16       16        8      2.5    snd_hda_intel NVIDIA Corporation Device 0fbc (rev a1)


Notice the width, speed and other differences.  
