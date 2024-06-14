# Ball Tracking Robot Car
My project is a robotic car controlled by a Raspberry Pi that uses sensors to identify, track the ball, and follow it. In the Raspberry Pi 4, we use Python 3 to code for tracking the ball, and use ultrasonic sensors to detect the ball. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- Project description, image of myself & and completed project, final milestone, second milestone, embedded videos for all milestones. -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Aadityaa B | Heritage High School | Computer/Electrical Engineering | Incoming Sophomore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


  There are a lot of different components that go into this project since it is a combination of hardware and software sides of engineering. There is a chassis for the car itself, along with its motors & wheels and other smaller parts that go into the car. Then there is the Raspberry Pi, which controls the vehicle with the programming I do in the programming app. For the sensory parts of the car, we have the ultrasonic sensors and the Pi camera that connects to the Raspberry Pi to track the ball itself. To connect the hardware and software, we have different types of wires, a H-bridge, and a breadboard to make it all come together.  
  So far, I've made the chassis for the robotic car and attached the motors. In the Raspberry Pi, I've written the code to turn the motors on and the code to take pictures/videos with the Pi camera. I also have the wires, H-bridge, and breadboard all connected with the motors, battery pack, and Raspberry Pi.
- Some challenges I have faced so far were mainly the wiring of the Raspberry Pi and breadboard to the battery pack and motors, as well as figuring out the code. It took looking at code from many different sources and finding the correct pin layout to get it to work. I don't know yet what kind of challenges I will face in the second milestone, but I look forward to conquering them.
- My plan is to come up with what modification I want to make and get the second milestone done as soon as possible. that way, I can focus on the modification for the rest of the second week and hopefully have that all figured out by the beginning of the third week.

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 | Computer for programming the car | $62 | <a href="https://www.amazon.com/Raspberry-Model-2019-Quad-Bluetooth/dp/B07TC2BK1X/ref=sr_1_3?asc_source=01H8HFYCS1MWCPQSJYRR7EWW12&crid=3K29UX526D2CH&dib=eyJ2IjoiMSJ9._PqCjKFXecURzDfuwZg7dnSe-rn341n1YEUC3kxkYF_Yx13g9nuKnUr6p98SCxu5Ta7LtrG8xDihrV87MNPA3zaiUe9_dNQo6Vdk5tCKMtKz-YBdmDtmQ74zuqfzO6hAf8GQ4CEFH6i_VK75th9MqakR3CtRjjChDmtB_STwTCE0XvK87VpVE9VvFxSDEgZmT202LVdRfE1wf1rfDGbHgTMwYAM8v0s-LE_ZKtIwoRE.loCQvBfb72g9nOlZLcM5vAWTw8LPKga8rIAm3xkNMeI&dib_tag=se&keywords=raspberry+pi+4+model+b&qid=1718382971&sprefix=raspberry+pi+4+model+b%2Caps%2C147&sr=8-3&tag=namespacebran691-20"> Link </a> |
| Smart Car Building Kit | Building the chassis | $19 | <a href="https://www.amazon.com/YIKESHU-Smart-Chassis-Encoder-Battery/dp/B073VHQT6P"> Link </a> |
| Breadboard | Connecting wires to battery, motors, raspberry pi | $9 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Wires | Thw wires itself connecting battery, motors, raspberry pi to breadboard | $12.5 | <a href="https://www.amazon.com/SIM-NAT-Breadboard-Arduino-Raspberry/dp/B07RX78T9L/ref=sr_1_5?crid=19OD2B6R7STLK&dib=eyJ2IjoiMSJ9.ZmpXiA1DmDoLssuQVlmgV33pDDn98oQdkqWEkd4GjmtQbxgPywu-zvVmlLYiVuZN7DQyZ7Xx_2KiEaiI6s0stm3eeAVGqslBbvhCDvbfrCdJpE1LYFw3HTXSbLru7I-gpi-wINt-jDT03qRk86DRUysRUDdlxgZ8231ta9-mq25jTygdqFOWh_tF8OgCYw7nhZjcVcZyWXEJ1fDyDderUkbVZCJUtPK2OOzZm0zN7tQ.z504ABAoZT5eNWPkr0XmRtpDaIEBM-9WOTBVTy_9wa0&dib_tag=se&keywords=wires+kit+for+raspberry+pi&qid=1718383544&sprefix=wires+kit+for+raspbaerry+pi%2Caps%2C180&sr=8-5"> Link </a> |
| H-Bridge Set| Connecting motors to breadboard,which connects to raspberry pi & battery | $9 | <a href="https://www.amazon.com/HiLetgo-Controller-Stepper-H-Bridge-Mega2560/dp/B07BK1QL5T/ref=sr_1_3?crid=QAC1LIBMFWG1&dib=eyJ2IjoiMSJ9.1NQtb_sWjrkCYw5IyjS8yVwr-fv72tK_yJsFj88l2drtLD4wveRySqaN9YpznGLwcugcjSV3m4qsiRuywvcyGlH5AbpIbvnuXCt_9qdWuBN3-1sBhEhNeQOSl4Q0nFOSo2ngRuX_ZxGFcHCU3BitVqx7yI09eDlz4bB4muYKX9IUaVkWGtXwacEMJ0_Vl9QgHmP1bb6nUnrB5X1zaLNJmKWoGDWnGYTpFiaT_sSTUVOhrc6KoDuHtemn3C_wQUigvCkp59LyIoMpxWknIVToB07VrttxGX0WbvcHsjYiAzc.UVAU3J_69T7X3LpinDoAsBOAeoDtP50lKM-XLWCoFzU&dib_tag=se&keywords=h-bridge+motor+set&qid=1718383652&sprefix=h-bridge+motor+set%2Caps%2C161&sr=8-3"> Link </a> |
| Energizer Non-rechargeable Battery Pack | Powering the motors | $9 | <a href="https://www.amazon.com/Energizer-Ultimate-Lithium-AA-Batteries/dp/B008OII4TY"> Link </a> |


# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
