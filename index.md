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
I've wrapped up the last few steps for my project which includes coding the entire final script for the robot and mounting everything on the robot. I'm still waiting for a Pi camera to arrive since the one I was using broke, and then I will be able to do some test runs and ensure it works. The biggest challenges were learning a lot of how things like the Raspberry Pi, breadboard, wiring, and h-bridge work since I've barely ever worked with those before. Some parts also broke/stopped working and incorrect wiring that caused certain components to stop working which took a while to debug. With those challenges, there were also overcoming them and triumphing. Some of my triumphs were getting several components to work and being able to move on to the next step like the picamera image processing, ultrasonic sensors, and motors. Hopefully, I'll be able to achieve the best accomplishment, which is to get the entire robot to function and do what it's supposed to properly. I hope to learn even more in-depth about robotics/engineering/programming and learn new, more advanced things that we did at BSE using the basic knowledge I've gained from this program.

# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- I've accomplished a lot since the first milestone. I was able to get the ultrasonic sensors to work and completed the entirety of the pi camera image processing to take pictures of the ball and be able to calculate the area and center of it. I also got the motors to run forward, backward, left, and right with the ability to stop them at any time. So far, what was surprising is how easy it is to be able to get things to work when you get an in-depth knowledge of what you are actually doing and how it all connects. Some of the challenges were one of the motors breaking, an ultrasonic sensor or two not working, and a whole lot of bugs during coding. I need to complete mounting all the components onto the car and make final adjustments to the final script. I also need to run through a few test runs and see what could be improved or if it's working at all.
- 
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
from picamera2.encoders import H264Encoder
import time
import cv2 #OpenCV
from picamera2 import Picamera2
import numpy as np
import RPi.GPIO as GPIO
import sys
from gpiozero import DistanceSensor

sensor_proximity=10.1
rerouting_proximity=17.5

lower_range= 180
upper_range= 1740
#ultraosnicsensors
GPIO.setmode(GPIO.BCM)

GPIO_TRIGGER1=26              #ultrasonicsensor1 right
GPIO_ECHO1 = 12

GPIO_TRIGGER2=6               #ultraosnicsensor2 middle
GPIO_ECHO2=5

GPIO_TRIGGER3=11              #ultraosnicsensor3 left
GPIO_ECHO3=9

def sonar(GPIO_TRIGGER,GPIO_ECHO):
    start=0                     
    stop=0
    # Set pins as output and input
    GPIO.setup(GPIO_TRIGGER,GPIO.OUT)  # Trigger
    GPIO.setup(GPIO_ECHO,GPIO.IN)    # Echo
     
    # Set trigger to False (Low)
    GPIO.output(GPIO_TRIGGER, False)
     
    # Allow module to settle
    time.sleep(0.01)
         
    #while distance > 5:
    #Send 10us pulse to trigger
    GPIO.output(GPIO_TRIGGER, True)
    time.sleep(0.00001)
    GPIO.output(GPIO_TRIGGER, False)
    begin = time.time()
    while GPIO.input(GPIO_ECHO)==0 and time.time()<begin+0.05:
        start = time.time()
     
    while GPIO.input(GPIO_ECHO)==1 and time.time()<begin+0.1:
        stop = time.time()
     
    # Calculate pulse length
    elapsed = stop-start
    
    # Distance pulse traveled in that time is time multiplied by the speed of sound (cm/s)
    distance = elapsed * 34300
     
    # That was the distance there and back, so take half of the value
    distance = distance / 2

    # Reset GPIO settings, return distance (in cm) appropriate for robot movements 
    return distance



#motors
MOTOR1B=15
MOTOR1E=17


MOTOR2B=18
MOTOR2E=16

picam2 = Picamera2()
       
camera_config=picam2.create_still_configuration(main={"size":(1920,1080)}, lores={"size":(480,270)},display="lores")
       
picam2.configure(camera_config)

