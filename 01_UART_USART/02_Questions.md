1. What does UART stand for?
Universal Asynchronous Receiver Transmitter

2. Is UART serial or parallel communication?
Serial communication

3. Does UART require a clock line?
No, UART is asynchronous.

4. Which signals are mainly used in UART?
TX
RX

5. Name some UART applications.
GPS
Bluetooth
GSM
PC Communication
Debug Console

6. Why is UART preferred over parallel communication?
Requires fewer wires and fewer GPIO pins.

7. Which two communication lines are mainly used in UART?
TX and RX

8. Give examples of devices commonly connected through UART.
GPS
Bluetooth
GSM
PC

9. What is the main advantage of UART?
Simple communication using only a few wires.

10. Is UART serial or parallel communication?
Serial communication

11. Why is UART called asynchronous?
No clock signal is used between transmitter and receiver.

12. How do UART devices synchronize without a clock?
Both devices use the same baud rate.

13. Is UART full duplex?
Yes

14. Why is UART full duplex?
Separate TX and RX lines allow simultaneous transmission and reception.

15. What is the baud rate of UART?
Baud rate is the number of bits per second.

16. What does TX stand for?
Transmit

17. What does RX stand for?
Receive

18. How should two UART devices be connected?
TX → RX
RX → TX
GND → GND

19. Why is GND connection required?
To provide a common voltage reference between devices.

20. What happens if TX is connected to TX?
Communication will not work.

21. What is the function of the UART transmitter?
Convert parallel data into serial data and transmit it.

22. What is the function of the UART receiver?
Convert serial data into parallel data and receive it.

23. Which pin is used for transmission?
TX

24. Which pin is used for reception?
RX

25. Why are shift registers used in UART?
To shift data bit-by-bit during transmission and reception.

26. What are the minimum UART connections?
TX
RX
GND

27. How should TX and RX be connected?
TX → RX
RX → TX

28. Why is GND connection required?
To provide a common voltage reference.

29. Name some devices commonly connected through UART.
PC
GPS
Bluetooth
GSM

30. Why must voltage levels be checked?
To prevent communication failure or device damage.

31. What is Simplex communication?
Communication in which data flows only in one direction.

32. Can the receiver send data back in Simplex communication?
No

33. Give examples of Simplex communication.
GPS → MCU
Radio Broadcast
TV Broadcast

34. What is the main advantage of Simplex communication?
Simple implementation with minimal wiring.

35. What is the limitation of Simplex communication?
No feedback or response path.

36. What is Half Duplex communication?
Communication in which both devices can transmit and receive,
but not simultaneously.

37. Can both devices transmit at the same time in Half Duplex?
No

38. Give an example of Half Duplex communication.
Walkie-Talkie

39. What is the main limitation of Half Duplex?
Transmission and reception cannot occur simultaneously.

40. What is Full Duplex communication?
Transmit and receive simultaneously.

41. Why is UART Full Duplex?
Because UART uses separate TX and RX lines.

42. Is SPI Full Duplex?
Yes

43. Is I²C Full Duplex?
No, I²C is Half Duplex.

44. What is the main advantage of Full Duplex?
Simultaneous transmission and reception.

45. What is Synchronous communication?
Communication using a shared clock signal.

46. What is Asynchronous communication?
Communication without a shared clock signal.

47. Is UART synchronous or asynchronous?
Asynchronous

48. How does UART synchronize data without a clock?
sing the same baud rate at transmitter and receiver.

49. Give examples of synchronous communication.
SPI & I²C

50. What is Baud Rate?
Number of bits transmitted per second.

51. Why must TX and RX use the same baud rate?
To ensure correct bit timing and data reception.

52. What is the bit time at 9600 baud?
≈104 µs

53. Which is faster: 9600 or 115200 baud?
115200 baud

54. What happens if transmitter and receiver use different baud rates?
Communication errors or garbage data.

55. What is Bit Rate?
Number of bits transmitted per second.

56. What is Baud Rate?
Number of symbols transmitted per second.

57. In UART, what is the relationship between Bit Rate and Baud Rate?
Bit Rate = Baud Rate

58. Why are Bit Rate and Baud Rate equal in UART?
Because one symbol represents one bit.

59. Is Baud Rate always equal to Bit Rate in every communication system?
No, Some systems use one symbol to represent multiple bits.

60. Name some common UART baud rates.
9600
19200
38400
57600
115200

61. Which baud rate is commonly used for debugging?
115200

62. Which baud rate is commonly used by GPS modules?
9600

63. What happens if TX and RX use different baud rates?
Communication errors or garbage data.

64. Which is faster: 9600 or 115200 baud?
115200 baud

65. What is a UART frame?
Complete structure of UART transmission including Start, Data, Parity and Stop bits.

66. What is the purpose of the Start Bit?
Indicates beginning of transmission and synchronizes receiver timing.

67. What is the purpose of the Stop Bit?
Indicates end of the UART frame.

68. What does 8N1 mean?
8 Data Bits
No Parity
1 Stop Bit

69. What is the idle state of a UART line?
HIGH

70. What is the purpose of the Start Bit?
To indicate the beginning of a UART frame and synchronize the receiver.

71. What is the value of the Start Bit?
Logic 0

72. What is the UART idle state?
Logic 1 (HIGH)

73. What transition indicates a Start Bit?
HIGH → LOW

74. Why is the Start Bit important?
Because UART has no clock signal and needs a synchronization point.

75. What do Data Bits contain?
Actual user data being transmitted.

76. Where are Data Bits located in a UART frame?
After the Start Bit.

77. What is the most common UART data length?
8 bits

78. Does UART transmit MSB first or LSB first?
LSB First

79. How many data bits can UART support?
5, 6, 7, 8, or 9 bits

80. What is the purpose of the Parity Bit?
Error detection.

81. What are the common parity modes?
Even
Odd
None

82. In Even Parity, what must be even?
Total number of 1's, including parity bit.

83. In Odd Parity, what must be odd?
Total number of 1's, including parity bit.

84. Can parity correct errors?
No, It only detects errors.

85. What is the purpose of the Stop Bit?
Indicates end of UART frame.

86. What is the value of a Stop Bit?
Logic 1 (HIGH)

87. What does 8N2 mean?
8 Data Bits
No Parity
2 Stop Bits

88. Why are two stop bits sometimes used?
To give the receiver more processing time.

89. What error occurs if the Stop Bit is not HIGH?
Framing Error

90. What is the UART idle state?
Logic HIGH (1)

91. What does the receiver do while line is idle?
Monitors RX and waits for a Start Bit.

92. What transition indicates a Start Bit?
HIGH → LOW

93. What happens after the Stop Bit?
The line returns to idle HIGH state.

94. During idle state, is data being transmitted?
No

95. What is binary of 0xF0?
11110000

96. In what order does UART transmit 0xF0?
0 0 0 0 1 1 1 1
(LSB First)

97. What is the Start Bit value?
0

98. What is the Stop Bit value?
1

99. How many bits are transmitted in 8N1?
10 Bits

100. What event starts UART reception?
Detection of Start Bit
(HIGH → LOW transition)

101. In what order are UART bits received?
LSB First

102. What does receiver check after data bits?
Parity Bit (if enabled)
Stop Bit

102. What happens after successful reception?
Data is stored in receive register.

103. What value is reconstructed from:
0 0 0 0 1 1 1 1
(LSB First)
0xF0