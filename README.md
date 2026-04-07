# MaRS-ELECTRONICS-TASK-1-
MaRS Club Electronics Subsystem Task 1 submission including Tinkercad simulations and mini project
SECTION A- Question 1 — Blinking LED with different time interval
Tinkercad Link:
https://www.tinkercad.com/things/j6rlwBen4zJ-start-simulating/editel?lessonid=EHD2303J3YPUS5Z&projectid=OT2JZ1PL20FZRMO&returnTo=https:%2F%2Fwww.tinkercad.com%2Fdashboard%2Ftutorials&sharecode=Z5hC19WurOL88FCPqzw3z6EdhtDGP3xFHVoQiNyZrwM
Code link:
https://github.com/hasinii-ii/MaRS-ELECTRONICS-TASK-1-/blob/249b63829a6e5a5eb81579420961579b940fdeba/Working%20code%20for%20SECTION%20A-%20Question%201%20%E2%80%94%20Blinking%20LED%20with%20different%20time%20interval
Explanation:
 This circuit uses an Arduino Uno with three LEDs connected to pins D11, D12, and D13, each with a 220Ω resistor to GND. The millis() function is used instead of delay() to track elapsed time independently for each LED. Each LED has its own previousMillis variable that stores the last time it toggled. Every loop iteration checks if enough time has passed for each LED separately, so all three blink simultaneously — at 500ms, 1000ms, and 1500ms — without any one LED blocking the others.
code logic:
 Instead of using delay() (which blocks all execution), millis() returns the time elapsed since the program started. Each LED has its own "previous timestamp" variable. Every loop iteration checks whether enough time has passed for each LED independently — so all three blink simultaneously without interfering with each other.
SECTION A- Question 2 — Controlling colour of RGB LED and blinking speed of another LED with potentiometer
Tinkercard link:
https://www.tinkercad.com/things/2G1fBwocBhV-q2-rgb-colour-blink-rate-via-potentiometer/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard%2Fdesigns%2Fall&sharecode=--GPdmvyjQGLgBZ6QjxlqVaC4xcKQeWJycMeta24cp4
code link:
https://github.com/hasinii-ii/MaRS-ELECTRONICS-TASK-1-/blob/e3475a9b334a9be062537fdfe093d71e57423538/Working%20code%20for%20SECTION%20A-%20Question%202%20%E2%80%94%20Controlling%20colour%20of%20RGB%20LED%20and%20blinking%20speed%20of%20an-%20other%20LED%20with%20potentiometer
Explanation:
A potentiometer connected to A0 outputs an analog value from 0 to 1023, which controls two things at once. The value is divided into three colour zones that smoothly transition the RGB LED through Red→Green→Blue using analogWrite() with map() for interpolation. The same potentiometer value is also mapped to a blink interval between 100ms and 1500ms, controlling how fast a separate LED blinks. A millis()-based timer handles the blink so both colour and speed update in real time without any delay() blocking the loop.
code logic:
 The potentiometer value (0–1023) is split into three zones to smoothly cycle through Red→Green→Blue→Red as a colour wheel. analogWrite() outputs PWM signals to the RGB LED. The same pot value is also mapped to a blink interval (100ms–1500ms), controlling the separate LED's speed using millis() (no blocking delay()).
SECTION A- Question 3 — Build a reaction time tester
Tinkercad Link:
 https://www.tinkercad.com/things/cocej4FUYVg/editel?returnTo=%2Fdashboard%2Fdesigns%2Fall&sharecode=0cWRxQI901A2jKC4GXbXtF1Dv1tDOVsUnxwYXIBGcJw
 code link:
  https://github.com/hasinii-ii/MaRS-ELECTRONICS-TASK-1-/blob/2c8c99fd5e2c30b434f91547093dac79a771c5bb/Working%20code%20for%20SECTION%20A-%20Question%203%20%E2%80%94%20Build%20a%20reaction%20time%20tester
Explanation:
The LED turns on after a random delay of 2–7 seconds, seeded from electrical noise on a floating analog pin using randomSeed(analogRead(A0)). The button is wired with INPUT_PULLUP, meaning Arduino's internal resistor keeps the pin HIGH — pressing the button pulls it LOW, requiring no external resistor. When pressed, reaction time is calculated as millis() - ledOnTime, giving elapsed milliseconds since the LED turned on. The result is printed to the Serial Monitor along with a performance rating, and a new random round begins automatically.
code logic:
 INPUT_PULLUP keeps the button pin HIGH internally — pressing it pulls it LOW, requiring no external resistor. randomSeed(analogRead(A0)) seeds the RNG from electrical noise on a floating analog pin. When the LED turns on, millis() records ledOnTime. On button press, millis() - ledOnTime gives reaction time in milliseconds. After each round, a new random delay is set.
 Section B: Mini Project - Smart Distance Alert System
 Tinkercad Link:
 https://www.tinkercad.com/things/eq8ynWE2mUe/editel?returnTo=%2Fdashboard&sharecode=X8kD24sGivNusxO6zn3_r83DPIsSMnFiZHRfqCbPnRg
 code link:
  https://github.com/hasinii-ii/MaRS-ELECTRONICS-TASK-1-/blob/2c8c99fd5e2c30b434f91547093dac79a771c5bb/Working%20code%20for%20Section%20B%3A%20Mini%20Project%20-%20Smart%20Distance%20Alert%20System
  - What the project does and why I chose it
This project measures the distance to nearby objects using an HC-SR04 ultrasonic sensor
and gives the user both a visual and audible alert based on how close the object is. A
green LED stays on when everything is clear (beyond 40 cm), a yellow LED with a short
repeating beep kicks in when something is getting close (between 20 and 40 cm), and a red
LED with a continuous alarm goes off when something is dangerously near (under 20 cm).
The live distance reading is also printed to the Serial Monitor the whole time so you can
watch it in numbers as well.
I picked this project because it felt the most directly connected to what we actually do
in MaRS. A Mars Rover needs to know when it is about to hit something — that is the whole
point of proximity sensing. Building this from scratch made me appreciate just how much
logic goes into something that seems simple on the surface: measuring a distance, deciding
which zone it falls into, and responding with the right combination of light and sound,
all happening in a tight loop without any single step freezing the rest.
  -Components used and their roles
 Component | Pin | Role 
 Arduino Uno | — | Brain of the circuit — runs all the logic and timing 
 HC-SR04 ultrasonic sensor | Trig → D9, Echo → D10 | Fires an ultrasonic pulse and listens for the echo to calculate distance 
 Green LED | D4 via 220Ω | Stays on in the safe zone, tells you nothing is nearby 
 Yellow LED | D5 via 220Ω | Turns on in the caution zone, paired with a short beep 
 Red LED | D6 via 220Ω | Turns on in the danger zone, paired with a continuous alarm 
 Buzzer | D7 | Gives an audible alert so you do not have to stare at the LEDs 
 3× 220Ω resistors | — | Limit current into each LED so they do not burn out 
  -Challenges faced and how I solved them
The first problem I ran into was that the sensor was giving back random garbage readings
every few cycles. After some research I found that this happens when the trigger pulse is
not clean — the fix was to pull the trigger pin LOW for 2 microseconds before sending the
10 microsecond HIGH pulse, which gives the sensor a proper rising edge to latch onto. That
made the readings rock solid.
The second issue was with the buzzer. My first version used `delay()` after each beep,
which meant the Arduino was completely frozen during that pause and could not take any new
sensor readings. I switched to using `tone()` with a built-in duration argument for the
caution beep, which lets the function handle its own off-timing in the background while
`loop()` keeps running. That one change made the whole circuit feel much more responsive.
