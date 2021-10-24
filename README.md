# puzzles

There is plenty of online resources for 3d interlocking puzzle. In particular, you might find some ready-to-print puzzles in the amazing [Printable Puzzle Project](https://www.puzzlehub.org/ppp).

There is another incredible resource, which is [Puzzle will be played...](https://puzzlewillbeplayed.com/) that collects diagrams for a HUGE number of different 3d interlocking puzzles; when I say that the collection is HUGE [I really mean it](https://puzzlewillbeplayed.com/-/flat.xml).

The only problem is that you probably want to physically play with the puzzles! You can use any 3d CAD or you can use some more specific software.

Since I spent some time translating `Puzzle will be played...` puzzles into `BurrTools`/`PuzzleCAD`, I thought you could benefit from this as well.

## Useful Software

We'll make use of some of the best software available on the internet.

### BurrTools

[BurrTools](http://burrtools.sourceforge.net/) is an amazing piece of software that lets you model many 3D puzzles and even solve them in most cases (assembly/disassembly). It's incredibly useful when designing your own puzzle and checking for all possible configurations. The main file format is .xmpuzzle, which is a compressed XML file that lets you store both pieces and extra metadata (like assemblies and solutions). You can also export to .stl for direct 3d printing, but that's not ideal. We'll get back to this.
Anyway, there is a new version of BurrTools available on GitHub. You can find it here. You should check it especially if you are using a recent macOS.


### OpenSCAD + PuzzleCAD

OpenSCAD is kind of a 3D compiler that reads in a script file that describes the object and renders the 3D model from this script file. This is not ideal for freehand modeling, but it's amazing for puzzles, as you can easily describe the pieces with clear geometric instructions.
In particular, you may want to use the PuzzleCad plugin. Instructions to install the plugin might be found here. You can either model things in OpenSCAD  directly or convert from `.xmpuzzle` with a command-line tool, provided with PuzzleCad:

```
java -jar bt2scad.jar puzzle_file.xmpuzzle
```

There are two main reasons why you might want to use PuzzleCad instead of relying on the BurrTools export tool.

1) PuzzleCad lets you set tolerances that could be really fundamental for the puzzle pieces to actually fit together. If you export the `.stl` file from BurrTools directly, you will have super-precise printing instructions, but your printer is not as precise and this could lead to hardly fitting pieces and you need might sandpaper every single piece.
2) Some pieces need support to print, e.g. the box in [AlPackino](https://puzzlewillbeplayed.com/444Box/AlPackino/) has four suspended blocks that would require some internal support. PuzzleCad lets you enter the schematic for the box and computes a suitable "cut" that lets you print the two halves and provides useful joints to snap the two halves together. This works for many different shapes; you can check an example [here](https://www.thingiverse.com/thing:3351526)

### Ultimaker CURA

[Ultimaker CURA](https://ultimaker.com/it/software/ultimaker-cura) is the software I use to convert `.stl` to `.gcode`, which then is fed to the 3D printer. The conversion depends on the specific printer you set up, but the good thing is that it will tell you in advance how much time it will take for the print and how much filament is going to use.
