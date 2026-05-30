1. Introduction
# UART stands for: Universal Asynchronous Receiver Transmitter
It is a hardware communication peripheral used to exchange data between two devices.
Communication Type
UART is: Serial Communication
because data is transferred: One bit at a time
Example: 10110010
Bits are transmitted sequentially.

# Asynchronous Communication
UART does not use: Clock Signal between transmitter and receiver.
Unlike:
SPI
I²C
there is no separate clock line.

# UART Uses Only Two Main Signals
TX (Transmit)
RX (Receive)

Example:
MCU1 TX -----> MCU2 RX

MCU1 RX <----- MCU2 TX

# Common Applications
UART is widely used for:
Microcontroller Communication
GPS Modules
Bluetooth Modules
Wi-Fi Modules
PC Serial Communication
Debug Console
GSM Modems

Examples
STM32 ↔ PC
MSPM0 ↔ GPS
ESP32 ↔ GSM Module
MCU ↔ Bluetooth Module

# Why UART is Popular?
Because it is:
Simple
Low Cost
Easy to Implement
Requires Few Wires
Only:
TX
RX
GND
are usually required.

# Basic UART Communication

Example:
MCU1 sends: 0x55
UART converts it into serial bits:
Start Bit
Data Bits
Stop Bit
Receiver reconstructs: 0x55
from the received bits.

2. Why UART is Required
Before UART, devices needed many wires for communication.

Without UART
Suppose we want to send:
8-bit Data

Using parallel communication:
D0
D1
D2
D3
D4
D5
D6
D7

Need: 8 Data Wires
plus control signals.

Problems
More GPIO Pins
More PCB Routing
More Connectors
Higher Cost

With UART
Same data sent serially:
1 → 0 → 1 → 1 → 0 → 0 → 1 → 0
using only:
TX
RX

Example
MCU1 TX -----> MCU2 RX
MCU1 RX <----- MCU2 TX
Only two communication wires.

Advantages
Fewer Wires
Fewer GPIO Pins
Simple Hardware
Long Distance Communication
Easy PC Connection

Typical Usage
Debug Messages
printf("Temperature = 25");
sent to PC terminal through UART.

GPS Module
GPS ----UART---- MCU
GPS continuously sends location data.

Bluetooth Module
Bluetooth ----UART---- MCU
Wireless commands exchanged through UART.

# Comparison
Parallel
8-bit data = 8 wires

UART: (serial transmission)
8-bit data = 1 TX wire

3. UART Communication Type
UART communication can be classified as:
# a. Serial Communication
# b. Asynchronous Communication
# c. Full Duplex Communication

# a. Serial Communication
UART transfers data: One bit at a time

Example:
Data: 0xA5
Binary: 10100101

Transmission:
1 → 0 → 1 → 0 → 0 → 1 → 0 → 1
Bits are sent sequentially.

Why Called Serial?
Because: Only one bit travels at a time through the TX line.

# c. Asynchronous Communication
UART is: Asynchronous
because there is: No Clock Signal between transmitter and receiver.

Unlike:
SPI → SCLK
I²C → SCL

UART has: No Clock Wire

Then How Does Receiver Know Timing?
Both devices are configured with the same: Baud Rate

Example:
TX = 9600 baud
RX = 9600 baud
Both agree on bit timing before communication starts.

# Full Duplex Communication
UART supports: Full Duplex

Meaning: Transmit and Receive at the same time
Example
MCU1 TX -----> MCU2 RX
MCU1 RX <----- MCU2 TX
Both devices can exchange data simultaneously.

Example Scenario
MCU1 sends: Hello
while MCU2 sends: OK
at the same time.

This is possible because: Separate TX and RX lines exist.

# Comparison
UART
Full Duplex
Separate: TX & RX

I²C
Half Duplex
Shared: SDA

SPI
Full Duplex
using: MOSI & MISO

4. UART Signals (TX and RX)
UART communication mainly uses two signals:
TX (Transmit)
RX (Receive)

TX (Transmit)
TX means: Transmit Data
This pin sends data out of the device.

Example:
MCU TX: sends data to another device.

