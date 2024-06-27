# Posture Corrector
The goal of the posture corrector is to help the user develop better posture naturally instead of a traditional back brace. This is through a flex sensor which is able to detect slouching, which sends a message from the arduino to your phone notifying you to fix your posture.

<!---
You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:

-->

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Kyle K | Prospect High School | Mechanical Engineering | Incoming Senior |

<!--- **Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**
-->
![Headstone Image](Kyle_K.jpg)

<!---
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE-->

# Second Milestone

For my second milestone, I have created a Bluetooth connection with my Arduino along with a rudimentary app on my Android, which I created using MIT App Inventor. This app is able to change text on-screen to tell if the user is either slouching or not slouching based on what it receives from my Bluetooth module. 

I spent a large portion of time understanding the basics of how the Bluetooth HC-05 module works and how it's meant to be set up. Oftentimes a Bluetooth Module’s data in and data out pins are labeled transmitter and receiver. The transmitter’s job is to transmit data serially from the module to the arduino, and the receiver’s job is to receive data from the Bluetooth communication. Serial communication is the process of sending data one bit at a time, so I coded my Arduino to send one byte to the Bluetooth module, this data would then be transmitted from the module to my Android phone. 

Originally my plan was to connect the RX and TX pins of my Bluetooth to the 0 and 1 data pins on the Arduino respectively to send data. However I found quickly that this wouldn’t work. By connecting the Bluetooth’s pins to the 0 and 1 data pins of the Arduino, while it would send the bytes from the Bluetooth module, it would also send all the other data from my Arduino’s Serial Monitor, which I couldn’t use.

I was able to specifically send out the individual Bytes by creating an object using the Software Serial class from the SoftwareSerial library, where I could then specify what data pins I could connect to my Bluetooth pins to without sending data from my Serial Monitor as well. By using the .write method, I was able to print my data to the TX pin, then use the .flush method to clear the queue of bytes. 

Now that my Arduino was able to send data to my phone, I needed to create an app to read the data and display if the user was slouching or not. For this I used MIT App Inventor. The MIT app inventor uses block-style coding which I was very unfamiliar with, so it took me a very long time to understand what I was doing. I was able to establish a Bluetooth connection with the module by creating a list picker element which, when clicked, would show the address and names of available connections.

When the Bluetooth Module is connected I had to create a system that could read the data it received. For this I used the clock component that would trigger every one-tenth of a second. From there I used a block labeled “call BluetoothClient1.ReceiveUnsigned1ByteNumber”. This block is able to read the bytes sent from my module. Because the bytes I sent were all positive numbers I would receive an unsigned byte which is always positive. With the bytes sent by my Bluetooth, I constructed a basic if state that would determine if the user is slouching based on what number it received. If the app received ‘0’ the user was not slouching if the app received ‘1’ the user is slouching. 

I encountered multiple issues when connecting my Bluetooth module both from the module being difficult to work with, along with me not quite understanding how the Bluetooth worked. I would blindly follow guides I found online instead of trying to understand what the methods in the Software Serial library or the blocks in the MIT App inventor did. Eventually by patiently sitting down and learning what they did, I was able to make my app work. 
For my third milestone, I plan on finalizing a lot of my project. This includes soldering my wires, permanently attaching my flex sensor onto my back brace, and adding a notification system onto my app with my new understanding of what the blocks do. 

<!---
**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone -->


# First Milestone

For my first milestone, I have a working basic prototype of my posture corrector. This is done by having a flex sensor attached to a back brace that is attached to the upper portion of the back along. There are also LED lights that will respond to the values returned by my flex sensor.

![Headstone Image](Flex-Sensor-bending-conditions.webp)

**A flex sensor works by having conductive ink on a small strip of plastic which acts as a variable resistor. By flexing the strip of plastic, you change the flex sensor's resistance. The more you bend the higher the resistance.**

When you slouch, your back stretches as you bend forward. The way my device is configured is that when the user's back is in a proper position, the flex sensor will be bent. When the flex sensor is bent the conductive ink particles are farther apart increasing the resistance in the flex sensor. Likewise, when the user reclines the flex sensor is straightened as the back stretches. This will allow the conductive ink particles to be close together, allowing them to have less resistance.

![Headstone Image](circuit.jpg)

**This diagram is the circuit schematic of the flex sensor the Analog reader reads the voltage in-between the flex sensor and the 330 Ohm resistor.**

In order to tell if the flex sensor was bent, I needed to find the resistance of the flex as the flex sensor is a variable resistor, meaning that its resistance changes based on how it bends. However the Arduino is unable to measure resistance, but it is able to measure voltage. We can find the change in voltage by using a voltage divider. The equation for the Voltage is Vout=Vin*R2R1+R2 as the two resistors are in series which means that we must add the resistance of both resistors. R1 represents the first resistor which is our 330-Ohm resistor and R2 represents our flex sensor’s resistance which may change based on how it bends. This allows for the analogRead function of my code to see the difference in voltage from the flex sensor bending as current passes through the flex sensor. From there I can return the values of the flex sensor as the sensor is straightened or bent. analogRead is able to convert the voltage from 0 to 5v into a value from 0 to 1024. Much of my time was spent testing what value the flex sensor exceeds when the user slouches. I discovered that the value hovers anywhere from 14-17. If the flex sensor has those values, the user will count as slouching in which the words "slouching" will appear on the serial monitor.

