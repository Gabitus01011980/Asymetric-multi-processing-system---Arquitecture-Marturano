

# Reasons

All computer systems used today and for more than forty years are based on Harvard or Von Newmann-type architectures, which are sequential systems. This means that they process one instruction at a time. Anyone who wants to delve deeper into these architectures should search the Internet and will find enough information. In order to give the sensation of performing multiple tasks at the same time, they work at very high speeds, taking turns giving spaces of time and memory to the different tasks that are being executed. The problem with these architectures is that currently the volumes of data that are processed are very large. To compensate for these problems, the design of multiple cores and the use of graphics processing boards has been used. These chips (both the central processor with its multiple cores and the graphics cards) work at the speed limit, with the semiconductor crystals reaching temperatures of 90 degrees. This implies two things: 1 \- This heat must be dissipated, which requires extra electrical consumption by cooling equipment.  2 \- This heat means energy consumed and wasted. 

# Overview

An asymmetric multiprocessing system would better manage tasks since it would assign different hardware stages to different threads.   
The concept of this architecture is that there is no central processor and the processing is delegated to each of the peripherals that begin to perform their specific task as if they were firmware objects; That is to say, each peripheral has the resources to deal with the information that it is responsible for processing. 

Of course: there are two special devices that manage the entire flow of information that flows from one peripheral to another and these are the **interconnection matrix** and the **communications manager** . Device states can be referred to as if they were firmware objects, questions can be asked through messages, and serviceable responses can be received in the form of events and properties. These two devices can manage a small group of peripherals and in the total system there may be more than one pair, each managing a set of its own peripherals. The groups are interconnected with each other through an output port that would be another type of peripheral. 

\-

The idea is to decentralize the operation of the system and let the peripheral devices interact with each other without the arbitration of a central processor. There is no central processor in this architecture.   
The peripheral devices dialogue with each other by communicating with each other through an interconnection matrix governed by an arbitration device. The latter keeps track of what and how many devices exist in the system.   
The peripherals have the “intelligence” necessary for communication with other peripherals, functioning as firmware using object programming type protocols. That is to say, the peripherals are firmware objects to which questions can be asked that will be attended to as events by them. In turn, the answers will be given in the form of messages sent to the peripherals that asked the question or to others as required. 

# Overview of main peripherals

## Console

Consisting of a screen and a keyboard, it is the most basic way to enter data (although not the only one).  
It is an ASCII type terminal whose function is to create the human-machine interface.   
However, it has the intelligence to corroborate that what is written has the appropriate format to be understood by the rest of the system.   
It works in two modes: 

1 \- Direct connection with any peripheral in the system. This mode is used to test the operation of the specific peripheral. As its name indicates, only the peripheral and the console are connected and you do not have to go through the **communications manager** nor for the **interconnection matrix** , unless these are the devices to be tested. 

2 \- Connection to the system in a standard way. This is the definitive way to connect to a working system. 

The console analyzes the text typed on the line before it is sent since it must know what device it is dealing with. For this, at the time of its first connection, the console sends a message to the peripheral to which it is connected so that it responds with an **identification code** . Once it has this code it knows what messages it can send in order to be understood by the peripheral.

Each peripheral has its set of messages, events and properties corresponding to its type that are identified with its **identification code** . 

## Communications administrator

It is responsible for keeping records of the communications channels that interconnect the different devices.   
When a device connects for the first time, it sends an **identification code** to the system. Thus this code is received by the **communication manager** that schedules the availability of this device so that when someone requires its use, the communication administrator assigns them a direct communication route through the **communications matrix** . The duration of the communication can last only during the sending of the message or during the transfer of a data stream after which the communication manager must be notified of the completion of the transfer so that the device is available for future requests. 

## Interconnection Matrix

This is controlled by the communications manager and has a series of hardware channels for the interconnection of different devices. The nature of the connections is not discussed in this treatise but can be parallel (very complex for hardware design), i2c, spi or USART. Basically it is a chip that has inputs and outputs that are connected to the different devices that make up the system and that are added according to the needs of the system designer.   
It has three channels that fulfill the following special functions:

1 \- channel to console   
2 \- channel to communications manager  
3 \- system output channel

The system output channel serves to connect different sets of systems to each other in order to be expanded if necessary. 

## How to design different smart peripherals 

It is possible to use microcontrollers that have already existed on the market for a long time and that have peripherals with their corresponding libraries to design intelligent peripherals. The ideal would be to use CPLDs that would provide better speed, but microprocessors are an economical and fast option. For example, a smart peripheral device would be an Ethernet network connection. There are network management boards on the market to use with Arduino such as the w5100 or similar. This system does not require too much effort for the development of the intelligent peripheral, it is an economical option and easy to develop.   
In the same way it is possible to develop a whole plethora of devices that would not require a large development effort.   
In this regard, it is necessary to note the need to form an organization in charge of standardizing the identification codes of the peripherals and the set of messages, properties and events that they possess. 

For more information: gabitus01011980@gmail.com  
