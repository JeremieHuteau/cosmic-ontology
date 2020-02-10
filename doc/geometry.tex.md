# Orbiting barycenters

## Definitions

### Base classes

A point is a spatial 1-d location. It has only one position at once.

$$Point ~ \equiv ~ \dots$$

A mass is a positive quantity.

$$Mass ~ \sqsubseteq ~ \text{xsd:float}$$

---

### Barycenter

A Barycenter have a point location and a mass.

$$Barycenter ~ \sqsubseteq ~ (= 1 ~ hasLocation.Point)  ~ \sqcap ~ (=1 ~ hasMass.Mass)$$

We can consider that objects (such as Earth or the solar system) are their own barycenters, or that barycenter are abstract entities objects are related to.

---

### Orbiting

To orbit is the action of a barycenter to revolve around another barycenter.

$$orbit: ~ Barycenter \to Barycenter$$

Barycenters are intended to orbit around other barycenters, but not restricted to.

$$Barycenter ~ \sqsubseteq ~ (\leq 1 ~orbit.Barycenter)$$


---

## Example

Consider the toy-example {Sun, Earth, Moon}.

	# Classes
	CelestialObject subClassOf Thing
	CelestialBody subclassOf CelestialObject
	
	# Entities
	SUN isA CelestialBody
	EARTH isA CelestialBody
	MOON isA CelestialBody
	EARTH_SYSTEM isA CelestialObject
	SOLAR_SYSTEM isA CelestialObject
	
	# Mereology
	EARTH partOf EARTH_SYSTEM
	MOON partOf EARTH_SYSTEM
	SUN partOf SOLAR_SYSTEM
	EARTH_SYSTEM partOf SOLAR-SYSTEM

We have two alternatives:

- Objects **are** barycenters
- Objects **have** barycenters

a. Objects *are* their own barycenters. Thus they have a 1-d location and a mass.

	# Being a barycenter
	CelestialObject subClassOf Barycenter

	EARTH orbit EARTH_SYSTEM
	MOON orbit EARTH_SYSTEM
	SUN orbit SOLAR_SYSTEM
	EARTH_SYSTEM orbit SOLAR_SYSTEM

b. Objects *have* a barycenter that is an external abstract entity .

	# Having a barycenter
	CelestialObject subClassOf hasBarycenter.Barycenter

	SUN_BC isA Barycenter
	EARTH_BC isA Barycenter
	MOON_BC isA Barycenter
	EARTH_SYSTEM_BC isA Barycenter
	SOLAR_SYSTEM_BC isA Barycenter
	
	SUN hasBarycenter SUN_BC
	EARTH hasBarycenter EARTH_BC
	MOON hasBarycenter MOON_BC
	EARTH_SYSTEM hasBarycenter EARTH_SYSTEM_BC
	SOLAR_SYSTEM hasBarycenter SOLAR_SYSTEM_BC
	
	EARTH_BC orbit EARTH_SYSTEM_BC
	MOON_BC orbit EARTH_SYSTEM_BC
	SUN_BC orbit SOLAR_SYSTEM_BC
	EARTH_SYSTEM_BC orbit SOLAR_SYSTEM_BC

