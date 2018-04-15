# SaturatrUsage
https://github.com/keithw/multisend/blob/master/sender/saturatr.cc

In the multisend (https://github.com/keithw/multisend), they provides a tool(saturatr) which can measure the capacity of line.
It involved with two classes Saturateservo and Acker.

    SaturateServo saturatr( "OUTGOING", log_file, feedback_socket, data_socket, remote_data_address, server, sender_id );
    Acker acker( "INCOMING", log_file, data_socket, feedback_socket, remote_feedback_address, server, sender_id );
  
SaturateServo is used for sending packets and getting acks.
It's output is like:

    OUTGOING ACK RECEIVED senderid=1523319503, seq=6189, send_time=1523319507214479929,  recv_time=1523319507960120687, rtt=0.7456, 1500 => 1500

Acker is used for sending acks and received data packets.
It's output is like:
  
    INCOMING DATA RECEIVED senderid=1523319958, seq=674, send_time=1523320614292785828, recv_time=1523320614293919111, 1delay=0.0011 

Usage:

First we can get the source code from https://github.com/keithw/multisend/
The source code saturatr.cc is under sender folder.
To compile it, we need c++11.

To use this tool, we need to run on both server and client side.

On the server side:
  
    ./saturatr

On the client side:

    ./saturatr [RELIABLE_IP RELIABLE_DEV TEST_IP TEST_DEV SERVER_IP]
    
There are two interfaces one is used as relibale the other is test.
Saturateservo (or Acker) will send data (or ACK) packer using test device (or reliable) and listening to relibale device (or test).

Here I just set the reliable and the test as the same interface.

Once we get the output files for server and client, we can use another tool to convert it to .pps tracefile which can use used as the input for Cellsim.
The code can be found:
https://github.com/keithw/multisend/blob/master/sender/trace-analysis/prep-for-simulation.py

To use it:
    
    python prep-for-simulation.py <file-name> <session-number>

Then we can get the output .pps files (uplink and downlink).

To test:

Here I built an 24Mbps link using Mahimahi.
    
    mm-link tracefile.up tracefile.down
    
Where the trace file sends 2 packets per ms. (So it would be 24Mbps)
In this way Mahimahi will build a container which holds two ip address (like 100.64.0.3 and 100.64.0.4).
Then inside the container we can run saturatr server, outside the container we can run saturatr client.
After that I use prep-for-simulation.py to analysis the output results and convert them to .pps files.
The result seems to be matched with 24Mbps (about 2 packets per ms).