RX (Receive)
RX means: Receive Data
This pin receives incoming data.

Example:
MCU RX: receives data from another device.

# Connection Rule
Very important:
TX → RX
RX → TX

Example
Two microcontrollers:
MCU1 TX -----> MCU2 RX
MCU1 RX <----- MCU2 TX
Cross connection is required.

Wrong Connection
TX -----> TX
RX -----> RX
Result: No communication
because both TX pins try to transmit and both RX pins only listen.

Ground Connection
Besides TX and RX:
GND must also be connected.

Example:
MCU1 TX -----> MCU2 RX
MCU1 RX <----- MCU2 TX
MCU1 GND ---- MCU2 GND

Why GND is Needed?
Because both devices need the same:
Voltage Reference
Without common ground:
Communication may fail or become unreliable.

Basic UART Connection
MCU1              MCU2
TX  -----------> RX
RX <----------- TX
GND ---------- GND

# Data Direction
Transmission TX → RX
Data moves from transmitter to receiver.

Reception RX receives incoming bits and reconstructs the byte.

5. Transmitter and Receiver
UART communication always involves:
Transmitter (TX)
Receiver (RX)
One device sends data.
Another device receives data.

Transmitter
Purpose: Convert parallel data into serial data

Example:
CPU wants to send: 0xA5
Binary: 10100101

UART Transmitter converts it into:
Start Bit
Data Bits
Parity Bit (optional)
Stop Bit
and sends bits one by one on:

TX pin
Receiver
Purpose: Convert serial data into parallel data

Receiver gets bits from: RX pin and reconstructs: 0xA5 for the CPU.

Data Flow
Example:
CPU
 ↓
UART Transmitter
 ↓
TX Pin
 ↓
RX Pin
 ↓
UART Receiver
 ↓
CPU

What Happens During Transmission?
Suppose CPU writes: UART_TX = 0x55;

UART hardware:
1. Takes 0x55
2. Adds Start Bit
3. Adds Stop Bit
4. Sends bits serially through TX.

What Happens During Reception?
Receiver:
1. Detects Start Bit
2. Samples incoming bits
3. Checks Parity (if enabled)
4. Checks Stop Bit
5. Stores received byte

# Transmit Shift Register
Inside UART: Transmit Shift Register stores outgoing data.

Example: 10100101
Bits are shifted out one at a time.

Receive Shift Register
Inside UART: Receive Shift Register collects incoming bits.

Example:
1
0
1
0
0
1
0
1
After all bits arrive: 0xA5 reconstructed

# Why Use UART Hardware?
Without UART hardware: CPU would need to manually generate and sample every bit which is inefficient.

UART hardware performs:
Bit timing
Bit shifting
Error checking
automatically.

6. UART Connection
To establish UART communication, devices must be connected correctly.
Minimum Connections
UART requires:
TX
RX
GND

Basic Connection
MCU1               MCU2
TX  ----------->   RX
RX  <-----------   TX
GND ------------   GND

Rule:
TX → RX
RX → TX
GND → GND

Why Cross Connection?
Because:
TX sends data
RX receives data

Therefore:
Transmitter must connect
to Receiver
Wrong Connection
TX -----> TX
RX -----> RX

Result:
No communication

Why GND Must Be Connected?
UART uses voltage levels.
Example:
0V = Logic 0
3.3V = Logic 1
Both devices must share the same: Reference Ground
Otherwise voltage levels may be interpreted incorrectly.

2-Wire UART
Sometimes only one direction is needed.
Example:
GPS -----> MCU
Connection:
GPS TX -----> MCU RX
GND -------- MCU GND
Only receive path exists.

3-Wire UART
Most common UART connection.
TX
RX
GND

Example:
MCU TX -----> Module RX
MCU RX <----- Module TX
GND --------- GND

# MCU ↔ PC Connection
Example:
MCU
 ↓
USB-UART Converter
 ↓
PC Terminal

Common converters:
CP2102
FT232
CH340

Purpose:
Debug Messages
Data Logging
Firmware Testing

# MCU ↔ GPS
GPS TX -----> MCU RX
GPS RX <----- MCU TX
GND --------- GND

