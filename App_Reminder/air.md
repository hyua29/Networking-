PMK: pairwise master key
=========================
PSK: phase-shift keying
============================
PTK: Pairwise Transient Key 
=============================
PSK: pre-shared key
====================
MIC: Message Integrity Code 
============================
ARP: address resolution protocol
==================================
- ARP is address resolution protocol: A TCP/IP protocol used to convert an IP address into a physical address, such as an Ethernet address. A host wishing to obtain a physical address broadcasts an ARP request onto the TCP/IP network. The host on the network that has the address in the request then replies with its physical hardware address. 
- IMP iwconfig wlan0mon channel 1 -> adaptor switches itself to all channel to receive all data but it might aireplay need a fixed channel
airmon-ng start interface 

Dump packets and capture handshake
===================================
- airodump-ng -c _channelNumber -w ~/Desktop/filename --bssid _id wlan0mon
- aireplay-ng --deauth _numberOfDeauthPackets/_0 -a [BSSID’s MAC Address] -c _clientMAC[optional] wlan0mon
- aircrack-ng -J <new hashcat file name> <cap file with handshake (.cap)>
- airdecap-ng -p _pw -e _essid _file (to decrypt wpa, all handshakes are required; a new file will be created)

Pre-calculate the PMKs
=======================
- airolib-ng database --import essid _essidFile
- airolib-ng database --import passwd _wordList
- airolib-ng database  --batch
- airolib-ng database --export cowpatty _essid _outputFile
- aircrack-ng -r database _.cap (need handshake)



















aireplay-ng --fakeauth _0/_1 -a [BSSID’s MAC Address] -h _myAdapterMAC wlan0mon
- allow the AP to reconize this adapte	r and respond to it 

! Need fakeauth to get response
REPLAY can generate a lot of traffic on a network so that airodump can have more information

aireplay-ng --aireplay _0/_1 -b [BSSID’s MAC Address] -h _targetAdapterMAC wlan0mon

aireplay-ng --test wlan0mon
