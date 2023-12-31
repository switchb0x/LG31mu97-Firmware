# LG 31MU97 Firmware Repair

## Background

If your LG 31MU97-B monitor is experiencing issues, it's possible that the problem is related to the IC205 chip on the mainboard. This chip, identified as an MX25L8006 series part, is a common culprit for problems in this monitor model.

To address this issue, you can consider reprogramming the EEPROM chip using a CH341A SPI Programmer with SOP8 clip. The following steps outline the process:

## Firmware Repair Steps

1. **Obtain the Necessary Hardware:**
   - Purchase a CH341A SPI Programmer with a SOP8 clip. You can find these on various online marketplaces. Here is an example of one on amazon:
![image](https://github.com/switchb0x/LG31mu97-Firmware/assets/65792132/002a8b0f-83f2-4429-94de-3673cba190f3)

2. **Connect the Hardware:**
   - Plug the CH341A programmer into a USB port on your computer.
   - Attach the SOP8 clip to the programmer.
   - Connect the SOP8 clip to the EEPROM IC205 on the monitor's mainboard.

3. **Perform the Reprogramming:**
   - On your Linux computer, open a terminal and run the following commands:
   
   ```bash
   $ sudo flashrom --programmer ch341a_spi -r backup.bin
   ```

This command backs up the existing firmware to "backup.bin."

Copy code
```
$ sudo flashrom --programmer ch341a_spi -w lg31mu97.bin
```
This command writes the new firmware (downloaded from here) to the EEPROM.

Note: Be cautious about the voltage supplied by the CH341A programmer. It operates at 5V, which may be higher than the EEPROM's required voltage of 3.3V. Consider modifying the CH341A to use the correct voltage if necessary.

Verify the Repair:

If the reprogramming process completes without errors, you can attempt to power on the monitor. Check for any improvements in its functionality.

**Alternative Solution:**
If you encounter difficulties with reprogramming or wish to avoid potential risks to the EEPROM, you can seek professional assistance. Pete's Computers (Manchester, UK) is one option for reprogramming the IC205 chip.

## GUI programmer approach
Using NeoProgrammer (GUI-based Option)
If you prefer a GUI-based approach, you can use NeoProgrammer, a graphical programming tool for EEPROM chips. Follow these steps:

**Download NeoProgrammer:**
![image](https://github.com/switchb0x/LG31mu97-Firmware/assets/65792132/a5884c34-f55f-4192-b262-32a525cb01a9)

Download NeoProgrammer from the official website: NeoProgrammer.
Connect the Hardware:

Ensure your CH341A programmer with the SOP8 clip is connected to the EEPROM IC205 on the monitor's mainboard, **leave the monitor unplugged from all power**. The device is a 25x (SPI NOR FLASH) so place the breakout board as indicated on the programmer.

Launch NeoProgrammer on your computer. If the clip is attached to the prom chip, you can selecte detect within the neoprogrammer and it should pull up a few options. select the same as the flash chip indicates (the part number is laser-printed directly on the flash chip).
![image](https://github.com/switchb0x/LG31mu97-Firmware/assets/65792132/d20354a1-5cb8-44c7-bc1e-1ff93e511d02)


In NeoProgrammer, configure the settings for your EEPROM chip (MX25L8006EM2I-12G).
Read and Write Firmware:

Use NeoProgrammer to read the existing firmware from the EEPROM, adn save it to a file. Erase the flash module. Load the binary from this repo into neoprogrammer and select program. Make sure to verify (the icon with the = sign). 

Verify the Repair:
Fully power down the device, and be sure to watch the screen (not hte red led on hte power button) to verify that it works again.

Unfortunately, I cannot afford the time to help people diagnose nad repair their devices; however, i'll leave comments enables so that others in the  community can help. Good luck.
