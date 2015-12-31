# ns3-frame-capture

This repository includes patches to the network simulator ns-3 in order to support frame capture (i.e. message-in-message reception) for wifi frames. Patches modify the wifi model (esp. interference helper) in ns-3.16.

The experimental investigations preceding this code adaption are explained in: **Paul Fuxjaeger, Stefan Ruehrup: Validation of the NS-3 Interference Model for IEEE802.11 Networks. 8th IFIP Wireless and Mobile Networking Conference (WMNC 2015), October 2015**. 
Please cite this publication when using the patch in your project.

### Patching ns-3.16
The patches can be applied by `patch < DIFF-FILE` to the following files in src/wifi/model of the ns-3.16 repository:
* interference-helper.cc
* interference-helper.h
* wifi-phy-state-helper.cc
* yans-wifi-phy.cc
* yans-wifi-phy.h

### Using frame capture in simulations
In order to activate frame capture, the following parameters have to be set:
* --ns3::YansWifiPhy::enablePacketCapture=1 
* --ns3::YansWifiPhy::PacketCaptureSIR=8
The first parameter enables packet capture, the second sets the minimum ratio, where capture (reception of a higher power frame) is possible while being in receive mode. Note that the ratio is linear.

### Acknowledgement
The Austrian Competence Center “FTW Forschungszentrum Telekommunikation Wien GmbH” is funded within the program COMET – Competence Centers for Excellent Technologies by BMVIT, BMWFJ, and the City of Vienna. The COMET program is managed by the FFG.

### License
Copyright (C) 2015 - FTW Forschungszentrum Telekommunikation Wien GmbH (www.ftw.at)

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License version 2 as published by the Free Software Foundation;

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program; if not, see http://www.gnu.org/licenses/.
