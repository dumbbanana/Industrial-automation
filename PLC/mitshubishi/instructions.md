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

## Using memory bit
#### Command
#### Example

---

## Move

Move command is used to shift values on one register to another. In addition to moving words and integers to a memory register, we can move data from and to special memory registors (conters C0, timers T0, )

#### Command

SYNTAX - MOV source destination

```
MOV 5 D1
```


#### Example

---

## Comparator
#### Command
#### Example

---

## Math functions
#### Command
#### Example

---

## Increment 
#### Command
#### Example

---

## Decrement 
#### Command
#### Example

---

## Set 
#### Command
#### Example

---

## Jump 
#### Command
#### Example

---

## Set
#### Command
#### Example

---

## Reset 
#### Command
#### Example

---

## Comparision 
#### Command
#### Example

---

## Zone comparison 
#### Command
#### Example

---

## Master Contol 
#### Command
#### Example

---

## Real Time Clock (RTC) 
#### Command
#### Example

---

## Subroutine 
#### Command
#### Example

---

## Scaling
#### Command
#### Example
