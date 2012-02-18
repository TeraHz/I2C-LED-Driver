I2C LED Driver
=======

`I2C LED Driver` is a high power LED driver with i2c control and 12bit resolution.

Features
--------

*	**High maximum current**

	`I2C LED Driver` uses the National Semiconductor [LM3409/HV](http://www.ti.com/lit/ds/symlink/lm3409.pdf)
	chip, which allows for up to 5A LED current using the appropriate external power mosfet and components.

*	**High maximum voltage**

	`I2C LED Driver` can be configured with the LM3409 for 6V to 42V input voltage or the LM3409HV for
	6V to 75V input voltage

*	**i2c analog dimming**
	
	`I2C LED Driver`'s i2c bus is handled by the [MCP4725](http://www.sparkfun.com/datasheets/BreakoutBoards/MCP4725.pdf)
	12Bit Digital-to-Analog Converter. The MCP4706 and MCP4716 DACs are drop in replacements for 8 and 10 bit resolution,
	respectively. 

*	**PWM dimming** (depricated)

	`I2C LED Driver` v0.5 and before can be used for simple PWM dimming. This feature is no longer supported with v0.6
	due to the simpler and superior i2c method.

*	**Direct analog dimming** (depricated)

	`I2C LED Driver` v0.5 can be used if direct analog dimming is prefered. This feature is no longer supported. See
	i2c analog dimming. 


Programming
-------

*	**Communication via i2c bus**

	Communication is done with 4 bytes:
	* 1 byte - address
	* 2 byte - commands
	* 3 and 4 byte - registers of the 12 bits (last 4 bits are ignored)

*	**Addressing**

	The 7 bit address is composed of 1100 for first 4 bits + 3 additional bits via configurable pins. 
	On the MCP4725, you have 4 options when you order 110000X, 110001X 110010X and 110011X where X is
	set to either 0 or 1 via the external smd jumper. 

	

	Refer to the [datasheet](http://www.sparkfun.com/datasheets/BreakoutBoards/MCP4725.pdf) for more information.
	
	A library will be made available in the near future.
		

Hardware
-------

*	**CAD software**
	
	The board and schematic are being developed using the the free version of [Eagle PCB](http://www.cadsoftusa.com).
	set to either 0 or 1 via the external smd jumper. 

	

*	**Limitations**

	Since only 3 bits of the address on the MCP4725 are configurable, that means only 8 driver boards can sit on a 
	i2c bus at one given time. If more than 8 driver boards are required a simple solution like using the
	[MAX4562](http://www.maxim-ic.com/datasheet/index.mvp/id/2019) for up to 3 more sets of 8 boards, or the
	[MAX4572](http://www.maxim-ic.com/datasheet/index.mvp/id/1974) for up to 7 more sets of 8 boards can be used.

	More about this setup can be read in the Maxim [App Note 955](http://pdfserv.maxim-ic.com/en/an/AN955.pdf).


Getting a `I2C LED Driver`
-------

*	**PCB**

	There are plenty fab house in China that offer PCB services for very reasonable price.
	[Seeed Studio](http://www.seeedstudio.com/depot/fusion-pcb-service-p-835.html?cPath=185) 
	will make 10 boards for a little over $10.
	[iTead Studio](http://iteadstudio.com/store/) has very similar offer.

*	**Power Supply**

	`I2C LED Driver` is a switch mode regulator based buck driver that is a little more forgivin in the amount of 
	input voltage it can handle, compared to the LED dropout voltage, however try to keep the total forward voltage
	of the LEDs not more than 10V under the input voltage. The closer the less work the regulator has to do.

*	**Bill Of Materials**

	The BOM files are for 1A, 48V input setup. It is highly recommended that you go throgh the component selection
	part of the [datasheet](http://www.ti.com/lit/ds/symlink/lm3409.pdf) to ensure that you have selected the appropriate
	components for your setup.
	Mouser project for the 1A, 48V setup can be found [here](http://www.mouser.com:80/ProjectManager/ProjectDetail.aspx?AccessID=0d7c3dba77).


License
-------

Attribution-NonCommercial-ShareAlike 3.0  (CC BY-NC-SA 3.0)

*	**You are free:**


	* to Share - to copy, distribute and transmit the work
	* to Remix - to adapt the work

*	**Under the following conditions:**

	* Attribution - You must attribute the work in the manner specified by the author or licensor
	(but not in any way that suggests that they endorse you or your use of the work).
	* Noncommercial - You may not use this work for commercial purposes.
	* Share Alike - If you alter, transform, or build upon this work, you may distribute the resulting
	work only under the same or similar license to this one.

*	**With the understanding that:**

	* Waiver - Any of the above conditions can be waived if you get permission from the copyright holder.
	* Public Domain - Where the work or any of its elements is in the public domain under applicable law,
	that status is in no way affected by the license.
	* Other Rights - In no way are any of the following rights affected by the license:
		- Your fair dealing or fair use rights, or other applicable copyright exceptions and limitations;
		- The author's moral rights;
		- Rights other persons may have either in the work itself or in how the work is used, such as publicity or privacy rights.

For more details about the license visit [http://creativecommons.org/licenses/by-nc-sa/3.0/](http://creativecommons.org/licenses/by-nc-sa/3.0/)

