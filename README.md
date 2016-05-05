
# TapeXY

Experiment in super low-cost XY stage, for uses in digital fabrication techniques
which have minimal weight and forces on head (laser engraving, 3d-printing).
Inspired by the [RishaLaser](http://rishalaser.org) project.

[Youtube VIDEO](https://www.youtube.com/watch?v=5F9-HIbBYwc)

![TapeXY first prototype](./doc/tapexy-first.jpg)

Key features:

* Using Kapton tape as basis for gliding surfaces,
inspired by [a design](http://www.thingiverse.com/thing:3554) by Peter Jansen
* Using braided Nylon/Polyamid wire ("Spectra line") instead of timing belts.
Like on Tantillus and some Delta printers.
* Reproduction with primarily lasercutter (or CNC mill), in wood/acrylics.
* [CoreXY](http://corexy.com) kinematics

Parts:

* Frame [FreeCAD](./tapexy-frame.fcstd)
* Gantry [FreeCAD](./tapexy-gantry.fcstd)
* Head [FreeCAD](./tapexy-head.fcstd)
* Pulleys. NinjaFlex/SemiFlex for friction. [FreeCAD](./pulley-ninjaflex.fcstd)
* Idlers. 8 pieces, each consisting of 1x 608 bearing, 1x M8-40mm bolt and 2x [sideguides](http://www.thingiverse.com/thing:31216)

Assembly: [FreeCAD](./tapexy.fcstd)

Done

* First working prototype of XY stage, driven by RAMPS/Cura
* Laser diode driver. DIY, linear constant-current source based on op-amp+NPN for 5volt supply

TODO:

* Make second iteration (with belts/pulleys in single plane)
* Design a proper belt/line attachment and tensioning system
* Design and make mount for laser diode
* Add mounting holes for endstops
* Run tests with laser
* Design some self-adjusting system for friction parts
* Create schematic and document laser diode driver

Later:

* Devise some way of testing tape friction coefficient
* Test alternative tapes, like packaging 'Scotch' and PET
* Test cutting Kapton tape with laser. Both CO2 and with the 445nm diode
* Test removing idler bearings, and just let Nylon wire slide on Kapton?
* Reduce number of screws used, by having lasercut pins instead
* Prototype a matching Z-bed/table design
* Test FDM printing
* Test some lightweight CNC milling, like wax, PCB traces or engraving.
* Test a build for full-size laser envelope

Research

* Coefficient of friction.
[Table](http://www.goodfellow.com/catalogue/GFCat2C.php?ewd_token=Q4ZIFOAVRhE2dSOYkbUxPMdSBZyxXk&n=Ab6sV0qHM8iAeitFJGlgDA1qjQCrhQ&ewd_urlNo=GFCat26&type=30&prop=3)
Kapton/Polyimide: 0.45, Teflon/PTFE: 0.05-0.2, UHMW PE: 0.1-0.2.

Existing low-cost laser diode engravers

* [smartDIYs](http://www.thingiverse.com/thing:1026345) open source kit. Lasercut acrylic, steelrods+timingbelts, motor on gantry.
* [Mr. Beam](https://www.mr-beam.org/) open source kit. Kickstarter 2014. 3d-printed + wood-frame. [Octoprint-based](https://github.com/mrbeam/OctoPrint) software

## Laser diodes

* [Banggood](http://www.banggood.com/Wholesale-Laser-Equipment-c-3491.html), 1.6W - [5.5W](http://www.banggood.com/445nm-5_5W-5500mW-Blue-Laser-Module-With-Heatsink-For-DIY-Laser-Cutter-Engraver-p-999283.html)
* Osram PL TB450B [DigiKey](http://www.digikey.com/product-detail/en/osram-opto-semiconductors-inc/PL%20TB450B/PL%20TB450B-ND/5719266)
* [DTR's Laser Shop](https://sites.google.com/site/dtrlpf/home/diodes)
* [Laserdirect@Ebay](http://www.ebay.com/sch/laserdirect/m.html?_nkw&_armrs=1&_ipg&_from&rt=nc&_mPrRngCbx=1)

Fibre guided

* [Ebay: 8 watt NIR 980nm](http://www.ebay.com/itm/980nm-8W-Fiber-Coupled-Laser-Semiconductor-Fiber-Coupled-laser-8000mW-IR-Laser-/141524214275?hash=item20f3802203:g:jsMAAOSwMpZUolDB)
* Ebay: [3W](http://www.ebay.com/itm/Laser-Diode-3-1-Watt-923nm-Fiber-Coupled-100um-JDSU-6380-L2-3-1W-NEW-63-00123-/111598682682?hash=item19fbccc23a:g:mhMAAOSwPhdU3sXA)
and [5W](http://www.ebay.com/itm/Laser-Diode-5-Watt-915nm-Fiber-Coupled-100um-JDSU-6390-L3-5W-NEW-63-00192-/111598671030?hash=item19fbcc94b6:g:0M8AAOSwqu9U3r8Y)

Should be possible to [combine](https://www.rp-photonics.com/beam_combining.html) multiple such fibre laser diodes with one focusing lens (maybe with colliminator).
To achieve powers of N times the individual laser source. Though with simple combinators, the brightness will not increase so much, due to widening of beam size.
 Also the heatsink no longer needs to be on the head, reducing weight of moving parts.


## CO2 lasers

For cheap lasercutters, CO2 lasers are used.

There are several aspects which are challenging.

* Laser tube itself
* Cooling the gas
* The optics
* Power supply

Principle

Using gas mixture of helium, nitrogen, and carbon dioxide gas.
A common standard mixture is 4.5 percent CO2, 13.5 percent N2, and 82 percent He. Penn suggests using a mixture of 14:14:72 in narrow-bore CO2 laser.

Aactive cooling to keep the temperature of the discharge tube below around 30 degrees C or so.

Flowing-gas lasers

"the flowing-gas CO2 laser requires a vacuum pump to achieve the low pressures (10-30 torr or so)"

* [35 Watt Flowing Gas CO2 Laser Tube Kit](http://repairfaq.cis.upenn.edu/sam/rconway/35wtkit.pdf), assembly instructions.
* [Flowing gas CO2 laser conversion from sealed gas](https://www.photonlexicon.com/forums/showthread.php/17719-Flowing-gas-CO2-laser-conversion-from-sealed-gas)
* [First Homemade CO2 Laser Built From Scratch](http://jarrodkinsey.org/co2laser/co2laser.html)

References

* [Understanding CO2 laser](http://www.laserk.com/newsletters/whiteCO.html)
* [RP Photonics Encyclopedia: CO2 lasers](https://www.rp-photonics.com/co2_lasers.html), describes different types. Sealed tube versus
* [Homebrew CO2 Laser Design and Construction Notes](http://www.timefracture.org/laserdocs/laser_design_notes.html)
* [RepairFAQ: Home-Built Carbon Dioxide (CO2) Laser](http://www.repairfaq.org/sam/lasercc2.htm). Looots of information
* [RepairFAQ: Carbon Dioxide Lasers](http://www.repairfaq.org/sam/laserco2.htm). Loots of information

## Related projects...

Of mine

* [Clothing](../clothing), various techniques rely on laser
* [Rishalaser](../rishalaser), build of existing open-source low-powered laserengraver

Of others

* [MPlus One](http://www.thingiverse.com/thing:1104249).
Cantilevered, moving bed like PrinterBot Simple and Smartrap, with lasered/milled structure.
Maybe has potential in combination with tape principle, possibly making even cheaper than a CoreXY?

Possible addons

* [Lasercut vacuum table](http://hackaday.com/2016/03/19/diy-vacuum-table-makes-lasering-even-easier)

## TapeZ

Moving-bed Z-axis stage for laserengraver/3d-printer to go with TapeXY.
Also uses Kapton tape and braided Nylon wire.

Existing wire/belt Z-axis:

* [SmartRapCore alternative Z](http://www.thingiverse.com/thing:896556)
* [Sli3dr](http://richrap.blogspot.co.uk/2014/07/3d-printers-big-printers-small-printers.html)
* [Igentis](https://www.youmagine.com/designs/ingentis-a-tantillus-variant)
* [Printxel](http://printxel.blogspot.ca/2012/12/printxel-community.html)
* http://forums.reprap.org/read.php?177,310249
* http://forums.reprap.org/read.php?160,170024
* http://forums.reprap.org/read.php?177,192178
* http://forums.reprap.org/read.php?14,319321
* http://forums.reprap.org/read.php?279,188149

A challenge is that Z-resolution/precision might be a bit low without gearing.
The hold-torque of a NEMA17 stepper might also not be enough to keep bed up.
Reduction gearing of between 1/4 and 1/9 is desirable.

## TapeCrane

My dad wants to build a cheap, large-scale 3d-printer (workspace with sides of 50-100cm)
which could be stowed away when not in used. For this he had two ideas for the kinematics.
One being a robot arm with two joints (elbow and wrist), working in the XY plane. Like SCARA.
The arm up/down or the bed would move to form Z axis.
The effector is cantilevered, making it tricky to keep rigid, and there are multiple
solutions for the inverse kinematics and singularity points.

The other idea was more like a crane, a [cylindrical robot](https://www.google.no/search?q=cylindrical+robot&tbm=isch).
It has the advantages of much simpler inverse kinematics (because no articulated joints),
and that the structure can be made more rigid in various ways:
Using tensioned wires (like a guy-wire), by supporting the far end, and/or using a (moving) counterbalance.

The most common configuration, has a rotating base. Alternatively, one can rotate just the (elevated) arm.
Either the whole arm can move back & forth to move end-effector, or the effector can travel along a static arm.

Unlike a cartesian or delta robot, several cylindrial robots could work into the same workarea.
They could potentially collaborate on a single (large) part, either for speed or multi-filament.
Or indepentently making different parts, or multiple instances of the same part.

Challenges:

* Mimizing weight of rotating joint, keeping it close to center of axis. For maximum speed
* Implementing the IK for cylindrical in firmware
* Cylindrical sectioned build area
* Decreasing precision at long-reach

TODO:

* Sketch a rough concept
* Test an arm beam, with tensioned wires on top+bottom for ridigity

## Experiments

### Kapton 608 bearing

.. Wednesday 14 Oct 2015, Oslo ..

Attempted to create a 608-sized bearing/bushing. 3d-printed, using Kapton tape added afterwards.
Using a V-profile to make the bearing support some axial load.
Initially 120 deg, but had to increase to 135-degrees to make it possible to insert inner part into outer ring.
Tolerances when 3d-printed (on a Ultimaker Original) seemed generally OK.

However, major issues were found when trying to assemble.
The Kapton tape was not particularly sticky to the print,
and would not easily fold around the V-profiles, especially the outer ring (with inward V profile).
When pressing the inner part of the bearing in, would easily
move the carefully aligned tape... Avoiding folds/creases was quite tricky.

I was able to succesfully assemble one bearing, with tape only on the inner part.
This rotated quite nicely, with not too much play
(considering the application of belt pulley, where some excentricity is quite OK).
Indicates that if one can figure out a practical assembly, the idea has some merit.

It could be that in larger scale, and with a more adhesive tape and, or with simpler geometry,
that the idea would have some merit. But with v-style 608 the process was too fiddly to be practical.

For TapeXY it could be possible to design an alternative idler/pulley solution.
For instance one could integrate the belt bottom/top guides, and use top/bottom of
rotating part for supporting the (tiny) axial load.

It is however desirable to be compatible with a standard solution,
or at least also allow a standard solution - since a hacked thing will (probably?)
never be as good as a proper bearing.

## Ideas

* Use a lightweight CNC milling head with thin tool to precicely score/drill acrylic.
So that one can just snap along these edges, and widen hole with hand-drill. To make more reprappable.
Challenge: limits design to straight external edges?

### Cheap closed-loop solutions

Have camera on head. Optical recognition.
For laser cutter. First move slowly, 

### Ninjaflex belted gearbox

Most 3d-printed gearboxes use meshing gears of PLA/ABS/Nylon.
Using a flexible timing belt to connect them instead has advantages:
* Less wear, since belts distribute force over a larger area.
Most wear should be on belt, allowing independent replacement. Also more wear tolerant.
* More silent, since belts are of softer material
* More tolerant for bad bearings (excentric or axial motion)

If well designed, could also be more overload tolerant as well
- belt should slip before damaging pulleys.

The belt could be printed out of NinjaFlex ([work by others](http://www.thingiverse.com/search/page:1?q=ninjaflex+belt&sa=)).
With some clever work on axel, bearings and belt-tensioner, it may be possible to make it zero-vitamins.

One application for such a gearbox, would be for a belted Z-axis of a printer using NEMA17 stepper.

## Printed belt tensioner

The standard solution for tightening belts is to have the bearing/pulley axel in a slot,
and then a bolt which the axel rests against, on the side the belt pulls.
Tightening the bolt, pushes the axel further up in the slot, and tightens the belt.
This works well, but requires a couple of vitamins (bolt, nut)

An excentric wheel, where radius increases when turning, could replace the bolt.
To keep it from just rotating, a ratcheting mechanism on a spring would lock it.
To loosen belt one would push out the ratchet.

## References

Work by others

* [3d-printed bushing](http://www.thingiverse.com/thing:1196801), replaces speciality linear bearings
* [3d-printed beam surface](http://www.thingiverse.com/thing:9080/#comments)

# Interesting designs

* [Delta-T, rail-free, wire-based delta](http://forums.reprap.org/read.php?1,525804)
* [SkyDelta, rail-free, wire-based delta](https://groups.google.com/forum/#!topic/deltabot/Jj6vyPf7jJ8)

# Electronic discharge machining

Looks promising as a non-contact method of machining metals.
Particularly for small/fine things, like PCB isolation engraving or.

Can be used with a wide array of tool-heads, to make custom shapes.

Disadvantages are heavy tool erosion. But maybe can use 0.5 mm grafite leads from pencils??

Needs some regulation circutry which constantly keeps the head at appropriate level from workpiece.
Bonus sideeffect : built-in Z-height autolevel.

References

* [YouTube: Principle test from Fablab India](https://www.youtube.com/watch?v=Zf7_GY7GMV40), part of Fabacademy 2016.
* [YouTube: Principle test from 2012](https://www.youtube.com/watch?v=GVSST58x_FE). Looks to be working quite well.
* [RepRap forums: DIY EDM](http://forums.reprap.org/read.php?1,262452)
* [Hackaday.io: Not Your Father's EDM](https://hackaday.io/project/3232-not-your-fathers-edm). Last update in Feb 2015.
