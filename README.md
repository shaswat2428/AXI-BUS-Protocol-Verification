# AXI-BUS-Protocol-Verification
AXI  uses multiple, dedicated channels for reading and writing of transactions. AXI is burst-based like its predecessor AHB
and uses a similar address and control phase before data exchange. AXI also includes a number of new features including out-of-order transactions,
unaligned data transfers, cache support signals, and a low-power interface.

#AXI Channels

There are five independent channels between an AXI master and slave. They are the: 

Read address channel
Read data channel
Write address channel 
Write data channel
Write response channel 

The address channels are used to send address and control information while performing a basic handshake between master and slave. 
The data channels are where the information to be exchanged is placed. 
A master reads data from and writes data to a slave. Read response information is placed on the read data channel,
while write response information has a dedicated channel. This way the master can verify a write transaction has been completed.

#AXI Signals


Much like the AHB, ASB, and APB signals from the previous AMBA revision, each of the AXI channels has a number of signals associated with it.
There are two global signals referred to as ACLK and ARESETn. These are the system's global clock and reset signal, respectively. 
The 'n' suffix on ARESETn means this signal is active low. 



Every channel has an ID tag used for out-of-order transactions. Any transaction with the same ID must remain in order, but transactions with 
different IDs may be completed in any order. This allows faster transactions to be completed before slower ones, even if the slower transaction
was issued first. For example, if a master is writing data to multiple slaves, the transaction IDs would allow the faster slave to finish sooner.

Bus widths are implementation-specific, but these signals are shown with a 32-bit bus width. The RLAST signal is used by the slave to signal to
the master that the last data item is being transferred. 

Other notable signals include the burst size, length, and type. The VALID and READY signals are used for handshaking between master and slave.


The cache, lock, and protection signals are used for caching, exclusive access (atomic operations), and illegal access protection, respectively.

 
 write address, data, and response signals. These signals mirror the read signals above but are used by the master to send data to a slave.
 WLAST signals to the slave that the last data item is being sent. The dedicated write response signals allow for a master to know that the
 write transaction completed successfully. 

# Channel Handshake
Every AXI channel contains both a VALID and a READY signal. These are used to synchronize and control the rate of transfer. The important thing
to remember here is that the source, or sender, uses the VALID signal to indicate that either data or control information is available. The destination,
or receiver, signals READY when it is actually able to consume that information. Thus, a transfer can only occur when both the VALID and READY signals
are asserted.

Notice information transfer  only occurs when both VALID and READY are high, regardless of which was asserted first. Also note that AXI uses the rising
clock edge for all transfers.


 
 
