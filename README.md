# MonitorForti
CLI command sets in the Debug flow :
1)         #diagnose debug disable
2)         #diagnose debug flow trace stop
3)         #diagnose debug flow filter clear
4)         #diagnose debug reset
5)         #diagnose debug flow filter addr x.x.x.x
6)         #diagnose debug flow show console enable
7)         #diagnose debug flow show function-name enable
8)         #diagnose debug console timestamp enable
9)          #diagnose debug flow trace start 999
10)       #diagnose debug enable
Note : 6) "diagnose debug flow show console enable" is not available in FortiOS 5.6.0 or higher

The meaning of each line:

1) To disable the debug command. In case we don't know that it has the debug CLI command still running in the unit or not? So we may disable first.
2) To stop the trace of debugging.
3)To clear all filters in the FortiGate.
4) To reset all debug commands in the FortiGate.
5) To filter only address x.x.x.x
6) To display trace on console
7) To show function name.
8) Put the time in the debug command for the reference.
9) To start the trace of debugging including the number of trace line that we want to debug.
10) To enable the debug command.

The debug filter Tips :


1) Filter only the ping traffic

Replace line 5 with the following CLI command:

#diagnose debug flow filter proto 1

Proto can be changed to be another protocol number value to focus on each protocol number as following. (proto = protocol number)

protocol number 1 = ICMP (ping)
protocol number 6 = TCP
protocol number 17 = UDP
etc.
2) Filter only ping that relates to the IP address that we want to focus on.
Replace line 5 with the following CLI command:

#diagnose debug flow filter addr x.x.x.x
#diagnose debug flow filter proto 1

Note :
x.x.x.x is the IP address that we want to filter.
proto 1 is ping traffic. (ICMP)
We can put only 1 IP address per 1 debug.
3) Filter only port number
Replace line 5 with the following CLI command:

#diagnose debug flow filter port Y

Y = port number (such as 80 (http) ,25(smtp) )

4) Filter only IP address and port number

Replace line 5 with the following CLI command:
#diagnose debug flow filter addr x.x.x.x
#diagnose debug flow filter port 80

5) Filter only source or destination port.

Replace line 5# with the following CLI command:

#diagnose debug flow filter sport 80                           -----> filter with the source port 80
Or
#diagnose debug flow filter dport 25                              -----> filter with the destination port 25

6) Filter only the source IP address or destination IP address.

Replace line 5 with the following CLI command:

#diagnose debug flow filter saddr x.x.x.x          -----> filter with the source IP address x.x.x.x
Or
#diagnose debug flow filter daddr y.y.y.y          -----> filter with the destination IP address y.y.y.y


7) Filter only the specific virtual domain

Replace line 5 with the following CLI command:

#diagnose debug flow filter vd X                                   -----> "X" is the index of virtual domain
