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

$$Point ~ \sqsubseteq ~ SpatialRegion$$

---

### Object

An object is a concrete thing

#### CelestialObject

A celestial object is an object that is considered by astronomist as a "celestial object"

$$CelestialObject ~ \sqsubseteq ~ Object$$

*Subclasses:* CelestialBody, Galaxy, PlanetarySystem

---

#### CelestialBody

A celestial body is an atomic celestial object (that is, an object that follow the astronomocal definition)

$$CelestialBody ~ \sqsubseteq ~ CelestialObject$$

*Subclasses:* Moon, Planet, Star, Nebula

---

#### OrbitingSystem

An orbiting system is an object whose barycenter is orbited by the barycenter of some objects

$$\begin{align*}
OrbitingSystem ~ & \equiv ~ Object ~ \sqcap ~ (\geq 1 ~ hasOrbitingComponent.Object) \\
& \equiv ~ Object ~ \sqcap ~ (= 1 ~ hasBarycenter.(\geq 1 ~ isOrbitedBy.Point))\end{align*}$$

*Subclasses:* StarSystem, PlanetarySystem, SatelliteSystem, Galaxy

--- 

#### Satellite

A satellite is an object.

$$Satellite ~ \sqsubseteq ~ Object$$

*Subclasses:* Moon

---

#### Moon

A moon is a celestial body that is a natural satellite

$$Moon ~ \sqsubseteq ~ Satellite ~ \sqcap ~ CelestialBody$$

---

#### Planet

---

#### Star

---

#### Nebula

---

#### StarSystem

A star system is an orbiting system made of stars only

$$StarSystem ~ \equiv ~ (\forall hasOrbitingComponent.Star)$$

*Subclasses:* UnaryStar, BinaryStar, TernaryStar

---

#### N-ary stars

Definition for UnaryStar, BinaryStar and TernaryStar

A *n*-ary star is a star system made of *n* stars

$$NaryStar ~ \equiv ~ (= n ~ hasOrbitingComponent.Star)$$

---

#### Satellite system

A satellite system is an orbiting system made of planets and satellites

$$SatelliteSystem ~ \equiv ~ (\forall hasOrbitingComponent.(Planet ~ \sqcup ~ Satellite))$$

---

#### PlanetarySystem

A planetary system is an orbiting system made of a star system and "other smaller objects"

$$PlanetarySystem ~ \equiv ~ (\forall hasOrbitingComponent.(StarSystem ~ \sqcup ~ SatelliteSystem ~ \sqcup ~ \dots)$$

---

#### Galaxy

...

---

## Properties

### Having a barycenter

Objects have a barycenter

$$hasBarycenter ~ : ~ Object \to Point$$

$$Object ~ \sqsubseteq ~ (= 1 ~ hasBarycenter.Point)$$

Thus points are barycenter of objects

$$\begin{align}
isBarycenterOf & ~ : ~ Point \to Object \\\\
isBarycenterOf & ~ \equiv ~ hasBarycenter^-
\end{align}$$

---

### Orbiting

Points orbit around points:

$$orbitAround ~ : ~ Point \to Point$$

Thus points are orbited by points:

$$isOrbitedBy ~ \equiv ~ orbitAround^-$$

Objects orbit with another object iif their barycenters orbit around the same point:

$$\begin{align}
orbitWith ~ & : ~ Object \to Object \\\\
orbitWith ~ & \equiv ~ hasBarycenter ~ \circ ~ orbitAround ~ \circ ~ isOrbitedBy ~ \circ ~ isBarycenterOf
\end{align}$$

Objects orbit in an orbiting system:

$$\begin{align}
orbitsIn ~ & : ~ Object \to OrbitingSystem \\\\
orbitsIn ~ & \equiv ~ hasBarycenter ~ \circ ~ orbitAround ~ \circ ~ isBarycenterOf
\end{align}$$

Thus orbiting system has orbiting components:
$$\begin{align}
hasOrbitingComponent ~ & : ~ OrbitingSystem \to Object\\\\
hasOrbitingComponent ~ & \equiv ~ orbitsIn^-
\end{align}$$



### Mereology

Object are made of objects, such as usual. From the orbiting relation we can infer a mereology relation, such as:

$$orbitsIn(?x, ?y) \to isPartOf(?x, ?y)$$

This is expressed simply with:

$$orbitsIn.\top ~ \sqsubseteq ~ isPartOf.\top$$