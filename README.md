# datagram_sender
send datagram from sender to receiver

Handshaking between sender and receiver:


The sender will collect inputs from user from its GUI. The inputs include ip address and port number of receiver, and the port for sender. This is the key to start the connection.
First datagram socket is created on the sender specifying the sender port number where data can be received. Then datagram packet is created which connects to the receiver ip address using the user inputted receiver port number. The important thing is that because all the ports and ip are user inputs the receiver side MUST also have these inputs when creating the connection. On the receiver side, the inputs will be collected from GUI. The inputs include ip address and port number of sender, and the port for receiver. The datagram socket with receiver port is created and datagram packet is created with sender ip and port. The datagram sockets are packets are basically sending data specified only by the port and ip inputs.


Format of datagrams:


The file will be read line by line, from the line packets will be created which are equal to the MDS input from user. To do this the String line will be converted and placed into Byte array according to MDS size. This will be the packet. The only thing that will be added to each packet at the end of message is the sequence number.
Example -> "message" + " " + sequence; This will be converted into byte accordingly and sent to receiver.
Different test runs and results by changing timeout and MDS:
First, we tested with a small file. We kept the timeout to 100000 microseconds and increased MDS from 16, 32, and 64. We noticed that the results were getting better with each increase of the MDS with minor fluctuations for computer speed or internal eclipse delays (we used eclipse for assignment). Now between reliable and unreliable, reliable was faster by factors of number of packets lost * timeout (approximately as other hardware delays occur). These differences for small files were very minor ~ 5ms difference. Now we changed the timeout by 100000, 500000, 1000000 microseconds. This did not have an effect on reliable transmissions. On unreliable transmissions, the total transmission time would increase by a lot (factors of lost packets* timeout). Next we tested using a larger file, the same results occurred for different timeout and MDS inputs. However, they were much more noticeable. Example, when changing MDS the number of packets sent in total varied much more as file size was larger thus there were more delays per packet. We have in the GUI a status panel which shows number of packets send and size, this would not vary that much for small files as differences in MDS would not results in many increases/decreases in packets sent. But for large files this was noticeable and so changing MDS and timeout had huge effect on total time. Overall the larger the MDS the faster total transmission time, the larger the timeout, the longer the transmission time for unreliable.
