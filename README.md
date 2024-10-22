## Embedded development lesson
### The first 4 tasks are supposed to be done in a simulator called Tinkercad, here is the instruction:
1. Join the Tinkercad classroom https://www.tinkercad.com/joinclass/M8XRNH9J8
2. Click on "My classes" in the profile sub menu
3. Click on "Robotics Lab Embedded Development"
4. There you will find two circuits for task1 and tasks 2-4. Click on them and then on "Copy and tinker"
5. Solve the tasks by making changes in the code menu.
6. For obvious reasons there are no autotests for these tasks, so raise your hand if you are done in order for me to check if everything is in order.

### Task 1
Make an LED gradualy change brightness from 0% to 100% and back over a short period of time.

### Task 2
Make an LED change brightness from 0% to 100% and back by roughly 10% for every button press (the change must be graduate over a short period of time, remember to process contact bounce.

### Task 3
Redo the 2nd task, but now use hardware interrupts to process button press.

### Task 4
Redo the 3d task, but do not use delay() or similar functions, use timer interrupts instead

### Task 5 (optional)
If you have successfully completed the previous tasks, you should implement your own millis() function, using timer 1 of attiny85 controller, that would be given to you. Make an LED blink every second.
