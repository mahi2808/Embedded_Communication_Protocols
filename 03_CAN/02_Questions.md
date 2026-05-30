1. What is CAN?
Controller Area Network,
a serial communication protocol used in automotive and industrial systems.

2. Which signals are used in CAN?
CAN_H & CAN_L

3. Why is CAN widely used in vehicles?
Because it provides reliable communication between multiple ECUs using fewer wires.

4. Is CAN multi-master?
Yes

5. What type of communication does CAN use?
Differential communication.

6. Why was CAN developed?
To provide reliable communication between multiple devices using fewer wires.

7. What problem does CAN solve?
Reduces wiring complexity in multi-device systems.

8. Why is CAN suitable for automotive systems?
Because it provides reliable and noise-resistant communication.

9. Why does CAN use differential communication?
To improve noise immunity.

10. Is CAN serial or parallel communication?
Serial communication.

11. Is CAN single-master or multi-master?
Multi-master

12. What type of communication does CAN use?
Message-based communication.

13. What is the advantage of differential communication?
Improved noise immunity.

14. Can any CAN node start transmission?
Yes, if the bus is free.

15. Which two wires are used in CAN?
CAN_H & CAN_L

16. What type of signaling does CAN use?
Differential signaling.

17. What is the advantage of differential communication?
Improved noise immunity.

18. What is the recessive state voltage?
CAN_H ≈ 2.5V
CAN_L ≈ 2.5V

19. What is the dominant state voltage?
CAN_H ≈ 3.5V
CAN_L ≈ 1.5V

20. Why are 120Ω resistors used in CAN?
To reduce signal reflections.

21. What is differential communication?
Communication where data is detected using voltage difference between two lines.

22. Which lines are used in CAN differential signaling?
CAN_H & CAN_L

23. Why is CAN highly noise resistant?
Because it uses differential signaling.

24. What is the dominant state in CAN?
CAN_H higher than CAN_L.

25. What is the recessive state in CAN?
CAN_H and CAN_L approximately equal.

26. What topology does CAN use?
Bus topology.

27. Why is a CAN transceiver required?
To convert logic-level signals into differential CAN signals.

28. How many termination resistors are used in CAN?
Two 120Ω resistors.

29. Where are termination resistors placed?
At both ends of the CAN bus.

30. Do all nodes receive CAN messages?
Yes

31. What does multi-master mean in CAN?
Any node can start communication when the bus is free.

32. Does CAN require a fixed master?
No

33. What happens if two CAN nodes transmit together?
CAN arbitration decides which node continues transmission.

34. Is data corrupted during arbitration?
No

35. Why is CAN multi-master useful?
It allows important nodes to transmit immediately without waiting for a master.

36. Is CAN address-based communication?
No, CAN is message-based communication.

37. What does CAN Identifier represent?
Message type and priority.

38. Do all CAN nodes receive transmitted messages?
Yes.

39. How does a node decide whether to process a message?
Using CAN ID filtering.

40. Why is message-based communication useful?
One message can be shared with multiple nodes.

41. What is CAN Identifier?
A field used to identify message type and priority.

42. Is CAN ID a device address?
No, It represents message type.

43. Which CAN ID has higher priority?
Lower numerical ID.

44. What is the size of Standard CAN Identifier?
11 bits.

45. What is the size of Extended CAN Identifier?
29 bits.

46. Why is arbitration needed in CAN?
To decide which node continues transmission when multiple nodes transmit simultaneously.

47. Which bit is dominant in CAN?
0

48. Which bit is recessive in CAN?
1

49. Which CAN ID has higher priority?
Lower numerical ID.

50. What happens to losing node during arbitration?
It stops transmission and retries later.

51. What is the dominant bit in CAN?
0

52. What is the recessive bit in CAN?
1

53. Which bit wins on the CAN bus?
Dominant bit.

54. Why are dominant and recessive bits important?
They enable CAN arbitration without data corruption.

55. What happens if a node transmits recessive but reads dominant?
The node stops transmitting because it lost arbitration.

56. What is SOF?
Start Of Frame.

57. What is the purpose of Identifier?
Defines message type and priority.

58. What is DLC?
Data Length Code, Indicates number of data bytes.

