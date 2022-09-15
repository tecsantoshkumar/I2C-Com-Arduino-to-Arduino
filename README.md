# Introduction

I2C communications have become the de facto method of communicating between microcontrollers, microcomputers and a variety of integrated circuits and sensors. It has been around since 1982 and was originally developed for use in television receivers.

## I2C Communications

I2C is a serial protocol used on a low-speed 2-wire interface. It was originally developed by **Phillips in 1982 to allow integrated circuits within television receivers to communicate** with one another.

Times have changed, Phillips is now NXP and I2C has become a communication standard that is supported by virtually every major semiconductor manufacturer.

I2C is an abbreviation for “Inter-Integrated Circuit”. It is also called “IIC” or ‘I squared C”.

## Uses and Limitations

I2C is used with microcontrollers like the Arduino and with microcomputers like the Raspberry Pi. Many displays and sensors interface to their host controller using I2C.

I2C does have several limitations however. It is not particularly fast, although for most of its intended uses it is plenty fast enough.

I2C can only be used over short distances, after all, it was originally meant to communicate between integrated circuits on the same printed circuit board. The maximum distance of reliable transmission decreases as the speed increases, at the slowest speed (100 Kbaud or a clock rate of 100 KHz) the maximum distance is about a metre.

## I2C Speeds

The original I2C bus had a maximum speed of 100 KHz. Most common applications still use this speed, as it is quite sufficient for transferring data from sensors and to simple displays.

I2C and has some higher speed modes. Not all I2C devices support these modes:

1. **Fast Mode** – This has a maximum clock speed of 400 KHz.

2. **Hi-Speed Mode** – A maximum clock frequency fo 3.4 MHz

3. **Ultra Fast Mode** – Maximum clock frequency of 5 MHz

On an I2C bus it is the master that determines the clock speed.

## How I2C Works

An I2C bus has two signals, along with a power and ground connection.