GPS sends:
Latitude
Longitude
Time Data

# MCU ↔ Bluetooth Module
Example:
HC-05
HC-06

Connection:
MCU TX -----> BT RX
MCU RX <----- BT TX
GND --------- GND
Commands exchanged using UART.

# MCU ↔ GSM Module
MCU TX -----> GSM RX
MCU RX <----- GSM TX
GND --------- GND

Used for:
AT Commands
SMS
Internet Communication

# Voltage Level Consideration
Important:
Both devices should use compatible voltage levels.

Example:
3.3V MCU
3.3V Module
Good.

But:
5V TX
3.3V RX
may require: Level Shifter

7. Simplex Communication
# What is Simplex?
Simplex communication means: Data flows in only one direction.

One device can: Transmit only
and the other can: Receive only

Communication Direction
Device A  --------->  Device B
Data flows only one way.

There is: No return path

Example
GPS -----> MCU
GPS continuously sends:
Location Data
Time Data
MCU only receives.

Other Examples
Radio Broadcast
TV Broadcast
Keyboard → PC
GPS → MCU

UART Example
Connection:
GPS TX -----> MCU RX
GND -------- MCU GND

Notice:
Only one TX-RX path exists.
No reverse communication.

Characteristics
One-way communication
Simple wiring
No acknowledgment
No response possible

Advantages
Simple Design
Less Wiring
Low Cost

Limitations
No Feedback
No Error Response
No Two-Way Communication

# Comparison
Simplex
A -----> B
Only one direction.

Half Duplex
A <----> B
One at a time

Full Duplex
A <====> B
Both directions simultaneously

8. Half Duplex Communication
Half Duplex communication means: Both devices can transmit and receive, but not at the same time.

Communication Direction
A -----> B
or
A <----- B
Only one direction is active at a time.

Example
Step 1:
A -----> B
A sends: Hello
B receives.

Step 2:
A <----- B
B sends: OK
A receives.

# Important Rule
Transmit OR Receive
Not Both Together

Walkie-Talkie Example
Most common example: Walkie-Talkie
One person presses the button and talks.
The other listens.
Then roles reverse.
Both cannot talk simultaneously.

UART Example
A single UART line shared for TX and RX.
MCU A <------> MCU B
One device transmits while the other receives.
Then direction changes.

# Characteristics
Two-way communication
One direction at a time
Shared communication path

Advantages
Less wiring
Supports two-way communication
Lower cost than Full Duplex

Limitations
Cannot transmit and receive simultaneously
Lower throughput than Full Duplex

# Comparison
Simplex
A -----> B
One direction only.

Half Duplex
A <----> B
Both directions.
One at a time.

Full Duplex
A <====> B
Both directions simultaneously.

9. Full Duplex Communication
What is Full Duplex?
Full Duplex communication means: Both devices can Transmit and Receive at the same time.
Communication Direction
A <====> B
Data flows in both directions simultaneously.

Example
Device A sends:
Hello to Device B.
At the same time,
Device B sends:
OK to Device A.
Both transfers happen simultaneously.

Why UART Supports Full Duplex?
UART uses:
Separate TX line
Separate RX line

Example:
MCU1 TX -----> MCU2 RX
MCU1 RX <----- MCU2 TX
Since transmit and receive paths are different:
TX and RX can work simultaneously.

Real Example
PC communicating with MCU:
PC  -----> MCU
MCU -----> PC

PC sends command: READ_TEMP
At the same time MCU can send: 25°C back to PC.

# Characteristics
Two-way communication
Simultaneous TX and RX
Higher throughput

# Advantages
Fast communication
No waiting for direction change
Efficient data transfer

# Limitations
Requires separate TX and RX paths
Slightly more wiring than Half Duplex

# Comparison
Simplex
A -----> B
One direction only.

Half Duplex
A <----> B
One direction at a time.

Full Duplex
A <====> B
Both directions simultaneously.

# Which Protocols Use Full Duplex?
UART: Yes
Separate TX and RX.

SPI: Yes
Uses: MOSI & MISO simultaneously.

I²C: No
Shared SDA line.
Therefore: Half Duplex

