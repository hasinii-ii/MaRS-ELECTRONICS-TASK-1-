# MaRS-ELECTRONICS-TASK-1-
MaRS Club Electronics Subsystem Task 1 submission including Tinkercad simulations and mini project
SECTION A- Question 1 — Blinking LED with different time interval
Tinkercad Link:
https://www.tinkercad.com/things/j6rlwBen4zJ-start-simulating/editel?lessonid=EHD2303J3YPUS5Z&projectid=OT2JZ1PL20FZRMO&returnTo=https:%2F%2Fwww.tinkercad.com%2Fdashboard%2Ftutorials&sharecode=Z5hC19WurOL88FCPqzw3z6EdhtDGP3xFHVoQiNyZrwM
Explanation:
 Instead of using delay() (which blocks all execution), millis() returns the time elapsed since the program started. Each LED has its own "previous timestamp" variable. Every loop iteration checks whether enough time has passed for each LED independently — so all three blink simultaneously without interfering with each other.
SECTION A- Question 2 — Controlling colour of RGB LED and blinking speed of another LED with potentiometer
https://www.tinkercad.com/things/2G1fBwocBhV-q2-rgb-colour-blink-rate-via-potentiometer/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard%2Fdesigns%2Fall&sharecode=--GPdmvyjQGLgBZ6QjxlqVaC4xcKQeWJycMeta24cp4
Explanation:
 The potentiometer value (0–1023) is split into three zones to smoothly cycle through Red→Green→Blue→Red as a colour wheel. analogWrite() outputs PWM signals to the RGB LED. The same pot value is also mapped to a blink interval (100ms–1500ms), controlling the separate LED's speed using millis() (no blocking delay()).
SECTION A- Question 3 — Build a reaction time tester
Tinkercad Link:
 https://www.tinkercad.com/things/cocej4FUYVg/editel?returnTo=%2Fdashboard%2Fdesigns%2Fall&sharecode=0cWRxQI901A2jKC4GXbXtF1Dv1tDOVsUnxwYXIBGcJw
 Explanation:
 INPUT_PULLUP keeps the button pin HIGH internally — pressing it pulls it LOW, requiring no external resistor. randomSeed(analogRead(A0)) seeds the RNG from electrical noise on a floating analog pin. When the LED turns on, millis() records ledOnTime. On button press, millis() - ledOnTime gives reaction time in milliseconds. After each round, a new random delay is set.
 
