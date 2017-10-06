## tshark
- Dump and analyze network traffic
- Wireshark-based tool very similar to tcpdump (console)

### Decode traffic 802.11 traffic (better alternative: use airdecap-ng):

Notes:
1. You can use either the PWD or the PSK form to provide the 802.11 key.
2. It seems to decode 802.11 frames correctly when directing the output to stdout. 
    But it does not work when writing to a file ("-w <new capture file>"). 
    When reading output.pcap with tcpdump it displays only 802.11 encoded frames
    
`tshark -r Wifi_rogue_AP.pcap -o wlan.enable_decryption:TRUE -o "uat:80211_keys:\"wpa-psk\",\"9ac29c094d7dca4726e0220e39ee3f59985918662b43c86b95b506d62a150c77\"" -w output.pcap
tshark -r Wifi_rogue_AP.pcap -o wlan.enable_decryption:TRUE -o "uat:80211_keys:\"wpa-pwd\",\"princess:FirstTargetBank \"" -w output.pcap`


### Filter pcap based on wireshark-like filters:
Read original capture "original.pcap" and save only packets coming from/going to IP 192.168.100.2 to "local_traffic.pcap

`tshark -r original.pcap -Y "ip.addr eq 192.168.100.2" -w local_traffic.pcap`

Leave only outbound traffic (assuming your IP is 192.168.10.10):

`tshark -r original.pcap -Y "ip.src eq 192.168.10.10" -w local_traffic.pcap`