Memory Table
| Mode        | Communication                  |
| ----------- | ------------------------------ |
| Simplex     | One Direction                  |
| Half Duplex | Both Directions, One at a Time |
| Full Duplex | Both Directions Simultaneously |

10. Synchronous vs Asynchronous Communication
This is one of the most important UART concepts.
Synchronous Communication
Meaning: Communication uses a shared clock signal.
Transmitter and Receiver use the same clock.

Example
SPI
MOSI
MISO
SCLK
SCLK synchronizes data transfer.

I²C
SDA
SCL
SCL synchronizes communication.

Characteristics
Clock required
High speed possible
Timing controlled by clock

Asynchronous Communication
Meaning: No shared clock signal.
Transmitter and Receiver communicate using: Baud Rate agreement.

Example
UART
TX
RX
No clock line exists.

How Does Receiver Know Timing?
Both devices are configured with the same: Baud Rate

Example:
9600 baud
115200 baud

Start Bit Helps Synchronization
UART frame begins with: Start Bit
Receiver detects the start bit and starts timing the incoming bits.

# Comparison
Synchronous
Clock Present
SPI
I²C

Asynchronous
No Clock
UART

Example Analogy
Synchronous
Two people reading
from the same metronome.
Everyone follows the same timing source.

Asynchronous
Both people agree
to speak at the same speed.
No shared timing signal.

Summary Table
| Feature    | Synchronous  | Asynchronous |
| ---------- | ------------ | ------------ |
| Clock Line | Required     | Not Required |
| Timing     | Shared Clock | Baud Rate    |
| Example    | SPI, I²C     | UART         |
| Wiring     | More Wires   | Fewer Wires  |

11. What is Baud Rate
What is Baud Rate?
Baud Rate is: The number of symbols transmitted per second.
For UART, one symbol usually represents one bit.

Therefore: Baud Rate ≈ Bits per Second (bps) for normal UART communication.

Simple Definition
Number of bits transmitted per second.

Example: 9600 Baud
9600 baud
means: 9600 bits transmitted every second.

Example: 115200 Baud
115200 baud
means: 115200 bits transmitted every second.
Communication is faster than 9600 baud.

Why Baud Rate is Important?
Transmitter and Receiver must use: Same Baud Rate
Example:
TX = 9600 baud
RX = 9600 baud
Communication works correctly.

Wrong Baud Rate Example
TX = 9600
RX = 115200

Result:
Garbage Data
Communication Failure
because receiver samples bits at the wrong time.

Common Baud Rates
1200
2400
4800
9600
19200
38400
57600
115200

# Bit Time
Bit Time means: Time required to transmit one bit.
Formula:
Bit Time = 1 / Baud Rate

Example
9600 Baud
Bit Time
= 1 / 9600
≈ 104.17 µs
One bit takes approximately: 104 µs

115200 Baud
Bit Time
= 1 / 115200
≈ 8.68 µs
One bit takes approximately: 8.68 µs

Effect of Increasing Baud Rate
Higher Baud Rate:
More Speed
Less Time per Bit

Lower Baud Rate:
Less Speed
More Time per Bit

Practical Examples
GPS Modules
Often: 9600 baud

Debug Console
Often: 115200 baud

Bluetooth Modules
Often: 9600 baud or 115200 baud


12. Bit Rate vs Baud Rate
This is a commonly confused concept.
Bit Rate
Bit Rate means: Number of bits transmitted per second.
Unit: bps
(bits per second)

Baud Rate
Baud Rate means: Number of symbols transmitted per second.
Unit: baud

In UART
Normally: 1 Symbol = 1 Bit
Therefore: Bit Rate = Baud Rate

Example
9600 baud
means: 9600 symbols/sec
Since: 1 symbol = 1 bit
Bit Rate becomes: 9600 bps

Another Example
115200 baud
Then: Bit Rate = 115200 bps

Why Are They Different Terms?
In some communication systems:
1 Symbol can represent
multiple bits.

Example:
1 Symbol = 2 Bits
Then: 
Bit Rate = Baud Rate × 2
But this is not normal UART.

