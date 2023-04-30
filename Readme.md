# Cinebot30 w/ Diatone Mamba F740 Mk4 COB LED
## _Because someone may need it..._


GEPRC recommends their own flight controller for this frame, but as it's quite difficult to get your hands on most stuff before they get snapped up, you have to make do with what you can get.

The Cinebot30 Frame or CT-30 comes with an optional set of COB lights and if paired with the GEPRC FC, correct pad and their CLI dump, you're pretty much good to go. Other flight controllers will need a bit of tinkering but is generally straight forward.
### Setup used:
- Diatone Mamba F740 Mk4 AIO
- Betaflight 4.3/4.4

### Default PINIO

Diatone has included a preconfigured pinio setup for the target of this board and many of their other Mk4 boards.
They have configured this to allow you to control the VTX power we could just use this, however we will be leaving this as alone and will be using PINIO 3

### Betaflight CLI

Double check resource to make sure the LED_STRIP is still B03

```sh
resource
resource BEEPER 1 B02
resource MOTOR 1 C08
resource MOTOR 2 C09
resource MOTOR 3 A08
resource MOTOR 4 A09
resource MOTOR 5 B00
resource MOTOR 6 B01
resource MOTOR 7 A10
resource MOTOR 8 B04
**resource LED_STRIP 1 B03** 
resource SERIAL_TX 1 B06
resource SERIAL_TX 2 A02
resource SERIAL_TX 3 B10
resource SERIAL_TX 4 A00
resource SERIAL_TX 5 C12
resource SERIAL_TX 6 C06
resource SERIAL_RX 1 B07
resource SERIAL_RX 2 A03
resource SERIAL_RX 3 B11
resource SERIAL_RX 4 A01
resource SERIAL_RX 5 D02
resource SERIAL_RX 6 C07
resource I2C_SCL 1 B08
resource I2C_SDA 1 B09
resource LED 1 C15
resource LED 2 C14
resource SPI_SCK 1 A05
resource SPI_SCK 2 B13
resource SPI_SCK 3 C10
resource SPI_MISO 1 A06
resource SPI_MISO 2 B14
resource SPI_MISO 3 C11
resource SPI_MOSI 1 A07
resource SPI_MOSI 2 B15
resource SPI_MOSI 3 B05
resource ADC_BATT 1 C01
resource ADC_CURR 1 C03
resource PINIO 1 C02
resource PINIO 2 C00
resource FLASH_CS 1 A15
resource OSD_CS 1 B12
resource GYRO_EXTI 1 C04
resource GYRO_CS 1 A04

```

We now clear the pin from the LED_STRIP by using

```
resource LED_STRIP none
```

Now we want add BO3 to PINIO 3 and add it to the PINIO_BOX

```
resource pinio 3 BO3
set pinio_box = 0,40,41,255
```

The default PINIO_BOX with the F740 AIO Mk4 is 0,40,255,255, we want to edit the third value adding '41' where '255' used to be. This will now give us an additional USER 2 option in the modes tab of Betaflight. We now just have to add a range to USER 2 and pair it with a switch on your radio. 

We should now have a COB LED strip that we can power on and off with a simple flip of a switch!

## Big Thanks!

Whilst the information for this is already available on the internet, I wanted to make it easier for me to come back to in the future. The following people have been extremely valuable, thank you!


| Big Thanks To | 
| ------ |
| Painless360 | 
| Joshua Bardwell | 
| NordFPV |