GPIO.setup([MOTOR1B,MOTOR1E,MOTOR2B,MOTOR2E],GPIO.OUT)
# Set pins as output and input
GPIO.setup(GPIO_TRIGGER1,GPIO.OUT)  # Trigger1
GPIO.setup(GPIO_ECHO1,GPIO.IN)      # Echo1
GPIO.setup(GPIO_TRIGGER2,GPIO.OUT)  # Trigger2
GPIO.setup(GPIO_ECHO2,GPIO.IN)      # Echo2
GPIO.setup(GPIO_TRIGGER3,GPIO.OUT)  # Trigger3
GPIO.setup(GPIO_ECHO3,GPIO.IN)      # Echo3

#Set triggers to false(999999(Low)
GPIO.output(GPIO_TRIGGER1, False)
GPIO.output(GPIO_TRIGGER2, False)
GPIO.output(GPIO_TRIGGER3, False)


GPIO.setup(MOTOR1B, GPIO.OUT)
GPIO.setup(MOTOR1E, GPIO.OUT)

GPIO.setup(MOTOR2B, GPIO.OUT)
GPIO.setup(MOTOR2E, GPIO.OUT)

#Defining functions for the motors to move
def forward():
    GPIO.output(MOTOR1B, GPIO.HIGH)
    GPIO.output(MOTOR1E, GPIO.LOW)
    GPIO.output(MOTOR2B, GPIO.HIGH)
    GPIO.output(MOTOR2E, GPIO.LOW)
         
def reverse():
    GPIO.output(MOTOR1B, GPIO.LOW)
    GPIO.output(MOTOR1E, GPIO.HIGH)
    GPIO.output(MOTOR2B, GPIO.LOW)
    GPIO.output(MOTOR2E, GPIO.HIGH)
     
def rightturn():
    GPIO.output(MOTOR1B,GPIO.LOW)
    GPIO.output(MOTOR1E,GPIO.HIGH)
    GPIO.output(MOTOR2B,GPIO.HIGH)
    GPIO.output(MOTOR2E,GPIO.LOW)
     
def leftturn():
    GPIO.output(MOTOR1B,GPIO.HIGH)
    GPIO.output(MOTOR1E,GPIO.LOW)
    GPIO.output(MOTOR2B,GPIO.LOW)
    GPIO.output(MOTOR2E,GPIO.HIGH)

def stop():
    GPIO.output(MOTOR1E,GPIO.LOW)
    GPIO.output(MOTOR1B,GPIO.LOW)
    GPIO.output(MOTOR2E,GPIO.LOW)
    GPIO.output(MOTOR2B,GPIO.LOW)
      
def sharp_left():
    GPIO.output(MOTOR1B,GPIO.LOW)
    GPIO.output(MOTOR1E,GPIO.HIGH)
    GPIO.output(MOTOR2B,GPIO.HIGH)
    GPIO.output(MOTOR2E,GPIO.LOW)
    
def sharp_right():
    GPIO.output(MOTOR1B,GPIO.HIGH)
    GPIO.output(MOTOR1E,GPIO.LOW)
    GPIO.output(MOTOR2B,GPIO.LOW)
    GPIO.output(MOTOR2E,GPIO.HIGH)
    
def segment_colour(frame):   
    hsv_roi =  cv2.cvtColor(frame, cv2.COLOR_RGB2HSV)
    test=cv2.medianBlur(hsv_roi,3)
    mask_1 = cv2.inRange(test, np.array([150, 140,1]), np.array([190,255,255])) 
    cv2.imshow('mask_1', mask_1)
    mask = mask_1 
    kern_dilate = np.ones((12,12),np.uint8)
    kern_erode  = np.ones((6,6),np.uint8)
    mask= cv2.erode(mask,kern_erode)    
    mask=cv2.dilate(mask,kern_dilate)     
    (h,w) = mask.shape
    cv2.imshow('mask', mask) 
    
    return mask

def find_blob(blob): 
    largest_contour=0
    cont_index=0
    contours, hierarchy = cv2.findContours(blob, cv2.RETR_CCOMP, cv2.CHAIN_APPROX_SIMPLE)
    for idx, contour in enumerate(contours):
        area=cv2.contourArea(contour)
        if (area >largest_contour) :
            largest_contour=area
            cont_index=idx
                    
    r=(0,0,2,2)
    if len(contours) > 0:
        r = cv2.boundingRect(contours[cont_index])
        
     
    return r,largest_contour