Interview/Practical Answer
For UART: Bit Rate ≈ Baud Rate
because: 1 symbol carries 1 bit.

Summary Table
| Parameter     | Meaning              |
| ------------- | -------------------- |
| Bit Rate      | Bits per second      |
| Baud Rate     | Symbols per second   |
| UART Relation | Bit Rate = Baud Rate |

13. Common Baud Rates
What are Common Baud Rates?
These are standard transmission speeds widely supported by:
Microcontrollers
PC Serial Ports
GPS Modules
Bluetooth Modules
GSM Modems

Common Values
1200
2400
4800
9600
19200
38400
57600
115200

Most Common Baud Rates
9600
Reliable
Widely Supported
Easy to Debug
Often used in:
GPS Modules
Bluetooth Modules

Industrial Devices
115200
Much Faster
Very Common for Debugging
Often used in:
STM32
ESP32
MSPM0
Debug Consoles

Speed Comparison
| Baud Rate | Relative Speed |
| --------- | -------------- |
| 9600      | Slow           |
| 19200     | 2× Faster      |
| 38400     | 4× Faster      |
| 57600     | 6× Faster      |
| 115200    | 12× Faster     |

Compared to: 9600 baud

Bit Time Comparison
9600 Baud
1 / 9600
≈ 104 µs

115200 Baud
1 / 115200
≈ 8.68 µs
Much faster bit transmission.

Why Not Always Use Maximum Baud Rate?
Higher speed means:
Less timing margin
More sensitivity to noise
More chance of communication errors

Lower speed means:
More reliable
Longer communication distance

# Practical Selection
GPS
Often: 9600 baud
because data rate is low.

Debug Messages
Often: 115200 baud
because many messages are transmitted.

Bootloader Communication
Often: 115200 baud
for faster firmware transfer.

# Important Rule
Both devices must use:
Same Baud Rate
Example:
TX = 115200
RX = 115200
Works correctly.

Wrong:
TX = 9600
RX = 115200
Result: Garbage Data

14. UART Frame Format
UART does not send raw bytes directly.
The UART hardware adds extra bits around the data.
This complete structure is called:
UART Frame

Basic UART Frame
Start Bit
Data Bits
Parity Bit (Optional)
Stop Bit

Example Frame
Suppose we want to send: 0x55
Binary: 01010101

UART transmits:
Start
Data Bits
Stop
not just raw data bits.

# Frame Structure
Typical UART frame:
| Start | Data | Parity | Stop |

Start Bit
Purpose: Indicates beginning of transmission.
Usually: Logic 0

Data Bits Actual user data.
Typically: 8 bits
Common options:
5-bit
6-bit
7-bit
8-bit
9-bit
Most common:
8-bit

Parity Bit (Optional)
Used for: Basic error detection.
Can be:
Even Parity
Odd Parity
or disabled.

Stop Bit
Purpose: Indicates end of frame.
Usually:
Logic 1
Common options:
1 Stop Bit
2 Stop Bits

# Typical UART Configuration
Very common configuration: 8N1
Meaning:
| Part | Meaning     |
| ---- | ----------- |
| 8    | 8 Data Bits |
| N    | No Parity   |
| 1    | 1 Stop Bit  |

Example: 8N1 Frame
Transmit: 0x55
Binary: 01010101
Frame becomes: Start + Data + Stop
Example:
0 01010101 1

Idle State
When no communication occurs: UART line stays HIGH

Important.
Therefore:
Start Bit = HIGH → LOW transition
Receiver detects this transition.

Total Bits in 8N1
1 Start Bit
8 Data Bits
1 Stop Bit

Total: 10 bits transmitted for every 8-bit data byte.

Why Extra Bits Are Needed?
Start Bit Synchronizes receiver timing.
Stop Bit Marks end of frame.
Parity Bit Detects transmission errors.

UART Frame Example
Data 0x41
ASCII: 'A'
Binary: 01000001
8N1 Frame: 0 01000001 1

Memory Trick
UART Idle = HIGH

Start Bit = LOW

Stop Bit = HIGH

15. Start Bit
What is Start Bit?
The Start Bit indicates: Beginning of a UART frame.
It tells the receiver: New data is coming.

