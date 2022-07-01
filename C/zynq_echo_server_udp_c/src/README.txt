lwIP Echo Server
----------------

// I had to make modifications to get this code to work on Xilinx SDK 2018.3.
// struct ip_addr needed to be changed to ip_addr_t . D.N.
// Added header files for lwip_init(), tcp_fasttmr(), & tcp_slowtmr() . D.N.

The lwIP Echo server application starts an echo server at port 7. Any data sent
to this port is simply echoed back.

By default, the program assigns the following settings to the board:
IP Address: 192.168.1.10
Netmask   : 255.255.255.0
Gateway   : 192.168.1.1
MAC address:  00:0a:35:00:01:02

These networking settings can be changed for your network in the file main.c or
main.cc for C++.

The main echo server logic is present in the file echo.c or echo.cc for C++.

platform.c or platform.cc implements certain processor and platform dependent
functions. The file platform_config.h is generated based on the hardware design.
It makes two assumptions: The timer has its interrupt line connected to the
interrupt controller, and all the ethernet peripherals (xps_ethernetlite or
xps_ll_temac) accessible from the processor can be used with lwIP.

Running the Echo Server example
-------------------------------

To test the echo server, download and run the program on the board, and then
issue the following command from your host machine:


$ echo -e "Hello World\n" |  nc -u -w 2 192.168.1.10 7
Hello World


References
----------

More details regarding the echo server can be obtained from Xilinx XAPP 1026:
http://www.xilinx.com/support/documentation/application_notes/xapp1026.pdf
