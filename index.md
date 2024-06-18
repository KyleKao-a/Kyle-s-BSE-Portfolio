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

<!---
# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone -->


# First Milestone

For my first milestone I have a working basic prototype of my posture corrector. How it works I that I have a flex sensor attatched to my back brace that is attatched high up on my back. When the user's back bends, will cause the sensor to be stretched, causing the value of the flex sensor to change. I have the flex sensor attatched to the arduino and am able to return the values of the flex sensor. If the flex sensor exceeds a certain value because of the bending, the user will count as slouching in which the words "slouching" will appear on the serial monitor.

![Headstone Image](Flex-Sensor-bending-conditions.webp)
**How a flex sensor works is that there is carbon on a small strip of plastic which acts as a variable resistor. By flexing the strip of plastic, you change the flex sensor's resistance. The more you bend the higher the resistance. 
**
Furthermore, I have attached lights onto my back brace that will start flashing if the arduino detects slouching that are also wired on the arduino. 

A big challenge I faced with my project is firstly, soldering the flex sensor to the wires as I accidently broke the flex sensor and needed a replacement, I also had a lot of trouble programming the lights of the brace since I'm pretty rusty at programming so it took a lot longer to find the right functions to use. 

My plan now is to attatched the bluetooth module onto the arduino and get the bluetooth to work and start sending messages to the samsung galaxy phone. 
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