Start Bit Value
The Start Bit is always: Logic 0(Line pulled LOW)

UART Idle State
Before transmission:
UART line remains HIGH.

Example:
───────────────
HIGH HIGH HIGH
No data is being sent.

Start of Communication
When transmission begins: Line changes

HIGH → LOW
This LOW period is the Start Bit.

Timing Example
Idle     Start

HIGH     LOW

───────┐
       │
       └────

Receiver continuously monitors RX.
When it detects: HIGH → LOW
it recognizes: Start Bit Detected  

Why Start Bit is Needed?
Because UART has: No Clock Signal
The receiver must know: Exactly when a frame starts.
The Start Bit provides this synchronization point.

What Happens After Detection?
a. Receiver: Detects Start Bit
b. Starts internal timer
c. Samples incoming bits according to baud rate

Example
Transmit: 0x55
Frame:
Start
Data
Stop

Example bits: 0 01010101 1
The first: 0 is the Start Bit.

Important Rule
Only: One Start Bit per UART frame.
Summary
Idle State = HIGH
Start Bit = LOW
Start Bit marks beginning of frame
Receiver detects HIGH→LOW transition

Memory Trick
Idle = HIGH
Start = LOW
HIGH → LOW = Start Bit

16. Data Bits
Data Bits contain: Actual user data being transmitted.
Example:
ASCII Character
Sensor Data
Command
Variable Value

Position in UART Frame
Start Bit
Data Bits
Parity Bit (Optional)
Stop Bit
Data Bits come immediately after the Start Bit.

Number of Data Bits
UART can support:
5-bit
6-bit
7-bit
8-bit
9-bit

Most common: 8-bit

Example
Transmit: 0x55
Binary: 01010101
These 8 bits become the Data Bits field.

# UART Sends LSB First
This is very important.
UART transmits: LSB First
not MSB First.

Example
Data: 0x55
Binary: 01010101
Bit positions:
Bit7 Bit6 Bit5 Bit4 Bit3 Bit2 Bit1 Bit0

 0    1    0    1    0    1    0    1
                                    ↑
                                   LSB

Transmission order:

1 → 0 → 1 → 0 → 1 → 0 → 1 → 0
Starts from: Bit0
ends at: Bit7                                   

Another Example
Data: 0x41
Binary: 01000001
Transmission order:
1 0 0 0 0 0 1 0
Again: LSB First

Why LSB First?
This is defined by the UART protocol.
Receiver expects: LSB First
therefore transmitter sends: LSB First

Frame Example
8N1 configuration.
Transmit: 0x55
Frame:
Start
1 0 1 0 1 0 1 0
Stop

Notice: Data starts with Bit0.

Memory Trick
I²C → MSB First
SPI → Usually MSB First
UART → LSB First

17. Parity Bit
Parity Bit is an optional bit used for: Error Detection during UART communication.
It helps detect: Single-bit transmission errors
Position in UART Frame
Start Bit
Data Bits
Parity Bit
Stop Bit
Parity Bit comes after the Data Bits.

# Is Parity Mandatory?
No
Parity can be:
Disabled
Even Parity
Odd Parity

# Most common configuration: 8N1
where: N = No Parity

# Even Parity
Rule: Total number of 1's must be EVEN.

Example 1
Data: 0x03
Binary: 00000011
Number of 1's: 2
Already even.

Therefore:
Parity Bit = 0
Total 1's remain: 2 (Even)

Example 2
Data: 0x07
Binary: 00000111
Number of 1's: 3
Odd.

Need total to become even.
Therefore: Parity Bit = 1
Now: 4 ones (Even)

# Odd Parity
Rule: Total number of 1's must be ODD.
Example 1
Data: 00000011
Number of 1's: 2
Even.
Need odd total.

Therefore:
Parity Bit = 1
Total becomes: 3 ones (Odd)

Example 2
Data: 00000111
Number of 1's: 3
Already odd.

Therefore:
Parity Bit = 0

# How Receiver Uses Parity
Receiver: Counts received 1's
Checks parity rule
Reports parity error if mismatch occurs

