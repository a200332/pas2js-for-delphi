# Pas2js Pascal to JavaScript transpiler for Delphi
It's a Pascal to JavaScript transpiler, adapted for Delphi compiler. It can get Delphi / Free Pascal projects and units and convert them to JavaScript. The original Pas2js transpiler for Free Pascal is [here](http://wiki.freepascal.org/pas2js).

The original Pas2js was downloaded from SVN on **January 21, 2019**. I.e. Pas2js for Delphi is inherited from this edition of Pas2js for FPC.

## Most important changes
In my edition there are no any modifications, except those that are necessary for compiling in Delphi for Windows.
* Used Unicode UTF-16 instead of UTF-8 (and ANSI) strings in the transpiler code.
* Used generic collections (TDictionary<string, XXX>) instead of TFPHashObjectList.

## Other changes made due to differences in syntax of Free Pascal and Delphi language
* case statement for a string expression --> if expression = ... then else if expression = ... then ...
* for item in enumeration do --> for item := Low(TEnumeration) to High(TEnumeration) do ...

## Limitation of Pas2js for Delphi
The original Pas2js supports several operation systems and compilation targets. This Pas2js for Delphi
* has the pas2js.dpr command-line utility for **Windows**, **32-bit**. You can compile it in Delphi IDE.
* It was tested for the **browser** target platform, i.e. it can generate JS files to use in HTML pages.

## Testing and compatibility
Pas2js for Delphi tested on demo programs included in the original Pas2js package.

There is no difference in the output JS files, generated by the original Pas2js (compiled in FPC), and this Pas2js for Delphi. Except for one: there is a little difference in a representation of floating-point numbers. For ex.,
* original constant in Pascal: hrfactor = 1/(24);
* same constant in JS compiled by FPC:    0.041666666666666664
* same constant in JS compiled by Delphi: 0.0416666666666667
* original: mssecfactor = 1/(24*60*60*1000);
* JS compiled by FPC:    1.1574074074074074E-8
* JS compiled by Delphi: 1.15740740740741E-8

## License
Pas2js has the same license as the original Pas2js for FPC. It is essentially GNU General Public License with one modification.

(C) 2019 Kryvich.
