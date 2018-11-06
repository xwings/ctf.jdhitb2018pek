Date: 1st - 2nd Nov 2018
Event: First Ever JD.COM + Hack In The Box, Beijing.
Desc: XCTF Grand Final

Organization:
- theshepherdlab.org, a research lab from JD.COM
- hackersbadge.com
- hackinthebox.org

Ffinally I decided we should have a "hardware" CTF challange. Considering this is China,the exposure of the team should be more "hardware".

Lets start with brief history of Hack In The Box Badge.

HITB2018AMS - First time ever i work with @WhiteA10n3 togeather with @klks84 for the badge. Using STMF103 and its a development board with a OLED screen. programmerable with Arduino
HITB2018SG - Still using STMF103, this time we make it with TFT screen, still programmerable with Arduino

After the great experience making a RESUABLE badge (not for conference ony). We decided to go one step further, a badge with router function.

Using a MTK chip with OpenWRT was the idea. We found a MTK7688 kit and we decided to get in to board drawing and making custom firmware.


![alt text](https://raw.githubusercontent.com/xwings/ctf.jdhitb2018pek/master/pic/blankboard.jpg)

We also decided to to make a small screen just to show SSID and Password

Finally, making a CTF chanllange into the badge.

Challange 0:

Figuring out we have 3 leds onthe badge, making the two of the led blink. 0 and 1 for each LED seems to be really cool. 

Note: Making CTF player walk to lunch area is a great deal !

```
0. LCD screen will show "See Me at Lunch Area 12 Noon till 2PM"

1. Badge will be distributed
2. BOOT
3. Wait till 12 Noon
4. Goto Lunch Area
5. Badge will scan for SSID at lunch place with theshepherdlab.io
6. Monitor the blink, 8bit stop 3 seconds after finish stop 10 secobds. 
8. First GreatwWall Window is 0 as in binary, second GreatWall windows 1 as in binary
9. 8 bit stop 1 second, complete stop 10 seconds 
10. that will be your flag, in hex
11. After conversin to ascii, it is jdhitb2018

("jdhitb2018".encode("hex"))
6a646869746232303138

flag 6a646869746232303138
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
- By default UART withroot is enabled. But you should not change the passowrd. It will break the MD5
- UART with a twist, we switched the VCC logo with ground.

We do have teams burned their board, changes the root password and come to me and ask for reflash and maybe get their finger burned.

Overall, we go received a very good Feedback on my very first hardware hacking CTF. I do hope I can make more hardware CTF in the future.


![alt text](https://raw.githubusercontent.com/xwings/ctf.jdhitb2018pek/master/pic/allbadge.jpg)