# Error Example
Transmit: 00000011
Even parity:
Parity = 0
Expected total: 2 ones (Even)
Suppose noise changes one bit:
Received: 00000111
Now total: 3 ones (Odd)
Receiver detects: Parity Error

# Limitation of Parity
Parity can: Detect many single-bit errors
but cannot reliably detect: All multiple-bit errors

Memory Trick
Even Parity
→ Total 1's Even

Odd Parity
→ Total 1's Odd

Parity
→ Detects Errors
Does Not Correct Errors

18. Stop Bit
Stop Bit indicates: End of UART frame.
It tells the receiver:Data transmission is complete.
Stop Bit Value
Stop Bit is always: Logic 1 (Line HIGH)
Position in UART Frame
Start Bit
Data Bits
Parity Bit (Optional)
Stop Bit
Stop Bit is the last field of the frame.

Example (8N1)
Transmit: 0x55
Frame: 0 10101010 1
Where: 0 = Start Bit
10101010 = Data Bits
1 = Stop Bit

Why Stop Bit is Needed?
Receiver must know: Frame has ended and communication is complete.
Without Stop Bit: Receiver cannot reliably detect frame boundary.

Relationship with Idle State
Remember: UART Idle State = HIGH
Stop Bit is also: HIGH
Therefore after transmission: Line naturally returns to idle state.

One Stop Bit
Most common configuration:
8N1
Meaning:
8 Data Bits
No Parity
1 Stop Bit

Two Stop Bits
Configuration:
8N2
Meaning:
8 Data Bits
No Parity
2 Stop Bits

Frame:
Start
Data
Stop
Stop

Why Use Two Stop Bits?
Provides: More time for receiver to process received data.
Useful for:
Slow devices
Older systems
Effect on Speed

More Stop Bits means: More bits transmitted per frame
Therefore: Lower effective throughput

Example
8N1
1 Start
8 Data
1 Stop
Total = 10 Bits

8N2
1 Start
8 Data
2 Stop
Total = 11 Bits

Receiver Check
Receiver expects: Stop Bit = HIGH
If it reads: LOW instead,
UART generates: Framing Error

# Memory Trick
Idle = HIGH
Stop Bit = HIGH
Start Bit = LOW

19. Idle State of UART Line
What is Idle State?
Idle state means: No UART transmission is occurring.
Nothing is being sent.
Nothing is being received.

UART Idle Level
UART line remains: Logic HIGH (1) during idle condition.

Example
Before transmission:
TX = HIGH

Waveform:
───────────────
HIGH HIGH HIGH
This is the idle state.

Why HIGH?
UART protocol defines: Idle = HIGH and Start Bit = LOW
This allows the receiver to easily detect:
HIGH → LOW transition
which indicates the start of a new frame.

# Start of Communication
Idle: HIGH
Start Bit: LOW
Transition: HIGH → LOW
Receiver detects: Start Bit and begins receiving data.

# End of Communication
Stop Bit: HIGH
After Stop Bit: Line remains HIGH again. 
This becomes: Idle State

Example Frame
8N1:
Idle
Start
Data
Stop
Idle
Waveform concept:
HIGH -----
         |
         ↓
LOW  (Start)

Data Bits

HIGH (Stop)

HIGH HIGH HIGH
(Idle)

Why is Idle State Important?
Receiver continuously monitors RX.
When RX is: HIGH
Receiver knows: No frame is being transmitted.
When RX changes: HIGH → LOW
Receiver knows: New frame started.

# Practical Debugging
If you connect an oscilloscope to TX:
When no data is transmitted: Line should stay HIGH.
If line stays LOW:
Possible issues: Wrong wiring
Stuck transmitter
UART configuration issue

Memory Trick
Idle = HIGH
Start = LOW
Stop = HIGH
HIGH → LOW
= Start Detection

20. UART Transmission Example
Assume UART configuration: 8N1
8 Data Bits
No Parity
1 Stop Bit

Step 1: Data to Transmit 0xF0
Binary: 11110000

Bit positions:
Bit7 Bit6 Bit5 Bit4 Bit3 Bit2 Bit1 Bit0

 1    1    1    1    0    0    0    0

