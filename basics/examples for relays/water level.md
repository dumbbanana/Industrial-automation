# WATER LEVEL

Design a control circuit to operate a refilling pump of a reservoir which should be started and stoped automatically with help of level sensors.
- The water pump should start refilling when the level below set low point
- It should stop refilling at set high point. (refer the figure below)
- Sensors are positioned at high and low level points.

<img src="../../assets/images/example/51.png" alt="ques" width="450"/>

----
### TRUTH TABLE

| HL | LL | M  |
|:--:|:--:|:--:|
| 0  | 0  | 1  |
| 0  | 1  | 0 - dropping / 1 -refilling |
| 1  | 1  | 0  |

0 - not triggered/OFF<br>1 - triggered/ON<br>
HL - high level sensor<br>LL - low level sensor

### Control circuit - one line diagram

<img src="../../assets/images/example/52.png" alt="" width="500"/>

### Control circuit schematic diagram

<img src="../../assets/images/example/53.png" alt="" width="500"/>

<br>