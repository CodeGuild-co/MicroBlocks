# MicroBlocks
# ==========

## The Brief:
The brief:
- to create containers for micro:bits to communicate and connect to each other physically
- only using materials from a supermarket
- keep it cheap

## Table of Contents
* [Design Brief](#design-brief)
* [Block Design ](#block-design)
* [Connections ](#connections)
* [Gates](#gates)
* [And Gates](#and-gates)
* [Or Gates ](#or-gates)
* [Not Gates](#not-gates)
* [Connections](#connections)
* [The Combined And and Not Gate](#the-combined-and-and-not-gate)
* [Team](#team)



## Design Brief

We needed specific blocks for each component involved in the design. We need a modular design for each block (i.e. two inputs and one output box). This will ensure that each block is designed specifically for its purpose and makes it more intuitive for the end user.

## Block Design

To simulate logic gates (`Or Gate`/`And Gate`/`Not Gate` etc.), we need inputs to represent the binary inputs. The inputs only require one output terminal, also communicating in binary, using a method called digital read. To connect the blocks we need a common ground terminal. Therefore, the input blocks require a ground terminal because they each will only have one side that connects to another component.
Most of the gates require two inputs to give a separate single output, but it is more convenient to supply two outputs, and two ground terminals. The gates will have a total of 8 terminals, however, the Not Gates will have a total of 4 terminals: an input, an output, and two ground terminals.

To allow the user to see the LED matrix, we cut out a slice from the net to provide a transparent area.  There is also a magnet behind each terminal to ensure a strong and easy connection. This will also cause the wrong sides to repel, making it more intuitive for the end user.


## Connections

Using magnetic tabs, tinfoil and sellotape, we are able to create physical connections that conduct electricity across the micro:bits. Although using wire would have been safer, as it is more insulated than tin foil, the latter is cheaper and more easily accessed, therefore it is more fitting to the brief of the design.


## Gates

In total, there are three gates: AND, OR and NOT. The AND gate takes in two inputs, either a 0 or a 1, and the condition is that they both have to equal 1 in order to output a 1. The OR gate ensures that if either input is a 1, the output will be 1. The NOT gate includes only one input. If this is a 1, the output will be 0 and vice versa.
Truth table for the AND gate:

| Input 1        | Input 2          | Output  |
| ------------- |:-------------:| -----:|
| 0     | 0     | `0`      |
| 0     | 1     | `0`     |
| 1     | 0     | `0`     |
|1      | 1     | `1`     |


Truth table for the OR gate:

| Input 1        | Input 2          | Output  |
| ------------- |:-------------:| -----:|
| 0     | 0     | `0`      |
| 0     | 1     | `1`     |
| 1     | 0     | `1`     |
|1      | 1     | `1`     |

Truth table for the NOT gate:

| Input 1        | Output  |
| ------------- | -----:|
| 0     | `0`     |
|1      | `1`     |



## Inputs

Code for the Inputs:
```js
let qrt = 0
input.onButtonPressed(Button.AB, () => {
    if (qrt == 100) {
        qrt = 0
    } else {
        qrt = 100
    }
})
basic.forever(() => {
basic.clearScreen()
while (qrt == 0) {
    if (input.buttonIsPressed(Button.A)) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
        . . # . .
        . # # . .
        . . # . .
        . . # . .
        . # # # .
        `)
    } else if (input.buttonIsPressed(Button.B)) {
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.showLeds(`
        . . # . .
        . # . # .
        . # . # .
        . # . # .
        . . # . .
        `)
    }
    }
})
```

## And Gates

Code for the And Gates:
```js
let qrt = 10
input.onButtonPressed(Button.AB, () => {
    if (qrt == 10) {
        qrt = 0
    }
    else {
        qrt = 10
    }

})

basic.forever(() => {
    basic.clearScreen()
    while (qrt == 10) {
    if (pins.digitalReadPin(DigitalPin.P1) == 1 && pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
        . . # . .
        . # # . .
        . . # . .
        . . # . .
        . # # # .
        `)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.showLeds(`
        . . # . .
        . # . # .
        . # . # .
        . # . # .
        . . # . .
        `)
    }
    }
})


```





## Or Gates

The code for the Or Gates

```js
let qrt = 0
input.onButtonPressed(Button.AB, () => {
if (qrt == 100) {
        qrt = 0
    } else {
        qrt = 100
    }
})
basic.forever(() => {
    basic.clearScreen()
    while (qrt == 100) {
        if (pins.digitalReadPin(DigitalPin.P1) == 0 && pins.digitalReadPin(DigitalPin.P2) == 0) {
            pins.digitalWritePin(DigitalPin.P0, 0)
            basic.showLeds(`
            . . # . .
            . # . # .
            . # . # .
            . # . # .
            . . # . .
            `)
        } else {
            pins.digitalWritePin(DigitalPin.P0, 1)
            basic.showLeds(`
            . . # . .
            . # # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        }
    }
})




```

## Not Gates

The Code For the Not Gates:
``` js
let qrt = 0
input.onButtonPressed(Button.AB, () => {
    if (qrt == 10) {
        qrt = 0
    } else {
        qrt = 10
    }
})
qrt = 10
basic.forever(() => {
    basic.clearScreen()
    while (qrt == 10) {
    if (pins.digitalReadPin(DigitalPin.P1) == 0) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
        . . # . .
        . # # . .
        . . # . .
        . . # . .
        . # # # .
        `)
    } else {
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.showLeds(`
        . . # . .
        . # . # .
        . # . # .
        . # . # .
        . . # . .
        `)
    }
    }
})
```
## The Combined And and Not Gate
The code for the combined And and Not gates:
```js
let qrt = 0
let gate = 0
input.onButtonPressed(Button.A, () => {
    if (gate == 0) {
        gate = 1
    } else {
        gate = 0
    }
})
input.onButtonPressed(Button.B, () => {
    if (qrt == 100) {
        qrt = 0
    } else {
        qrt = 100
    }
})
basic.forever(() => {
basic.clearScreen()
while (qrt == 100) {
    while (gate == 1 && qrt == 100) {
        if (pins.digitalReadPin(DigitalPin.P1) == 0 && pins.digitalReadPin(DigitalPin.P2) == 0) {
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.showLeds(`
        . . # . .
        . # . # .
        . # . # .
        . # . # .
        . . # . .
        `)
            } else {
                pins.digitalWritePin(DigitalPin.P0, 1)
                basic.showLeds(`
                . . # . .
                . # # . .
                . . # . .
                . . # . .
                . # # # .
                `)
            }
        }
    while (gate == 0 && qrt == 100) {
        if (pins.digitalReadPin(DigitalPin.P1) == 1 && pins.digitalReadPin(DigitalPin.P2) == 1) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
        . . # . .
        . # # . .
        . . # . .
        . . # . .
        . # # # .
        `)
            } else {
                pins.digitalWritePin(DigitalPin.P0, 0)
                basic.showLeds(`
                . . # . .
                . # . # .
                . # . # .
                . # . # .
                . . # . .
                `)
            }
        }
    }
})

```

## The Finished Product
￼![alt text](https://github.com/CodeGuild-co/MicroBlocks/blob/master/IMG_3944.jpeg)
￼![alt text](https://github.com/CodeGuild-co/MicroBlocks/blob/master/IMG_3945.jpeg)
￼![alt text](https://github.com/CodeGuild-co/MicroBlocks/blob/master/IMG_3946.jpeg)

Team:
- Halle Gordon-Jeary
- Orla Brimacombe
- Asma Mansur
- Jeevan Dominguez
- [Almaz Ahmad](https://github.com/sp1d5r)

