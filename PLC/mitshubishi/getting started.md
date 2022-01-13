# Getting started

The software in discussion is GX works 3, since we are using FX series controller for testing. If you are working with Q series controllers use GX works 2.

### Create new project

```
project -> new 
```
- select the CPU series 
- select the model type
- then select the program language

PLC can be programmed with languages such as Ladder diagram, Function block diagram, Sequencial flow chart, Instruction list, Structural text.

### Enable remote reset 

To reset the controller from GX works, while downloading a new program to the controller, you need to enable remote reset.

```
navigation -> parameter -> fx 5u cpu -> cpu parameter -> operation related setting -> remote reset setting -> enable
```

### programing tab

```
naviation -> program -> scan -> main -> ProgPou -> programbody
```

### Convert

To compile the program on ProgPou (Program Optimization Unit), which comprises of program body and local labels, to need to convert the program

```
convert -> convert(B) or press F4
```

### Write to PLC

After completing the program and converting it, the next part will be uploadinf the code to PLC. This can be called downloading to PLC depending on manufacturer because everything in IDE is written from PLC prespective.

```
write to plc -> parameter+program/select all ->execute
```

'Select all' to upload comments too which is recommended for ease of understanding for other programmers while working on plc 

https://ie3a.mitsubishielectric.com/fa/en/dl/10994/sh081215.pdf