
# Classes

## CelestialBody
Atomic class.

### Star
CelestialBody and UndergoesType3LitschitzProcessWithIronPercentageOver90AndSomeOtherConditions

### BlackHole
...

### NeutronStar
...

## System
CelestialBody or Group of CelestialBody

### PhysicalSystem
A System for which all sub-Systems are GravitationallyBoundTo one another.
(Easy to define in FOL, possible in DL ???)

(there also exists Optical systems, for which all sub-systems are visible and close (angle wise) from Earth (or somewhere else). I don't think defining this is interesting until we include ray-tracing in our ontology)


### X-System (StarSystem, PlanetSystem, SolarSystem...)
System and SystemOf X
Maybe useless since SystemOf is defined ?

### n-arySystem
System and Contains exactly n Thing
I don't think defining classes based on the set of integers is a good idea. Can be derived from Contains.

## Point
Reuse a BFO class for spatial point ?


# Relations

## Contains
generic member relation ? specific to System -> System ?

## SystemOf
System -> class
System only Contains (IsA class)
(Can we do this under DL ?)

## GravitationallyBoundTo
System -> System, symmetric

## Orbits
System -> Point
Maybe to reify in order to link the specific orbit equation ?


# Examples

## 3-ary star system
```
star1, star2, star3 := Star

system1, system2 := System
barycentre1, barycentre2 := Point

system1 Contains star1, star2
star1 GravitationallyBoundTo star2
star1 Orbits barycentre1
star2 Orbits barycentre1

system2 Contains system1, star3
system1 GravitationallyBoundTo star3
system1 Orbits barycentre2
star3 Orbits barycentre2
```
