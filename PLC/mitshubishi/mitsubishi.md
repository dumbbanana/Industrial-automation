# MITSUBISHI Programmable Logic Controller

We are starting with a PLC controller from Mitsubishi. 

- Mitsubishi offer 2 types of plc controllers mainly,
    - Q series (rack type)
    - fx series (modular type)

The software offered by Mitsubishi to program their products called GX works
- GX work 2 for Q series and older models 
- GX work 3 for FX series

----

For training, we used Model FX - 5u; which is a compact 24V DC PLC controller with 16 input and 16 output ports and output ports were relay type, which means output from plc can be DC or AC depending on the power supply connected to output common port.

<img src="../../assets/images/mitsubishi/download.jpg" alt="modelpic" width="300"/>

<br>

### Outline

<img src="../../assets/images/mitsubishi/label.png" alt="label" width="500"/>

<br>

### Internal configuration

<img src="../../assets/images/mitsubishi/figure2.png" alt="figure2" width="500"/>

<br>
<br>

As the figure above shows contacts in ladder programs are triggered by the power at the input port which is independent of the type of contact used to keep the input port high/low.

This means a stop button on the panel which is normally closed is mentioned as normally open contact in the program. This could be confusing as the way I like to put to imagine the contact on panels are perpendicular to contacts on the program which are triggered only when current passes through them as the figure below shows.

<img src="../../assets/images/mitsubishi/fig3.png" alt="figure2" width="400"/>

<br>
Since the NC from the panel is already triggering the port on the controller using a NO in the programming will operate as the circuit as designed 

<br>

| contact on panel | contact used in the program to represent it | result of the circuit (normally) |
| :---: | :---: | :---: |
|   NO  |   NO  |  off  |
|   NO  |   NC  |  on   |
|   NC  |   NO  |  on   |
|   NC  |   NC  |  off  |

[For the purposes of understanding since wiring configuration may vary depending on the circuit configuration I have NC and NO in programs without considering the button on the panel, therefore make appropriate changes to the code according to the contact on panel.]

<br>

In Mitshubishi, input ports are represented/labelled as X0, X1, X2, X3, .... and output ports are represented/labelled as Y0, Y1, Y2,...

