# INSTRUCTIONS 
---

## Timer (T0)

Timer is an output component which turns on an input component (usually a switch) after a set time. Timers can be configured to ON delay or OFF delay timer depending on the input component used [NO -> on delay timer , NC -> off delay timer]

#### Command

SYNTAX - output timer value


- **Example instruction:**
```
OUT T0 100
```
Normally the unit of value is in 100ms; the above Command creates an ON delay of 10 seconds.

- Changing the unit of time
```
OUT -> 100 msec timer
OUTH -> 10 msec timer
OUTHS -> 1 msec timer
```
For instance 'OUTHS T0 50' creates a 50 millisecond ON delay timer (1000 ms = 1 sec)

- Reseting the timer 

Timers reset when there si no signal -> T0 resets to zero 

- Using timer for comparisons

The current value of the running timer is stored in the timer registers (T0, T1, T2, T3 ...) you can use it to trigger other circuits by using comparators, comparision, zone comparision and math functions.

#### Example

Use cases of timer can be filling a reservoir or running a mixer or conveyor controls and packaging autoamtions

For simple implementation refer 

---

## Retentive timer (ST0)

Unlike regular timers, whose value gets reset with no signal, retentive timer value is stored in memeory when it receives no signal and resumes the timer when signal returns.

This type of timer requires a RESET switch to reset the timer, or else the timer stops and stays at the set value even when it doesnt recieve any signal.

#### Command

SYNTAX - output timer value


- Example instruction:
```
OUT ST0 100
```
Normally the unit of value is in 100ms; the above Command creates an ON delay of 10 seconds.

- Changing the unit of time
```
OUT -> 100 msec timer
OUTH -> 10 msec timer
OUTHS -> 1 msec timer
```
For instance 'OUTHS ST0 50' creates a 50 millisecond ON delay timer (1000 ms = 1 sec)

- Resetting the timer 

Timers reset when the RESET switch is triggered -> ST0 resets to zero 

```COMMAND - RST ST0 (or) OUT RST ST0 ```

- Using timer for comparisons

The current value of the running timer is stored in the timer registers (ST0, ST1, ST2, ST3 ...) you can use it to trigger other circuits by using comparators, comparision, zone comparision and math functions.

#### Example

Use cases are industrial ovens where food shouldn't be overcook.

For simple implementation refer

---

## Counter

