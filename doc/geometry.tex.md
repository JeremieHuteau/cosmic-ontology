# Orbiting systems

We want to define orbiting systems.

Consider the toy system with 3 bodies: the sun, the earth and the moon.

1. The sun, the earth and the moon are located by their individual barycenters
2. The earth and the moon orbit around their common barycenter which is the location of the "earth system"
3. The earth system and the sun orbit around their common barycenter which is the location of the solar system

We want to modelize that:

- The solar system is made up of the sun, the earth and the moon (mereology)
- The solar system is orbited by the sun and the earth system which is orbited by the earth and the moon (set theory)

---

## Definitions

### Base classes

A **Location** is an abstract 0-dimensional region

$$Location ~ \sqsubseteq ~ \top$$

An **LocatedThing** is anything that have a location

$$LocatedThing ~ \equiv ~ (= 1 ~ isLocatedAt.Location)$$

Maybe we shoud ensure that those two classes are disjoint.

### Base relations

A LocatedThing **isLocatedAt** a Location that **isLocationOf** it.

A location **orbitsAround** another Location that **isOrbitedBy** it.

### Infered classes

An **OrbitalSystem** is a Thing which Location isOrbitedBy something.

$$OrbitalSystem ~ \equiv ~ (= 1 ~ isLocatedAt.(\geq 1 ~ isOrbitedBy.\top))$$

### Infered relations

Something **isIn** an OrbitalSystem that **contains** it (ensemblistic operators) iif its location orbitsAround the location of the OrbitalSystem.

$$isIn ~ \equiv ~ isLocatedAt ~ \circ ~ orbitsAround ~ \circ ~ isLocationOf$$

A Thing is **partOf** a Thing that **isMadeOf** it (mereologic operators) iif it isIn that Thing of it isIn something that isIn that Thing (transitive closure).

$$partOf ~ \equiv ~ isIn^+$$

---

## Back to our toy example

	# Located things
	SUN isA LocatedThing
	EARTH isA LocatedThing
	MOON isA LocatedThing
	EARTH_SYSTEM isA LocatedThing
	SOLAR_SYSTEM isA LocatedThing
	
	# Locations
	EARTH_BC isA Location
	EARTH isLocatedAt EARTH_BC
	MOON_BC isA Location
	MOON isLocatedAt MOON_BC
	EARTH_SYSTEM_BC isA Location
	EARTH_SYSTEM isLocatedAt EARTH_SYSTEM_BC
	
	# 1. Partial relationships
	EARTH_BC orbitsAround EARTH_SYSTEM_BC
	MOON_BC orbitsAround EARTH_SYSTEM_BC
	
	# 2. Partial relationships
	EARTH_SYSTEM_BC isIn SOLAR_SYSTEM
	SUN isIn SOOLAR_SYSTEM
