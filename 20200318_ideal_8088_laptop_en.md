# Building the Ideal Laptop Episode One (8088 & IBM PC)

Originally posted on March 18, 2020:
https://www.mydigit.cn/thread-133380-1-1.html

Unexpectedly, by the time I posted, it was already mid-March. This laptop project started in mid-January, and two months have flown by 😓. However, the pandemic is not over yet, so there's still time to continue researching. Last time, I made a mini card computer for the IBM XT. It was originally planned for use in a laptop, but due to being busy with work, it was put on hold, and now I've taken another step forward.

![img0](images\20200318_00.jpg)

This time, I'm building a laptop compatible with the IBM PC.

## 【Configuration Introduction】
CPU: 8088 (NEC V20)
Memory: 640KB
Hard Drive: Option for CF card/DiskOnChip as storage device
Display: 1024x768 TFT (LED backlight) / Graphics card compatible with CGA/VGA
Peripherals: Floppy drive, serial port, keyboard, standard ISA expansion
System: DOS6.22

## 【Preparation】

First, we've confirmed the configuration plan, next comes the casing. I considered several options for the casing: first was acrylic, second was aluminum alloy CNC machining, third was using another laptop's casing, and fourth was custom injection molding. After comprehensive consideration, I chose the third option, as there might still be changes later.

There are many models of finished laptops, but it's easier to choose after setting a few fixed conditions:
1. Thickness: It needs to be thick (vintage components are taller, and I also need to make a multilayer circuit board).
2. Minimal modification: Ideally, it should have a native floppy drive slot.
3. Commonly available casings: This means the production time needs to be closer to the present.
4. Appearance: Personally, I prefer those with consistent thickness from front to back, meaning no tapering, more squared, with clear edges.

Actually, after specifying that it must have a floppy drive slot and be produced relatively recently, the options narrowed down. Business laptops from DELL, HP, Fujitsu generally include a floppy drive. However, while searching, I stumbled upon a Toshiba J60, a machine with a Core Duo CPU that still includes a floppy drive, and it's thick, so it meets all the basic requirements. I chose it.
This is what the TOSHIBA J60 looks like:

![img1](images\20200318_01.jpg)

Having chosen the casing, the next steps are some preparatory works:
1. Modify the LCD backlight
2. Make an LVDS screen cable
3. Minor modifications to the casing
4. Measure the internal space, hole positions, and determine the motherboard size.

First step: Modifying the LCD backlight. I tested the original LCD backlight, which needed 1A of current! I estimate my entire system wouldn't even need 1A, so modification was necessary.
![img2](images\20200318_02.jpg)

I chose a 5V LED driver board, which was not easy to find, but still available.
![img3](images\20200318_03.jpg)

I didn't take detailed pictures of the modification process, as the main focus is on making the vintage computer. After testing, this LED backlight needed 0.5A of current, half of the original, but still felt high.
After lighting up the screen, I found the brightness too high, even glaring during the day, so I adjusted the driver board's feedback resistor to the lowest brightness, which still felt very bright.
Thus, after re-testing, the current needed was only 0.1A! That's 100mA for a brightness higher than the original 1A current. So, this modification was necessary and greatly helps with battery life.
![img4](images\20200318_04.jpg)

After the modification, I began testing. Due to the camera's sensitivity to light, the actual brightness is much higher than it appears in the pictures (this is at 100mA current).

Second step, making the LVDS screen cable.
I found out this screen uses a 30P single 6-bit LVDS, so I bought a cable, shielded it with tape, and the screen cable was pretty much ready.
![img5](images\20200318_05.jpg)

Third step, casing modifications mainly involved removing unnecessary support points. Then, I planned to install a small LCD screen to display current and keyboard status. First, I sketched the outline needed for the LCD screen and drilled a rough shape.
![img6](images\20200318_06.jpg)

![img7](images\20200318_07.jpg)

Then... I carved it out bit by bit with a craft knife. Regardless,

 except for a scratch I made, everything fit perfectly.
![img8](images\20200318_08.jpg)
![img9](images\20200318_09.jpg)

Fourth step, drafting the design, determining the motherboard outline and hole positions to finalize the PCB size.

Original motherboard:
![img10](images\20200318_10.jpg)

Drafted hole positions:
![img11](images\20200318_11.jpg)

## 【Motherboard Fabrication】

With the preparation done, it's time to start designing the motherboard based on the previously mentioned configuration requirements.

1. Designing the motherboard/graphics card LVDS driver
The motherboard power section, each power route has current detection for easy consumption testing.
![img12](images\20200318_12.jpg)
IO decoding and UART
![img13](images\20200318_13.png)
FDC
![img14](images\20200318_14.png)
Other parts of the drawings are too many, so I've put them all in the attachment for reference.

2. Designing the PCB. Routing was a headache, but thankfully, the board was big enough for easy layout.
![img15](images\20200318_15.jpg)
3D preview, not all library components rendered
![img16](images\20200318_16.jpg)
After waiting 5 days, the boards finally arrived. I couldn't wait to start soldering.

First, soldering the graphics card:
![img17](images\20200318_17.jpg)
Another view from the back
![img18](images\20200318_18.jpg)
Motherboard soldering:
![img19](images\20200318_19.jpg)
Checking for cold solder joints under a magnifying glass:
![img20](images\20200318_20.jpg)
Here came the most unfortunate event of the entire project. After soldering for 6 hours, the system didn't work. I spent another two hours desoldering components one by one for troubleshooting without finding the issue. It was late at night, so I had to wait until the next day to continue.

The next day, with no other option, I had to cut all the lines and use the minimal system approach to slowly eliminate potential issues. Finally, I found the problem was that the CPU socket was mirrored. I had to make a new board.
I decided to change the color of the new board too. After waiting another 4 days, I could happily start soldering again.
![img21](images\20200318_21.jpg)

The CPU board used was the one made last year, very stable:
![img22](images\20200318_22.jpg)

The completed soldering looked like this, and I'll introduce it after installing the modules. Although the board looks sparse, it uses the ISA bus, so many other modules can be installed.
![img23](images\20200318_23.jpg)

![img24](images\20200318_24.jpg)

Power section, keyboard IO part:
![img25](images\20200318_25.jpg)

Battery:
![img26](images\20200318_26.jpg)

External ISA interface:
![img27](images\20200318_27.jpg)

CF card and floppy drive:
![img28](images\20200318_28.jpg)

The manual part of the entire project is almost finished:
![img29](images\20200318_29.jpg)

I also bought a new English keyboard:
![img30](images\20200318_30.jpg)

Comparing the two:
![img31](images\20200318_31.jpg)

Then powering on, booting up! Here it's booting from the CF card, with DOS 6.22 installed.
The BIOS used is open source, which reduced a lot of work.
![img32](images\20200318_32.jpg)

The small LCD screen is mainly to assist me with writing the keyboard scanning program, as the keyboard driver is not yet complete. Additionally, the LCD screen will primarily display battery life, total power consumption, etc.
![img33](images\20200318_33.jpg)

Since this post mainly covers the making process, I plan to write another post specifically for testing and usage later.
I've attached the drawings for reference. The BIOS was already uploaded in a previous post and hasn't been changed.

[Drawings.rar (72.84 KB)](attachment\20200318_blueprint.rar)

A few days have passed since completing the post, and I've already started working on a 7-inch portable laptop. It will be more integrated but also more stable. I don't only research vintage 8088 computers; I enjoy DIY laptops, and platforms like 915PM, 945PM, PM965, PM45 are all within my DIY range. It's just that drawing takes a lot of time. If there are friends who like DIY, we can research together.

End of post