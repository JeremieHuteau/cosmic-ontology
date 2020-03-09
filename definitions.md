# Definitions

*Note:* version 1.0 that aims to unify our drafts.

*Note:* This document is really verbose and we have to consider a severe refactoring.


## Main idea

### Objects and celestial objects

Celestial objects are particular objects that follow an astronomical definition. **TODO**

Objects can be celestially atomic (thus they are called *bodies*) or not (thus they are systems). All objects are composite in the sense of they are made of rocks, etc.

### Orbiting

Objects have a barycenter that is a point. Points are orbiting around another point. 

Consider the moon-earth-sun toy system:

 - EARTH is a Planet with barycenter EARTH_BC
 - MOON is a moon with barycenter MOON_BC
 - SUN is a star with barycenter SUN_BC
 - EARTH_MOON_SYSTEM is a satellite system with barycenter EARTH_MOON_SYSTEM_BC
 - SUN_SYSTEM is an unary star with barycenter SUN_SYSTEM_BC 
 - SOLAR_SYSTEM is a planetary system with barycenter SOLAR_SYSTEM_BC

Then:

 - EARTH_BC and MOON_BC both are orbiting around EARTH_MOON_BC
 - SUN_BC is orbiting around SUN_SYSTEM_BC (both points have the same position)
 - EARTH_MOON_BC and SUN_SYSTEM_BC are orbiting around SOLAR_SYSTEM_BC

---

## Class definitions

### Spatial regions

A spatial region is an *n*-dimensional area that may evolve (typically: change its position) but keeps its identity. It is intended to represent the location of an object

 
#### Point

A point is a 0-dimensional spatial region

<p align="center"><img src="/tex/e95297309479f330cfad981f891beb5d.svg?invert_in_darkmode&sanitize=true" align=middle width=180.84258555pt height=14.611878599999999pt/></p>

---

### Object

An object is a concrete thing

#### CelestialObject

A celestial object is an object that is considered by astronomist as a "celestial object"

<p align="center"><img src="/tex/c9d448969071e798094873ea75d44c10.svg?invert_in_darkmode&sanitize=true" align=middle width=196.4894349pt height=14.611878599999999pt/></p>

*Subclasses:* CelestialBody, Galaxy, PlanetarySystem

#### CelestialBody

A celestial body is an atomic celestial object (that is, an object that follow the astronomocal definition)

<p align="center"><img src="/tex/f4dd347035ce14cdd47d90364db92fb3.svg?invert_in_darkmode&sanitize=true" align=middle width=253.17494069999998pt height=14.611878599999999pt/></p>

*Subclasses:* Moon, Planet, Star, Nebula

#### OrbitingSystem

An orbiting system is an object whose barycenter is orbited by the barycenter of some objects

<p align="center"><img src="/tex/afe72b01fd9fb63e97658c75228c3f4c.svg?invert_in_darkmode&sanitize=true" align=middle width=569.12688855pt height=41.09589pt/></p>

*Subclasses:* StarSystem, PlanetarySystem, SatelliteSystem, Galaxy

#### Satellite

A satellite is an object.

<p align="center"><img src="/tex/f444598b0eb676d18954f174c3ab16ef.svg?invert_in_darkmode&sanitize=true" align=middle width=144.35811884999998pt height=14.611878599999999pt/></p>

*Subclasses:* Moon

#### Moon

A moon is a celestial body that is a natural satellite

<p align="center"><img src="/tex/86b4ca812523104f7ae851fec4eba6f8.svg?invert_in_darkmode&sanitize=true" align=middle width=273.80992319999996pt height=14.611878599999999pt/></p>

#### Planet

...

#### Star

...

#### Nebula

...

#### StarSystem

A star system is an orbiting system made of stars only

<p align="center"><img src="/tex/2a5174eafb14a557db516971e3a31575.svg?invert_in_darkmode&sanitize=true" align=middle width=356.0543085pt height=16.438356pt/></p>

*Subclasses:* UnaryStar, BinaryStar, TernaryStar

#### N-ary stars

Definition for UnaryStar, BinaryStar and TernaryStar

A *n*-ary star is a star system made of *n* stars

<p align="center"><img src="/tex/64bde763e5821069967e1e391f4bac5a.svg?invert_in_darkmode&sanitize=true" align=middle width=364.42559339999997pt height=16.438356pt/></p>

#### Satellite system

A satellite system is an orbiting system made of planets and satellites

<p align="center"><img src="/tex/9d4b5f833dfb579ad03602278b36f4bb.svg?invert_in_darkmode&sanitize=true" align=middle width=507.2573781pt height=16.438356pt/></p>

#### PlanetarySystem

A planetary system is an orbiting system made of a star system and "other smaller objects"

<p align="center"><img src="/tex/820eef59e87c82de7a589e65df9b3d1a.svg?invert_in_darkmode&sanitize=true" align=middle width=661.27634595pt height=16.438356pt/></p>

#### Galaxy

...

---

## Properties

### Having a barycenter

Objects have a barycenter

<p align="center"><img src="/tex/2538fae338263755e6f7133b3def9fc3.svg?invert_in_darkmode&sanitize=true" align=middle width=251.43208694999998pt height=14.611878599999999pt/></p>

<p align="center"><img src="/tex/a30d09aa6e3e8b35910ef72057fe6ef1.svg?invert_in_darkmode&sanitize=true" align=middle width=281.56929405pt height=16.438356pt/></p>

Thus points are barycenter of objects

<p align="center"><img src="/tex/10b74b04529755640c27fb27ea8e55d4.svg?invert_in_darkmode&sanitize=true" align=middle width=274.4031576pt height=41.01566205pt/></p>

### Orbiting

Points orbit around points:

<p align="center"><img src="/tex/ded01cc8598de3d5ccdb7866538c09a1.svg?invert_in_darkmode&sanitize=true" align=middle width=225.267999pt height=11.4155283pt/></p>

Thus points are orbited by points:

<p align="center"><img src="/tex/3a0db99845ecd9873b84b1464b0728e4.svg?invert_in_darkmode&sanitize=true" align=middle width=224.69250045pt height=17.1069228pt/></p>

Objects orbit with another object iif their barycenters orbit around the same point:

<p align="center"><img src="/tex/c0eaaafc9214dee482c0a4e16fa4473e.svg?invert_in_darkmode&sanitize=true" align=middle width=598.4964908999999pt height=39.2694126pt/></p>

Objects orbit in an orbiting system:

<p align="center"><img src="/tex/9b457f54ed73c00ed612fbad325ab2ad.svg?invert_in_darkmode&sanitize=true" align=middle width=468.17840025pt height=39.2694126pt/></p>

Thus orbiting system has orbiting components:
<p align="center"><img src="/tex/58664d61fac9cf02ef5687e4906dea9b.svg?invert_in_darkmode&sanitize=true" align=middle width=391.81789514999997pt height=41.01566205pt/></p>



### Mereology

Object are made of objects, such as usual. From the orbiting relation we can infer a mereology relation, such as:

<p align="center"><img src="/tex/74a119ea1a4ac7236296e696b0f51660.svg?invert_in_darkmode&sanitize=true" align=middle width=264.99195195pt height=16.438356pt/></p>

This is expressed simply with:

<p align="center"><img src="/tex/5999a4592974b37e7c31b707fc2ab05e.svg?invert_in_darkmode&sanitize=true" align=middle width=198.76655864999998pt height=14.611878599999999pt/></p>