![Headstone Image](Schematic.jpg)

**Current schematic connecting the flex sensor and the LED strip**

I also have an LED strip connected to the breadboard. I was able to power both the flex sensor and the LED lights with the 5V pin of the Arduino by making a power line on the edges of the breadboard with a wire connected to one part of the power line and the 5V pin while doing the same when connecting ground. I need to code the lights to begin flashing when slouching was detected. I was able to do so with the strip.fill(A,B,C) member function. Strip is the class object created with certain member variables such as LED count and LED_PIN which allows us to control the LED strip. A dictates the color of the Neopixels, B tells where the first Neopixel should be lit up, and C tells where the last Neopixel should be lit up. Unlike a regular LED which would just turn on with a set color if it had power, the individual Neopixels are able to do different actions by being connected to a data pin on the Arduino which allows me to send data to the Neopixels and tell them which individual Neopixels should turn on and in what color. Now I need to make the lights flash instead of just showing a solid color. I was able to do this by adding delay(500); inside the if statement describing what to do if the analogRead value is too high. When the analog value is too high, the lights turn on, then the program waits 500 ms to then turn the lights off using the strip.fill function. This created a half second delay wherever the lights flash in certain intervals creating a flashing effect.

A challenging aspect of my project was with hardware, specifically soldering and wiring. When creating an extension for my flex sensor, I accidentally broke the flex sensor by keeping it in contact with the soldering iron for too long. This melted the plastic and the wiring of the flex sensor, requiring me to get a replacement. The other instance was when I accidentally shorted an Arduino UNO when making a power line for the ground wires of my Bluetooth module and LED lights. By inserting the ground wires into the power side of the breadboard, I accidentally shorted the Arduino requiring another replacement. My many errors have opened my eyes as to how much precision and care must be taken when working with physical components both for my safety and to maintain equipment quality. 

A challenging aspect of my project was with hardware, specifically soldering and wiring. When creating an extension for my flex sensor, I accidentally broke the flex sensor by keeping it in contact with the soldering iron for too long. This melted the plastic and the wiring of the flex sensor, requiring me to get a replacement. The other instance was when I accidentally shorted an Arduino UNO ;when making a power line for the ground wires of my Bluetooth module and LED lights. By inserting the ground wires into the power side of the breadboard, I accidentally shorted the Arduino requiring another replacement. My many errors have opened my eyes as to how much precision and care must be taken when working with physical components both for my safety and to maintain equipment quality.

Another challenge I faced was in the software aspect of my project, as I was quite unfamiliar with coding on an Arduino. I initially struggled with defining classes and using the various functions provided by the NEOPIXEL library. The struggle has helped me to gain a better understanding of coding on an Arduino and how to troubleshoot issues.

For my second milestone, I plan on further developing the software aspect of my project with my newfound knowledge of coding on Arduino. This is by getting a Bluetooth module to work with the Arduino. I also plan to have a basic version of my app using the MIT App Inventor.


<iframe width="560" height="315" src="https://www.youtube.com/embed/TSYudepJFzY?si=NndYQ7sqB-8C4Hcd" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<!---
**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project --->

# Starter Project: Handheld Retro Arcade

The Handheld Retro Arcade is mostly for soldering practice as I had to solder almost all parts of the arcade onto the main frame. This included using a soldering iron and solder to connect many of the arcade's pieces. I had to solder parts like the buttons, micro USB, IC chip, power cable, 2D LED dot matrix module, etc. along with assembling the battery case and the frame of the arcade. 

Essentially the arcade works by using either the batteries or the micro USB to power the IC Chip attached to the main frame. The IC chip acts as the brain of the arcade, containing all the code and logic for the arcade's games. With the chip powered, when the player presses any button on the arcade it sends a signal through small wires on the main frame of the arcade to the chip. When the signal reaches the IC chip, the chip can translate the input of the buttons into output by telling the 2D LED dot matrix which dots to light up. The 2D LED dot matrix is the arcade screen and how the player views the game they are playing.

![Headstone Image](Cropped_Chip.jpg)

**Figure 1. The IC Chip here is the brain/command center of the arcade, all actions you do in your game go through here first. Information enters and leaves the IC Chip via the pins which are the silver parts the stick out of the Chip. Each pin is unique in both position and function. When information enters the chip it is processed by layers of semiconductor wafers, copper, and other materials, which interconnect to form transistors, resistors or other components in a circuit**

For example, the console can translate you pressing the right button of the arcade into the action of moving the tetris piece to the right. This is by sending a signal onto the IC Chip which translates the signal into an action onto the LED Matrix. This allows the player to see that the tetris piece moves to the right.

A challenging aspect of this project is soldering the many components of the arcade console. Since I am inexperienced with soldering, soldering the smaller holes was hard to do. I also initially failed to follow instructions properly and had to restart the project in the beginning. This made me think that I was now wildly behind and I began panicking. Thankfully I was able to finish the starter project on time, and this project has taught me meaningful soldering skills and to keep my composure even in the face of hardship and difficulty. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/HDBI_cemtvI?si=11bn_fcc8gBkOhFm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<!---
# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. --->

<!---
# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. --->
<!---
```
CODE GOES HERE
```
-->
<!---
# Bill of Materials

Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
--->
<!---
# Other Resources/Examples

One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)
--->
To watch the BSE tutorial on how to create a portfolio, click here.
