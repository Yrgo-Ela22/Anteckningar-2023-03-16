# Anteckningar 2023-03-16
Drivrutiner för utskrift av tal på 7-segmentsdisplayer, implementerade för mikrodator ATmega328P. 

Två 7-segmentsdisplayer matas från samma pinnar (PORTD0 - PORTD6), där timerkrets Timer 1 används för att
skifta vilken display som är på vid ett givet tillfälle. En gång i millisekunden skiftas aktiv display.
På display1 skrivs tiotal ut och på display2 skrivs ental ut. 

Talbasen kan väljas mellan 2, 10 samt 16 för utskrift av binära, decimala samt hexadecimala tal.
Eftersom två displayer används sätts maxvärdet för binära tal till 0b11 (3), för decimala tal till 99
samt för hexadecimala tal till 0xFF (255).

Ur ett givet tal x av talbasen radix beräknas tiotalet samt heltalet enligt nedan:

tiotal = x / radix (heltalsdivision)
ental = x - tiotal * radix

Som exempel, det decimala talet 74 delas in i tiotal och ental enligt nedan:

tiotal = 74 / 10 = 7 (heltalsdivision)
ental = 74 - 7 * 10 = 4

I nästa del ska upp- och nedräkning av talet på displayerna implementeras via timerkrets Timer 2.
För tillfället sker uppräkning med fördröjning i funktionen main.