![I2C](https://user-images.githubusercontent.com/62633516/190425896-a3b4fcb4-1925-4569-a08c-9228c0054f2c.png)

### The two signal lines are as follows:

1. **DSA** - This is the bidirectional data line.
2. **DSC** - This is the clock signal.

There are two pull-up resistors attached to each signal line, they pull the bus up to the supply voltage when it is inactive.

Note that the supply voltage is not standard, it can be either 3.3 or 5-volts. It can also be a lower voltage for some high-speed I2C implementations.

This difference in supply voltages can cause issues when you are interfacing I2C devices that use different logic levels. We will discuss this more in a future article when I show you how to interface a Raspberry Pi (3.3-volt logic) with an Arduino Uno (5-volt logic).

There are two types of devices that can be interfaced to the I2C bus – Masters and Slaves.

The Master device controls the bus and supplies the clock signal. It requests data from the slaves individually.  There can be more than one master device on the bus but only one can be the active master at any given moment.

The master devices do not have an address assigned to them.

Slave devices do have an address, and this address needs to be unique on the bus. They use a 7-bit addressing scheme, so up to 128 slaves can be on one I2C bus. In real life this large collection of devices is never used, it is rare to see over a dozen I2C devices on one bus.

A newer, 10-bit addressing scheme has been implemented, it is backward-compatible with the existing 7-bit addressing method.

Commercial I2C devices are allocated I2C address by NXP, who maintain the bus specifications. Although I2C has been open source since 2006 there is a fee charged for obtaining a slave address from NXP.  No fee is required for master devices, or for devices that are not meant for commercial manufacture.

Some I2C devices are assigned multiple addresses, usually variances in the lower address bits. These devices can be manually configured for different addresses, allowing multiple devices of the same type to be used on a single I2C bus.

## Other I2C Derivatives

There are other buses that have been derived from the I2C bus, and which are in many ways compatible with I2C.

**TWI** – The Twin Wire Interface is virtually identical to the I2C bus. This is actually the bus that the Arduino uses, TWI was developed when the I2C bus was not open source and Atmel did not want to risk a trade name violation. The only major difference between TWI and I2C is that TWI does not support an advanced technique called “clock stretching”.
**SMBus** - is another I2C equivalent bus, developed by Intel. Like TWI it supports most I2C features.

In a future article I will explain how the data on the I2C bus is structured. But now we have some basic I2C information, enough to start experimenting.

Introduction
I2C communications have become the de facto method of communicating between microcontrollers, microcomputers and a variety of integrated circuits and sensors. It has been around since 1982 and was originally developed for use in television receivers.


Although we have used many I2C sensors and displays in previous articles we have not actually looked into how I2C works and how it can be used to communicate between microcontrollers.

Today we will correct that and learn more about I2C. We’ll also see how it can be used to exchange information between two Arduinos and how it can be used to allows one Arduino to control another one.

I2C Part 1-Using 2 Arduinos

This will be the first of four articles on I2C. In future articles we will see how we can build our own I2C devices, how to interface a Raspberry Pi and an Arduino using I2C and how to do some advanced I2C configurations, including using multiple masters on one I2C bus.

Let’s get started!

I2C Communications
I2C is a serial protocol used on a low-speed 2-wire interface. It was originally developed by Phillips in 1982 to allow integrated circuits within television receivers to communicate with one another.

Times have changed, Phillips is now NXP and I2C has become a communication standard that is supported by virtually every major semiconductor manufacturer.

I2C is an abbreviation for “Inter-Integrated Circuit”. It is also called “IIC” or ‘I squared C”.

Uses and Limitations
I2C is used with microcontrollers like the Arduino and with microcomputers like the Raspberry Pi. Many displays and sensors interface to their host controller using I2C.

I2C does have several limitations however. It is not particularly fast, although for most of its intended uses it is plenty fast enough.

I2C can only be used over short distances, after all, it was originally meant to communicate between integrated circuits on the same printed circuit board. The maximum distance of reliable transmission decreases as the speed increases, at the slowest speed (100 Kbaud or a clock rate of 100 KHz) the maximum distance is about a metre.

I2C Speeds
The original I2C bus had a maximum speed of 100 KHz. Most common applications still use this speed, as it is quite sufficient for transferring data from sensors and to simple displays.

I2C and has some higher speed modes. Not all I2C devices support these modes:

Fast Mode – This has a maximum clock speed of 400 KHz.
Hi-Speed Mode – A maximum clock frequency fo 3.4 MHz
Ultra Fast Mode – Maximum clock frequency of 5 MHz
On an I2C bus it is the master that determines the clock speed.

How I2C Works
An I2C bus has two signals, along with a power and ground connection.

I2C Bus Communications

The two signal lines are as follows:

SDA – This is the bidirectional data line.
SCL – This is the clock signal.
There are two pull-up resistors attached to each signal line, they pull the bus up to the supply voltage when it is inactive.

Note that the supply voltage is not standard, it can be either 3.3 or 5-volts. It can also be a lower voltage for some high-speed I2C implementations.

This difference in supply voltages can cause issues when you are interfacing I2C devices that use different logic levels. We will discuss this more in a future article when I show you how to interface a Raspberry Pi (3.3-volt logic) with an Arduino Uno (5-volt logic).

There are two types of devices that can be interfaced to the I2C bus – Masters and Slaves.

The Master device controls the bus and supplies the clock signal. It requests data from the slaves individually.  There can be more than one master device on the bus but only one can be the active master at any given moment.

The master devices do not have an address assigned to them.

Slave devices do have an address, and this address needs to be unique on the bus. They use a 7-bit addressing scheme, so up to 128 slaves can be on one I2C bus. In real life this large collection of devices is never used, it is rare to see over a dozen I2C devices on one bus.

A newer, 10-bit addressing scheme has been implemented, it is backward-compatible with the existing 7-bit addressing method.

Commercial I2C devices are allocated I2C address by NXP, who maintain the bus specifications. Although I2C has been open source since 2006 there is a fee charged for obtaining a slave address from NXP.  No fee is required for master devices, or for devices that are not meant for commercial manufacture.

Some I2C devices are assigned multiple addresses, usually variances in the lower address bits. These devices can be manually configured for different addresses, allowing multiple devices of the same type to be used on a single I2C bus.

Other I2C Derivatives
There are other buses that have been derived from the I2C bus, and which are in many ways compatible with I2C.

TWI – The Twin Wire Interface is virtually identical to the I2C bus. This is actually the bus that the Arduino uses, TWI was developed when the I2C bus was not open source and Atmel did not want to risk a trade name violation. The only major difference between TWI and I2C is that TWI does not support an advanced technique called “clock stretching”.
SMBus is another I2C equivalent bus, developed by Intel. Like TWI it supports most I2C features.
In a future article I will explain how the data on the I2C bus is structured. But now we have some basic I2C information, enough to start experimenting.

## Arduino Wire Library
The Arduino has a built-in library for working with I2C called the Wire Library. It makes it very easy to communicate on the I2C bus, and it can configure the Arduino to become either a master or a slave.

The Wire library has several useful functions for working with I2C.

1. **begin()** – This initiates the library and sets up the Arduino to be either master or slave.
2. **requestFrom()** – This function is used by the master to request data from a slave.
3. **beginTransmission()** – This function is used by the master to send data to a specified slave.
4. **endTransmission()** – This function is used by the master to end a transmission started with the beginTransmission function.
5. **write()** – Used by both master and slave to send data on the I2C bus.
6. **available()** – Used by both master and slave to determine the number of bytes in the data they are receiving.
7. **read()** – Reads a byte of data from the I2C bus.
8. **SetClock()** – Used by the master to set a specific clock frequency.
9. **onReceive()** – Used by the slave to specify a function that is called when data is received from the master.
10. **onRequest()** – Used by the slave to specify a function that is called when the master has requested data.

## Arduino I2C Connections

The SDA and SCL connections for I2C are different between Arduino models. The experiments I’m about to show you were done using two Arduino Unos, but you can use other models of the Arduino providing you change the pins accordingly.

I’ve put together a chart to help you get it figured out. It includes some common Arduino boards, as well as a few of the discrete chips.  The pinouts for the chips I list (ATTiny and ATmega328P) are with the DIP package, not the surface-mount ones.

<table style="height: 307px;" width="768">
<tbody>
<tr style="background-color: #6495ed; color: #ffffff;">
<td><span style="font-weight: 400;">Arduino Board or Chip</span></td>
<td><span style="font-weight: 400;">SDA</span></td>
<td><span style="font-weight: 400;">SCL</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Uno</span></td>
<td><span style="font-weight: 400;">A4</span></td>
<td><span style="font-weight: 400;">A5</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Mega2560</span></td>
<td><span style="font-weight: 400;">20</span></td>
<td><span style="font-weight: 400;">21</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Nano</span></td>
<td><span style="font-weight: 400;">A4</span></td>
<td><span style="font-weight: 400;">A5</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Pro Mini</span></td>
<td><span style="font-weight: 400;">A4</span></td>
<td><span style="font-weight: 400;">A5</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Leonardo</span></td>
<td><span style="font-weight: 400;">2</span></td>
<td><span style="font-weight: 400;">3</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">Due (has two I2C)</span></td>
<td><span style="font-weight: 400;">20 + SDA1</span></td>
<td><span style="font-weight: 400;">20 + SCL1</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">ATTiny85 &amp; ATTiny45</span></td>
<td><span style="font-weight: 400;">5</span></td>
<td><span style="font-weight: 400;">7</span></td>
</tr>
<tr>
<td><span style="font-weight: 400;">ATmega328P</span></td>
<td><span style="font-weight: 400;">27</span></td>
<td><span style="font-weight: 400;">28</span></td>
</tr>
</tbody>
</table>

Some Arduino Uno clones have separate SDA and SCL pins and you can use them instead of the two analog pins if you wish. They are internally connected to the same place.

Note that the Arduino Due actually has two I2C ports.

Also, be aware that there are some incorrect hookup diagrams on the internet for the Pro Mini. Use the two analog pins, A4 and A5, as shown in the table above.

## I2C Between 2 Arduino’s

For our first experiment we will hoo two Arduinos together and exchange data between them. One Arduino will be the master, the other will be the slave.

I’m using two Arduino Unos, but you can substitute other Arduino’s if you don’t have two Unos. Use the previous chart for the connections.

## Hooking up 2 Arduino’s
Here is how I connected my two Arduino Unos together:

![i2c-arduino](https://user-images.githubusercontent.com/62633516/190429888-37f3d03b-7f45-4645-83e1-3078bb8ec884.JPG)

It is quite a simple hookup, essentially you just tie the ground and the two I2C pins together.

One thing to be aware of is that my diagram does not show the use of pull-up resistors, I found that everything seemed to work correctly without them.  However, you might want to include them, especially if you experience errors or intermittent operation.

To hook up some pull-up resistors attache a couple of 10k resistors to the SDA and SCL lines. Attach the other end to the 5-volt output on one of the Arduino’s.

## Master Demo Sketch
Here is the sketch that will be used on the Arduino that you have designated as being the master.

``` 
/*
  I2C Master Demo
  i2c-master-demo.ino
  Demonstrate use of I2C bus
  Master sends character and gets reply from Slave
*/

// Include Arduino Wire library for I2C
#include <Wire.h>

// Define Slave I2C Address
#define SLAVE_ADDR 9

// Define Slave answer size
#define ANSWERSIZE 5

void setup() {

  // Initialize I2C communications as Master
  Wire.begin();
  
  // Setup serial monitor
  Serial.begin(9600);
  Serial.println("I2C Master Demonstration");
}

void loop() {
  delay(50);
  Serial.println("Write data to slave");
  
  // Write a charatre to the Slave
  Wire.beginTransmission(SLAVE_ADDR);
  Wire.write(0);
  Wire.endTransmission();
    
  Serial.println("Receive data");
  
  // Read response from Slave
  // Read back 5 characters
  Wire.requestFrom(SLAVE_ADDR,ANSWERSIZE);
  
  // Add characters to string
  String response = "";
  while (Wire.available()) {
      char b = Wire.read();
      response += b;
  } 
  
  // Print to Serial Monitor
  Serial.println(response);
}
```

As with all I2C sketches, we start by including the Wire library.

Next we define a few constants to represent the I2C address of the slave and the number of bytes of data that we expect to retrieve from it.

In the Setup we initialize the I2C communications as a master. We know it is a master as there is no address parameter in the begin function.  We also setup a serial monitor and print a line of text to it.

Now to the Loop.

We start with a tiny time delay, mostly to slow things down enough so that we can read the display on the serial monitor.

Next we use the beginTransmission function to send data to the slave. In this case the data we send is just a number zero.  We finish sending with a call to the endTransmission function.

Next we request some data back from the slave using the requestFrom function.

After that we formulate a response string by reading the data, a byte at a time, from the slave.

We print the details of what we are doing and of the data we receive to the serial monitor.  And then we finish the Loop and do it all over again.

## Slave Demo Sketch
Now onto the sketch used by the slave.

```
/*
  I2C Slave Demo
  i2c-slave-demo.ino
  Demonstrate use of I2C bus
  Slave receives character from Master and responds
*/

// Include Arduino Wire library for I2C
#include <Wire.h>

// Define Slave I2C Address
#define SLAVE_ADDR 9

// Define Slave answer size
#define ANSWERSIZE 5

// Define string with response to Master
String answer = "Hello";

void setup() {

  // Initialize I2C communications as Slave
  Wire.begin(SLAVE_ADDR);
  
  // Function to run when data requested from master
  Wire.onRequest(requestEvent); 
  
  // Function to run when data received from master
  Wire.onReceive(receiveEvent);
  
  // Setup Serial Monitor 
  Serial.begin(9600);
  Serial.println("I2C Slave Demonstration");
}

void receiveEvent() {

  // Read while data received
  while (0 < Wire.available()) {
    byte x = Wire.read();
  }
  
  // Print to Serial Monitor
  Serial.println("Receive event");
}

void requestEvent() {

  // Setup byte variable in the correct size
  byte response[ANSWERSIZE];
  
  // Format answer as array
  for (byte i=0;i<ANSWERSIZE;i++) {
    response[i] = (byte)answer.charAt(i);
  }
  
  // Send response back to Master
  Wire.write(response,sizeof(response));
  
  // Print to Serial Monitor
  Serial.println("Request event");
}

void loop() {

  // Time delay in loop
  delay(50);
}
```

Once again we start by including the Wire library.  As with the previous sketch we also define the I2C address for the slave, as well as the number of bytes we are planning to send back to the master.

Next we define the string that we are going to send back to the master, in this case just the word “Hello”. If you decide to change this make sure that you adjust the ANSWERSIZE constant in both sketches to be correct.

In the Setup we initialize the connection to the I2C bus with a begin function. Take note of the different way we do this, as this is a slave we specify the I2C address we are going to be using. By doing this the Wire library knows we want to operate in slave mode.

Now we need to define the names of the functions that we will call when two events occur – a data request received from the master and data received from the master.  We also setup and print to the serial monitor.

The function receiveEvent is called when we receive data from the master.  In this function we read data while the data is available and assign it to a byte (remember, the data will be received one byte at a time).

The requestEvent function is called whenever we get a request for data from the master.  We need to send our string “Hello” back to the master. As we need to send the data one byte at a time we divide the characters in “Hello” into individual items in an array and then send them one-by-one.

We report all of our progress in both functions to the serial monitor.

The Loop in this sketch just adds a time delay, which matches the one used in the master sketch.

## Running the Demo Sketches
To run these sketches you’ll need to be able to view the Serial monitor on each Arduino. If you have two computers with the Arduino IDE installed then that will make it a lot easier.

![master-slave](https://user-images.githubusercontent.com/62633516/190432706-8e8d2b9a-6cfb-4fe1-b13c-ff8f033b4458.png)

On Microsoft Windows it is possible to open up two instances of the Arduino IDE. If that is done you could display both serial monitors side-by-side on the same screen.

Alternately, you could use one computer and power up the second Arduino with its own power supply. You would have to switch the computer and power between the two Arduino’s. By doing this you could monitor both screens one-by-one.