Step 2: UART Sends LSB First
UART always transmits: LSB First
Therefore transmission order becomes:
Bit0
Bit1
Bit2
Bit3
Bit4
Bit5
Bit6
Bit7

Values:
0
0
0
0
1
1
1
1

Step 3: Add Start and Stop Bits
Start Bit: 0
Stop Bit: 1

Complete frame:
Start
0 0 0 0 1 1 1 1
Stop

So transmitted bits are:
0 | 0 0 0 0 1 1 1 1 | 1

Total Bits
1 Start
8 Data
1 Stop
Total: 10 Bits

Timing Example (9600 Baud)
Bit time:
1 / 9600
≈ 104 µs
Each bit lasts: 104 µs

Receiver Operation
Receiver sees: HIGH → LOW
Detects: Start Bit
Then samples:
0
0
0
0
1
1
1
1

Reconstructs:
11110000
which is: 0xF0
Then checks: 
Stop Bit = HIGH
Frame accepted.

Simple Waveform
Idle  Start  D0 D1 D2 D3 D4 D5 D6 D7 Stop Idle
 1      0    0  0  0  0  1  1  1  1   1    1

Notice: Four LOW bits
followed by Four HIGH bits

because: 0xF0 = 11110000
UART sends LSB first

21. UART Reception Example
Now we'll see how the receiver converts serial bits back into a byte.
Received Frame
Suppose RX line receives:
0 | 0 0 0 0 1 1 1 1 | 1

Meaning: Start Bit
Data Bits
Stop Bit

Step 1: Detect Start Bit Receiver continuously monitors RX.
Idle state: HIGH
Suddenly: HIGH → LOW
Receiver detects: Start Bit and starts its baud-rate timer.

Step 2: Sample Data Bits
Receiver reads bits at fixed intervals.

Received bits:
0
0
0
0
1
1
1
1

Remember:
UART receives LSB First
So:
Bit0 = 0
Bit1 = 0
Bit2 = 0
Bit3 = 0
Bit4 = 1
Bit5 = 1
Bit6 = 1
Bit7 = 1

Step 3: Reconstruct Byte
Receiver places bits back into normal order:
Bit7 Bit6 Bit5 Bit4 Bit3 Bit2 Bit1 Bit0
 1    1    1    1    0    0    0    0

Binary: 11110000
Hex: 0xF0

Step 4: Check Stop Bit
Receiver expects: HIGH for Stop Bit.
If received: HIGH
Frame is valid.

Step 5: Store Data
Receiver stores: 0xF0 in UART receive register.
CPU can now read it.

Example:
data = UART_Read();

Result: data = 0xF0

Full Reception Flow
Detect Start Bit
        ↓
Sample Data Bits
        ↓
Check Parity (if enabled)
        ↓
Check Stop Bit
        ↓
Store Byte
        ↓
CPU Reads Data

Example 2
Received frame: 0 | 1 0 0 0 0 0 0 0 | 1
Data bits received: 1 0 0 0 0 0 0 0

LSB First means:
Bit0 = 1
Others = 0

Result: 00000001 = 0x01

Memory Trick
Start Detected
↓
Read Bits
↓
Check Parity
↓
Check Stop
↓
Store Byte

22. UART Timing Diagram Analysis

23. Parity Error

24. Framing Error

25. Overrun Error

26. Break Condition

27. UART Buffer / FIFO

28. Polling Based UART

29. Interrupt Based UART

30. DMA Based UART

31. Flow Control Introduction

32. Hardware Flow Control (RTS/CTS)

33. Software Flow Control (XON/XOFF)

34. UART Configuration Parameters

35. UART Initialization Example

36. UART Debugging Techniques

37. Logic Analyzer UART Decoding

38. UART Advantages

39. UART Limitations

40. UART vs SPI

41. UART vs I²C

42. UART vs USART

43. USART Synchronous Mode

44. Questions & Answers

45. USART Clock Signal (CK)

46. USART Synchronous Frame Format

47. USART Master and Slave Operation

48. USART Clock Polarity and Phase

49. USART Advantages

50. USART Limitations

51. UART vs USART (Detailed)