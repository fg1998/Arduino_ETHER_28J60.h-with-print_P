# Arduino_ETHER_28J60.h-with-print_P
Implements print::print_P for use with the F() macro to save Arduino Memory.

Usage :

<pre>
#include "ETHER_28J60.h"
#include <avr/pgmspace.h>

//Define MAC, IP and Port
static uint8_t mac[6] = { 0x54, 0x55, 0x58, 0x10, 0x00, 0x24 };
static uint8_t ip[4] = { 192, 168, 0, 105};
static uint16_t port = 80;

//ethernet Object
ETHER_28J60 e;

void setup()
{
  e.setup(mac, ip, port)  
}

void loop()
{
  char* params;
  
  if(params = e.serviceRequest())
  {
		e.print_P(F("Foo\n"));
		e.print_P(F("print_P helps you to save Arduino RAM\n"));
		e.print_P(F("For use with the 28J60 Ethernet Module. Generally as a breakout board"));
		e.print_P(F("Based on Simon Monk code"));

		e.respond();
  }
}
</pre>
