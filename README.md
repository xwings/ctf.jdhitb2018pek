Date: 1st - 2nd Nov 2018
Event: First Ever JD-HITB, Beijing.
Description: XCTF Grand Final, 2018

Organization:
- theshepherdlab.org, a research lab by JD Security
- hackersbadge.com, a free and opensource badge making lab
- hackinthebox.org, that super hacking conference

Ffinally I decided we should have a "hardware" CTF challange. Considering this is China,the exposure of the team have more exposure to hardware hacking.

Lets start with brief history of Hack In The Box Badge.

HITB2018AMS - First time ever i work with @WhiteA10n3 togeather with @klks84 for the badge. Using STMF103 and its a development board with a OLED screen. programmerable with Arduino
HITB2018SG - Still using STMF103, this time we make it with TFT screen, still programmerable with Arduino

After the great experience making a RESUABLE badge (not for conference ony). @WhiteA10n3 and me decided to go one step further, make a router into a badge.

The idea is, use a MTK series with openWRT. We found a MTK7688 kit and decided to get in to board drawing and making custom firmware.

Here, is the blank board

![alt text](https://raw.githubusercontent.com/xwings/ctf.jdhitb2018pek/master/pic/blankboard.jpg)

We also decided to to make a small screen just to show SSID and Password. No more TFT this time.

Finally, making a CTF chanllange into the badge. Must not be too hard, or too easy. 

Challange 0:

Figuring out we have 3 leds on the badge and we able making the two of the led blink (having hard time tuning the GPIO). 0 and 1 for each LED Windows seems to be really working fine.

The plan is, making CTF player goto the lunch area. Have food and find the challange. 

Note: Making CTF player walk to lunch area is a great deal!

```
0. LCD screen will show "See Me at Lunch Area, 12 Noon till 2PM"

1. Badge will be distributed
2. BOOT
3. Wait till 12 Noon
4. Goto Lunch Area
5. Badge will scan for SSID at lunch place with SSID theshepherdlab.io
6. Monitor the blink
8. First GreatwWall Window is 0 as in binary, second GreatWall windows 1 as in binary
9. Every 8 bit stop 1 second, complete stop 10 seconds 
10. Flag in HEX
11. After conversin to ascii, it is jdhitb2018

("jdhitb2018".encode("hex"))
6a646869746232303138
```

Challange 1:

```
0. Announcement: Show me your soldering skillz

Tips:
1. login as admin and you will see the flag
2. flag print will be from (sha1(therootpassword).md5(/etc/passwd))
3. part of FLASH strings, only shows in the dark side (breed bootloader)


root password is : rt6855a-spi.0
flag (sha1(rt6855a-spi.0))+(md5(/etc/passwd))
```

challange one is fun, we manage to plant some trip into the challange
- Simple soldering skill required.
- By default UART with root is enabled. But you should not change the root passowrd. It will break the MD5
- UART with a twist, we switched the VCC logo with ground.

******
Update: 6th Nov 2018, 1500 by changing the root password, it will work too. *Design Flaw* 
******

We do have teams burned their board, changes the root password and come to me and ask for reflash and maybe get their finger burned.

Overall, we do receive very good Feedback on my very first hardware hacking CTF challange. We do hope we can work more closely with XCTF in the future.


![alt text](https://raw.githubusercontent.com/xwings/ctf.jdhitb2018pek/master/pic/allbadge.jpg)
