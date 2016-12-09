The v: Message.
This message sets date and time on the cube.
Length is 45 and it looks like this:

0000: 76 3A 51 30 56 55 41 41 41 4B 41 41 4D 41 41 41  v:Q0VUAAAKAAMAAA
0010: 34 51 51 30 56 54 56 41 41 44 41 41 49 41 41 42  4QQ0VTVAADAAIAAB
0020: 77 67 2C 31 66 64 64 61 30 39 36 0D 0A	       wg,1fdda096..

containing

position  length  description
--------  ------  --------------------------------------------------------
00-01	   2	  Identifier "v:"
02-21	  32	  Timezone data.
		  Matches the last 24 byte of the (decoded) cube C message
		  base64-encoded
22	   1	  Separator ","
23-2A	   8	  Timestamp, see below
2B-2C	   2	  \r\n

Timestamp must be the UTC time in seconds since 2000.1.1
converted to a hex string as to get by
hex(DateTime.UtcNow.Subtract(New DateTime(2000, 1, 1)).Ticks / TimeSpan.TicksPerSecond)
The cube replies by an "A:" acknowledge.
