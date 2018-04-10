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

To use this tool, we need to run on both server and client side.

On the server side:

  ./saturatr

On the client side:

  ./saturatr [RELIABLE_IP RELIABLE_DEV TEST_IP TEST_DEV SERVER_IP]
