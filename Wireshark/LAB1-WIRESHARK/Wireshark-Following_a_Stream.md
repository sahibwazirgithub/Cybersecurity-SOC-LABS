## WIRESHARK STREAM:
With wireshark we have a feature to follow a specific stream of data.\
There can be different types of streams e.g tcp or http stream.\
When it comes to tcp based protocols the client and server maintain a specific session.\
when we look at the stream we are looking at the entire communication between two devices.

## EXAMPLE:1 (Following a TCP stream):
select any tcp based protocol packet-->right click-->follow-->TCP stream a dialogue box with the packet involved in the session opens up.\
<img width="1920" height="1080" alt="Screenshot 2025-12-26 180509" src="https://github.com/user-attachments/assets/acf5846c-f8ed-407b-a7e2-9354d4b822c0" />

The light red represents client packet and light blue represent server packet.\
we can also see the no.of client packets and server packets on the bottom left of the dialogue box.



## EXAMPLE:2 (Following a HTTP stream)
select any http based protocol packet-->right click-->follow-->HTTP stream a dialogue box with the packet involved in the session opens up.\
<img width="1920" height="1080" alt="Screenshot 2025-12-26 180949" src="https://github.com/user-attachments/assets/d8d872cd-4b23-4188-9b87-bca4f6a369be" />

