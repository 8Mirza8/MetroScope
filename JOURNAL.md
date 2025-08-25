---
Title: "MetroScope"
Author: "Said"
Description: "I made a decorative table made of PCB showing the live location of the trains on the M4 line in Istanbul."
Created On: "25/08/2025"
---

# August 17th: The idea came to my mind

One day, I was waiting for the metro on my way home from school, and a chart on the platform showed the average train arrival time. I wanted to make a PCB miniature of this chart. First, I did some research to see if it was possible. The Istanbul Municipality had publicly available transportation APIs, but they didn't have the metro APIs I needed for my project. So I emailed the Istanbul Municipality and requested these APIs. Until that was done, I would use my own reference values ​​in my code (like which trains arrive at which stops, when, and how often).

**Total time spent: 1.5h**

# August 18th: Writing code without APIs

I calculated the times between subway stops by dividing the distance between them by the subway's speed, then I calculated the times the subway operates. Although I couldn't find information on how many minutes the subway passes, I made an estimate. Since I don't have a PCB yet, I made a virtual emulator for myself with the Tkinter library in Python and put the stops there. I was very happy to see that there were no errors in my code, and that was it for today.

<img width="711" height="642" alt="image" src="https://github.com/user-attachments/assets/03931d3d-91cd-4909-b48b-d7013bdc389b" />
**Total time spent: 2h**

# August 20th: Pcb design

I wrote the code in Python because once I have the APIs, I'll need an internet-connected microcontroller that can access them, and I'll be using my Raspberry Pi Zero 2W board for this. There are 24 stops on the M4 line, so I'll use SMD LEDs representing these 24 stops, but I needed to figure out how to control those 24 LEDs without 24 GPIO pins. That's when I learned I could use a 74HC595. With this integrated circuit, I'd only need three GPIO pins (each IC would control eight LEDs, so I'd need three). After making the necessary connections on EasyEDA, it was time to design the PCB. I found a line map of all the metro lines on the Istanbul Municipality website. From this map, I extracted the required line shape for the M4 metro line and saved it as an SVG. Then, using this SVG file, I created a silk layer and placed my SMD LEDs at the stops on the silk layer. Then, since I was going to plug the Raspberry Pi Zero 2W into this PCB, I made a shield from the headers. After adjusting the dimensions, I drew the board outline and moved on to the routing phase. After that, I added a keyhole and my name to the PCB and saved it. My PCB was ready; now I just had to wait for the APIs.
<img width="989" height="832" alt="image" src="https://github.com/user-attachments/assets/377cf10c-99c4-4c92-832b-9823bb93361b" />
<img width="1351" height="495" alt="image" src="https://github.com/user-attachments/assets/9ef5d48e-f06e-4289-bd10-6eb5d921d033" />

# August 25th: I RECEIVED THE APIS FROM THE MUNICIPALITY!

The Istanbul Municipality contacted me and published the metro API list. I combined the ones I needed from this list (/GetLines, /GetStations, /GetDirectionsByLineIdAndStationId, /GetTimeTable, and /GetStationBetweenTime) with my old code. After a bit of tinkering and debugging, I was able to get it working successfully. All I had to do was plug my card into my PCB and try it out!

<img width="910" height="708" alt="image" src="https://github.com/user-attachments/assets/e0ea5079-d75b-45e3-936e-37ceb558d4f2" />
<img width="1126" height="377" alt="image" src="https://github.com/user-attachments/assets/bbd5491f-9e96-4f07-b216-d3a31cbaddbd" />



