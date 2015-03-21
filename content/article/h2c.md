+++
categories = ["h2c"]
comments = true
date = "2015-03-08T22:34:03-04:00"
description = ""
draft = true
image = ""
tags = ["article", "h2c"]
title = "H2Ceramic Cooling System"
type = "article"
url = "h2c"
video = ""

[menu]
  [menu.sitenav]
	identifier = "h2c-overview"
	name = "Overview"
	parent = "h2c"
	post = ""
	pre = ""
	weight = 1

+++

[[File:hothardware-big xps 730 h2c1.jpg|thumbnail|XPS 730X H2C (front)]]
[[File:hothardware-big xps 730 h2c2.jpg|thumbnail|XPS 730X H2C (back)]]

The H<sub>2</sub>Ceramic Cooling System (aka H<sub>2</sub>C and H<sub>2</sub>C Hybrid Cooling) is a unique feature that was designed by Dell specifically for the Dell XPS 700 series eXtreme Performance Systems (XPS).

## Overview

The unit is basically a [thermoelectric](http://en.wikipedia.org/wiki/Thermoelectric_cooling "Wikipedia: Thermoeletric Cooling")/water-cooling hybrid design using a single 120mm x 38mm radiator, four 35W TEC plates on a waterchiller block, a thermistor, a waterpump, and two waterblocks (one for the CPU and one for the [Intel X58](http://en.wikipedia.org/wiki/Intel_X58 "Wikipedia: Intel X58") chipset's [Northbridge](http://en.wikipedia.org/wiki/Northbridge_(computing) "Wikipedia: Northbridge")).  The final component is a Dell proprietary [[mcb|Master Control Board (MCB)]] with firmware programmed to monitor ambient temps as well as the temp of the CPU and waterchiller block - all to control the TEC plates with variable voltages.

{{< blockquote author="Eric Duncan" link="http://eduncan911.com" linktext="eduncan911.com" >}}
I immediately opened the Alienware Area-51 ALX up and to my surprise found the exact same motherboard and components as my XPS 730X!
{{< /blockquote >}}

### Dell's H<sub>2</sub>C Design

With a little marketing hype, Dell announced their DELL H<sub>2</sub> TECHNOLOGY: HYBRID COOLING FOR OVERCLOCKED CPUs.  The original marketing material has been removed from Dell's website, therefore I am hosting the only copy that I know of in existence.

[[File:Dell H2C Technology Hybrid Cooling for Overclocked CPUs.pdf|DELL H<sub>2</sub> TECHNOLOGY: HYBRID COOLING FOR OVERCLOCKED CPUs]]

This PDF released holds some valuable insight into the inner workings and concepts of the H<sub>2</sub> system itself.  Some of these highlights are listed below.

#### Targeting cooling of just above ambient

By far one of the most critical design objectives was this except from the PDF:

:''"The target cooling level for H<sub>2</sub>C is just above ambient room temperature because colder temperatures can cause condensation or frost that damage the system. Because thermoelectric cooling can cool below ambient room temperature, H<sub>2</sub>C includes sensors and control logic to keep recirculating fluid temperature from falling below the ambient temperature."''

You can see this in Figure 3 below.

[[File:Dell H2C Technology-Figure 3.png|framed|none|Dell H2C Technology-Figure 3.png]]

This was achieved by a ''(insert specs)'' [http://en.wikipedia.org/wiki/Thermistor thermistor] placed directly onto the waterblock and wired to the [[mcb|MCB]] for monitoring.  When the waterblock was cooled down to near ambient temps, as measured by the [[mcb|MCB]]'s own onboard ambient sensor, the TEC plates would simply be turned down to cool less.

#### Runs quieter than standard water-cooling

Another excerpt is keen to another major objective.

:''"In testing against the best custom solutions available, H<sub>2</sub>C was proven to be cooler in overclocked mode and potentially quieter in normal operating mode as shown in Figure 7."''

[[File:Dell H2C Technology-Figure 7.png|framed|none|Dell H2C Technology-Figure 7.png]]

To translate this excerpt and Figure 7, it breaks down like this under heavy CPU loads: Typical fan-on-heatsink setups are loud, standard water cooling kits are quieter, while the H<sub>2</sub>C design allows for even lower noise.  This is basically achieved by using the waterchiller block ''after'' the radiator.  You, in essence, use the left over airflow exiting the back of the radiator for a 2nd cooling affect, over the TEC's heatsinks.  TECs and their heatsinks run a lot hotter than normal watercooling radiators.  

This was a win-win combination!  You end you reusing wasted air to do additional cooling, therefore lowering the CPU temps even further without increasing fan speed.

### Who made the H<sub>2</sub>C units to begin with?  Was it really Dell?

Not really, they designed the system but outsourced the assembly.  The fact is Dell designed the system for "low noise" using [http://en.wikipedia.org/wiki/Thermoelectric_cooling Thermoelectric Cooling] plates.

''(insert initial engineer names found)''

Dell originally contracted Delphi to create these H<sub>2</sub>C units in the XPS 720, and revision A00 in the XPS 730.
Maybe because of the high failure rates, but Dell only knows why, Dell changed suppliers to [http://www.coolitsystems.com/ CoolIT Systems] to build revisions A01 and A02 of the H<sub>2</sub>C units for the [[Main_Page|XPS 730X]].  CoolIT Systems were the ones who built similar TEC waterblock systems before the H<sub>2</sub>C units (like their TEC Cooling tanks).  As of 2009, CoolIT now been contracted exclusively to make the Corsair H80/H100 units (you may have heard of them).  Exclusively as in, CootIT Systems no longer warranties, supports, or sells any other system.  It's all Corsair or bust at their place.

## Problems with the H<sub>2</sub>C

[[File:h2c-scale.jpg|thumbnail|h2c-scale.jpg]]
While a great design, the H<sub>2</sub>C was not built to last.  Common causes are leaking hoses and just normal water evaporation, causing the pumps to overheat and fail. 

### Design Flaws

The system overall is designed very well (that's why we love our XPS 730X machines).  The firmware works well by monitoring the average CPU temps and responding by ramping up the voltage to the TEC units and Front CPU Fan, along with the PCI Cage Fan and HDD Fans (yes, these increase as well).

#### Too slow to ramp-up under demand

The firmware is too slow to react to instant demands of high CPU loads.  You can see this here in this graph when overclocked to 4.5 Ghz ''(insert graph of Prime95 and voltage monitoring and CPU temps)''.  While the CPU temp is ok, as soon as instant 100% demand for the CPU comes, temps increase to over 100C until the H<sub>2</sub>C can rampup the TEC voltage, and then to cool the waterchiller.  All of this takes time.  The result is high CPU temp spikes under extreme overclocking.  

#### Operating range too high for extreme overclocking

''(insert measured range and graphs of 60C - 80C)''


### Assembly Flaws ###

I have built dozens of custom water cooling setups, and some quite extreme (insert examples/pics from personal builds).  One thing I quickly learned when building systems is to find the right mix of parts for longevity.  
To rehash, Dell did not build these units.  They sub-contracted out the design originally to Delphi and then to CoolIT.  It was these companies that took the designs and assembled it as needed.  Each with their own ups and downs.

#### Delphi H<sub>2</sub>C Rev A00

Delphi originally built revision A00 for the XPS 730 (nForce LGA775 socket).  Though many have reported revision A00 was in their XPS 730X (Intel X58 LGA1366 socket) machines.  There were several issues with this build.

:'''LGA775 Socket Waterblock''': By far one of the biggest parts flaw is the CPU waterblock.  It was originally designed to fit the Intel LGA775 socket.  When placed onto the larger LGA1366 socket, there is an edge of about 3mm that is not covered.  Even though the top of the CPU is really just a heat spreader, I would prefer not to have any hot-spots at the edges of my CPUs.

:'''Spring-style Hose Clamps''': These type of clamps that simply use tension do work in theory.  But it has been my experience as an automotive technician that these type of clamps leak over time.

:'''Pump''': ''(insert info about flawed parts)''

:'''Dissimilar Metals causes Scale''': One of the other largest assembly flaws is the use of aluminum and copper in the water loop.  This is a big no-no in water cooling because the metals chemically react causing several scale build up.  The "white-stuff" you see bleeding from the pump and hoses.

#### CoolIT H<sub>2</sub>C Rev A01 and Rev A02


''(talk about reduces hose sizes)''

''(heatshrink hose installation)''

''(smaller radiator)''

### Scale Buildup

Mainly in the Rev A00 units, we have [http://en.wikipedia.org/wiki/Limescale (scale)] build-up by the dissimilar metals in the system (another poor design decision).  

As a result of any of these failures, the [[mcb|MCB]] would sense an increase in CPU temps and increase the [[fans|Fans]] to jet engine-like sound levels.

## Repairing the XPS 730X H<sub>2</sub>C

[[h2c_servicing|See: H<sub>2</sub>C Servicing]]

## Modifying the XPS 730X H<sub>2</sub>C

[[h2c_mods|See: H<sub>2</sub>C Modifying]]

## XPS 730X H<sub>2</sub>C Wiring

[[h2c_wiring|See: H<sub>2</sub>C Wiring]]

## XPS 730X TEC and Waterchiller Details

[[h2c_tec|See: H<sub>2</sub>C TEC and Waterchiller]]


''(incomplete - will be adding more)''

## See also

* {{< relref "h2c-repairs.md" >}}
* {{< relref "h2c-mods.md" >}}
* {{< relref "h2c-wiring.md" >}}
* {{< relref "h2c-tec.md" >}}