Counter increments the memory register with each pulse (length of the pulse doesn't matter), counter count at rising edge of a pulse.

#### Command

SYNTAX - output counter value

- Example instruction:
```
OUT C0 100
```

Output of counters are normally off, they wil send signal after the set value is reached, which in this case is 100.

- Reseting the counter 

Counters reset when the RESET switch is triggered -> C0 resets to zero 

```COMMAND - RST C0 (or) OUT RST C0 ```

- Using counter for comparisons

The current count in the counter is stored in the counter registers (C0, C1, C2, C3 ...) you can use it to trigger other circuits by using comparators, comparision, zone comparision and math functions.

#### Example

Counter are used in operations that keep track of number of products made and operations that are repetative.

For simple implementation refer

---

## Rising and falling pulse

These input component send a pluse on rising or falling edge of a pulse signal.

#### Commponent

- Rising (low to high)



- Falling (high to low)



#### Example

Using pulse signal are necessary in places where operation are done at clock speed (eg math function) to avoid ghost entries.

For simple implementation refer

---

## Move

Move function block is used to shift values on one register to another. In addition to moving words and integers to a memory register, we can move data from and to special memory registors (conters C0, timers T0, time)

#### Command

SYNTAX - MOV source destination

```
MOV 5 D1
```
Overwrites D1 register with the value 5 

#### Example
Some of the use cases for move function blocks are in HMIs where values are given to timers and counters by an operator.

For simple implementation refer

---

## Using memory registors

Due to constraints on output and input ports in PLC modules, we cannot configure plc in same way as relay logic circuits. PLC programmer use memory bits as virtual input and output port. There are 65536 [2^16] memory bits available for general purpose use (m0, m1, m2, m3...). 

as you know,

```
1 Byte = 8 bits 

1 integer(D0,D1,D2...) = 16 bits

1 double integer(D0,D2,D4) = 32 bits
```
Can't access or manupliate data as bytes in Fx-5u. Each integer/word consists of 16, changing values in m0, m1, m2,....,m15 will change value in D0.

To access memory bit use M0 ; integers use D0 ; double integers are assigned through function block and instructions. while assigning double integers even number data registers are used to account for extra bits of data.

| Bits | integer/word | Double integer |
| :---: | :---: | :---: |
| M0 - M15 | D0 |  |
| M16 - M31 | D1 | D0 |
| M32 - M47 | D2 |  |
| M48 - M63 | D3 | D1 |
| ... | ... | ... |

For simple implementation refer

---

## Comparator

Comparators are used to compare values between set values and values in data registers. Comparators are input component, they function as a switch in circuit.

#### Command

SYNTAX - operation input reference

```
< D0 100
```
compares D0 value to 100 and output true; triggers the circuit when ```D0 < 100```

| Function | Symbol |
| :---: | :---: |
| greater than | > |
| less than | < |
| equal to | = |
| less than/equal to | <= |
| greater/equal to | >= |
| not equal | < > |

#### Example

Some of the use cases for comparators are in temperature control.

For simple implementation refer

---

## Increment 

Increments the data by '1'

#### Command

```
SYNTAX - INC register
```
```DINC -> increments double integer```

```INCP -> increments on pulse``` [To avoid incrementing multiple times on single input]

#### Example

Used to count products on line or packages on conveyors or to keep track of system cycle

For simple implementation refer

---

## Decrement 

Decrements the data by '1'

#### Command

```
SYNTAX - DEC register
```
```DDEC -> increments double integer```

```DECP -> increments on pulse``` [To avoid decrementing multiple times on single input]

#### Example

For simple implementation refer

---

## Jump 

This function is used to skip several rungs in a program. Jump is an output component. If jump is triggered, it skips from command line to the line where page no is mentioned.

#### Command

SYNTAX - ConditionalJump PageNumber

```
CJ P0
```
skips from CJ to p0 line if trigerred.

#### Example

Some of the use cases for jump are in toggle for mode of operation and featues on HMI.

For simple implementation refer

---

## Set

This is used to set the output or memory bit high (1) if trigerred and stays high unless reset is trigered.

#### Command

SYNTAX - SET output (Y0 or M0)

```
SET y0
```
#### Example

For simple implementation refer

---

## Reset 

This is used to set the output or memory bit low  (0) if trigerred

#### Command

SYNTAX - RESET output (Y0 or M0)

```
RESET y0
```

#### Example

For simple implementation refer

---

## Comparision 

Comparision are used to compare two input values and outputs 3 different values based on whether first values is greater than, less than or equal to second value.

#### Command

SYNTAX - CMP firstinput secondinput output

```
CMP D0 D1 Y0
```
sets outputs high based on values 

```if > then y0```

```if = then y1```

```if < then y2```

outputs are saved in consecutive registers from the output mentioned in command.

#### Example

Can be used instead of multiple comparators

For simple implementation refer

---

## Zone comparison

Zone comparison compares the input value to the given range and outputs 3 different values based on whether input values is greater than, less than or in between the given range.

#### Command

SYNTAX - ZCP LowestRange HighestRange  InputValue Output

```
ZCP D0 D1 D2 Y0
```
sets outputs high based on values 

```if D2<D0 then y0 is ON```

```if D0<D2<D1 then y1 is ON```

```if D2>D1 then y2 is ON```

outputs are saved in consecutive registers from the output mentioned in command.

#### Example

Can be used instead of multiple comparators

For simple implementation refer

---

## Real Time Clock (RTC) 

RTC stores real time values (System time) in special data registers (SD) which can be accessed for for math functions and comparators.

#### registers

```
SD 8013 -> Default Seconds
```
```
SD 8014 -> Default Minutes
```
```
SD 8015 -> Default Hours
```
```
SD 8016 -> Default Date
```
```
SD 8017 -> Default Month
```
```
SD 8018 -> Default Year
```
```
SD 8019 -> Default Day of week
```

---

## Subroutine 

This function is used to toggle between multiple pages in the program. This is an outpt function, works when triggered. A section of a program is allocted as main page which will be always on. Solutions are written in subpages. 

#### Command

SYNTAX - Function PageNumber

```
CALL P0
```
```
FEND - Close the main page
```
```
RET - Close the subpage
```

#### Example

Some of the use cases for subroutines are toggling between manual and auto modes, toggling between weekly and weekend schedules.

For simple implementation refer

---

## Master Contol 

Master control literally puts a switch on power line and turns off power to the rungs till mentioned. This is a output component, if trigerred the rung section will be turned off.

#### Command

SYNTAX - function tag-of-MC memory-bit

```
MC N0 M0
```
at start of the section
```
MCR N0
```
at end of the section

#### Example

This can be used as emergency stop in case to keep the devices running which are depended on input signal.

For simple implementation refer

---

## Math functions
#### Command
#### Example

---

## Scaling
#### Command
#### Example