59. What is CRC used for?
Error detection.

60. What is ACK used for?
Indicates successful frame reception.

61. What is the identifier size in Standard CAN?
11 bits.

62. What is the identifier size in Extended CAN?
29 bits.

63. Why is Extended CAN used?
To support more message identifiers.

64. Which CAN type has smaller frame size?
Standard CAN.

65. Does arbitration work in both Standard and Extended CAN?
Yes

66. What is the purpose of Data Frame?
To transmit actual CAN data.

67. Which CAN frame is most commonly used?
Data Frame.

68. What does DLC indicate?
Number of data bytes.

69. What is the maximum data size in Classical CAN?
8 bytes.

70. What is checked before processing CAN data?
Identifier.

71. What is ACK in CAN?
Acknowledgement used to confirm successful frame reception.

72. Who sends ACK in CAN?
Receiver node.

73. Which bit is sent during ACK?
Dominant bit (0).

74. What happens if ACK is missing?
Transmitter retransmits the frame.

75. Does ACK mean application processed the data?
No, It only confirms successful frame reception.

76. What is CRC in CAN?
Cyclic Redundancy Check used for error detection.

77. Why is CRC used?
To detect corrupted CAN frames.

78. What happens if CRC mismatches?
Frame is rejected and retransmitted.

79. Can CRC correct errors?
It only detects errors.

80. Who calculates CRC?
Both transmitter and receiver.

81. Why is CAN highly reliable?
Because it uses multiple error detection mechanisms.

82. What is Bit Monitoring?
Node monitors transmitted bits and compares them with actual bus value.

83. What is Bit Stuffing?
Insertion of opposite bit after 5 consecutive identical bits.

84. What happens if ACK is missing?
ACK Error occurs and frame is retransmitted.

85. What happens after CAN detects an error?
Error frame is transmitted and message is retransmitted.

86. Q1. What is Error Frame in CAN?
A special frame used to indicate communication errors.

87. Who can generate Error Frame?
Both transmitter and receiver.

88. Why is Error Frame used?
To destroy corrupted CAN frames.

89. What happens after Error Frame?
Frame retransmission occurs.

90. What are the two types of Error Frames?
Active Error Frame
Passive Error Frame

91. What are CAN error states?
Error Active
Error Passive
Bus Off

92. Which is the normal CAN state?
Error Active.

93. Can an Error Passive node transmit?
Yes.

94. Can a Bus Off node transmit?
No.

95. Why is Bus Off used?
To prevent a faulty node from disturbing the CAN network.

96. What is CAN baud rate?
Communication speed of CAN bus.

97. Must all CAN nodes use same baud rate?
Yes.

98. What happens if baud rates differ?
Communication errors occur.

99. Which supports longer cable length?
Lower baud rate.

100. Give common CAN baud rates.
125 kbps
250 kbps
500 kbps
1 Mbps

101. What is CAN bit timing?
Defines timing of bit transmission and reception.

102. What is Sample Point?
The instant at which receiver reads the bit value.

103. Why is synchronization required?
To keep all CAN nodes aligned in time.

104. What happens if bit timing is incorrect?
Communication errors occur.

105. Why is CAN highly reliable?
Because it uses CRC, ACK, error detection and automatic retransmission.

106. Why is CAN noise resistant?
Because it uses differential communication.

107. Does CAN support multi-master communication?
Yes.

108. How does CAN reduce wiring?
Multiple nodes share the same CAN bus.

109. How does CAN handle message priority?
Lower CAN ID gets higher priority.

110. What is the maximum data size in Classical CAN?
8 bytes

111. Is CAN faster than SPI?
No, SPI is faster.

112. Why does CAN need extra hardware?
Because a CAN transceiver is required.

123. Can low-priority messages be delayed?
Yes, Due to arbitration.

124. What happens to cable length as baud rate increases?
Maximum cable length decreases.

125. Q1. Where is CAN most commonly used?
Automotive systems.

126. Why is CAN used in vehicles?
Reliable and noise-resistant communication between ECUs.

127. Is CAN used in EVs?
Yes.

128. Is CAN used in industrial automation?
Yes.

129. Name some automotive modules that use CAN.
Engine ECU
ABS
Airbag
Dashboard
BMS

130. 