def no_obstacle(distanceC,distanceL,distanceR): #TRUE: no obstacles within 10 cm of sensor, FALSE: obstacle
        
    if distanceC>sensor_proximity and distanceR>sensor_proximity and distanceL>sensor_proximity:
       return True
    else:
       return False
    
#Camera capture

#camera = cv2.VideoCapture(0)
       
#camera.set(3,320)
       
       
#picam2.start_preview(Preview.QTGL) #display the video
       
picam2.start()
       
time.sleep(2)
       
flag=0#Searching:0:left turn for last location of ball, 1 for right term
       
flag_reroute=-1#Reroute searching

found=0
       
while(True):
    im = picam2.capture_array()
    height = im.shape[0]
    width = im.shape[1]
    #cv2.imshow('file1.png', im)
    global center_x
    global center_y
    center_x=0.
    center_y=0.
    distanceR = sonar(GPIO_TRIGGER1,GPIO_ECHO1)
    distanceC = sonar(GPIO_TRIGGER2,GPIO_ECHO2)
    distanceL = sonar(GPIO_TRIGGER3,GPIO_ECHO3)
    print("dL, dC, dR ", distanceL//1, distanceC//1, distanceR//1)
    hsv1 = cv2.cvtColor(im, cv2.COLOR_RGB2HSV)
    mask_red=segment_colour(im[:,:,[0,1,2]])
    #cv2.imshow('frame', mask_red)
    #Masking red the frame
    loct,area=find_blob(mask_red)
    x,y,w,h=loct 
    #center_x=x+((w)/2)
    #center_y=y+((h)/2)
    print(area)
    print(found)
       
    if (w*h)<20000:
            #If the width and height is really small, that means it can't find the ball
        found=0
    else:
            #This means it has found the ball
        found=1
            #Creates the rectangle so we can get the center x value and center y value
            #This helps us track it better
        simg2 = cv2.rectangle(im,(x,y),(x+w,y+h),255,2)
        center_x=x+w/2
        center_y=y+((h)/2)
        print("Center is:",center_x,center_y)
        cv2.circle(im,(int(center_x),int(center_y)),3,(0,110,255),-1)


    initial=2000000

    if((area<initial) and (found==1)):
        print("Ball is found")
        print(no_obstacle(distanceL,distanceC,distanceR))
        if no_obstacle(distanceL,distanceC,distanceR):
            if(center_x<lower_range):
                flag=0
                rightturn()
                print("leftturn")
                time.sleep(0.05)
            elif (center_x>upper_range):
                flag=1
                leftturn()
                print("rightturn")
                time.sleep(0.05)
            else:
                forward()
                print("forward")
                time.sleep(0.05)
    else:
        stop()
        time.sleep(0.005)
        if ((distanceC < sensor_proximity) and (area>=1500000)):
            stop()
            time.sleep(0.005)
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
| Ultrasonic sensors | Detecting distance between car and ball | $9 | <a href="["](https://www.amazon.com/Organizer-Ultrasonic-Distance-MEGA2560-ElecRight/dp/B07RGB4W8V/ref=sr_1_11?asc_source=01H8HFYCS1MWCPQSJYRR7EWW12&crid=2UILRK8AIBOYP&dib=eyJ2IjoiMSJ9.hxKSGnm38uFYPbLd-yrIsAwtxyRhETnroFHfs4vAAJNUM_kIEuR-nuF7-zrx6y7HTcehmQa5c-zSOroOyhP6BSMitoYHhl7aItvKPuH_1_-VpL5MOC4LZI3bXoahUHZoq62JEehgre2XBi1HZzq5OBky4eTgane4rNZvKn5hizH14nxcxUzec_t6_BZ-OzKSPbG9xr4En_DPghFmAxh_ywgEl6YPahX9gAItQ9j9Z9A.gQX575YLLnN5W5kK6GYpAVAgBQZNCFtzP0s-0F89CwM&dib_tag=se&keywords=ultrasonic+sensor&qid=1719595462&sprefix=ultrasonic+sensor%2Caps%2C189&sr=8-11&tag=namespacebran691-20)> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
