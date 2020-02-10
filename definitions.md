 <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> 

# Definitions

## Classes

Definitions taken from Wikipedia: [Astronomical object page](https://en.wikipedia.org/wiki/Astronomical_object), and following links.

*Note:* this document is a draft intended to define mrq's first concepts.

---

### Celestial object

An **Celestial object** (or "astronomical object") is a **Celestial body** or a group of **Celestial bodies**

---

### Celestial body

$$\dots$$

---

### Composite

A **Composite** is a group of **Celestial bodies**. It's only a group?

---

### Non_Composite

A **Non_Composite** is a **Celestial body**. Double definition :-(

---

### Nebula

A **Nebula** is a disjoint union of **Diffuse nebula**, **Planetary nebula**, **Supernova remnant** and **Dark nebula**.
$$Nebula ~ \equiv ~ DiffuseNebula ~ \sqcap ~ PlanetaryNebula ~ \sqcap ~ SupernovaRemnant ~ \sqcap ~ DarkNebula$$

---

### Star

A **Star** is a **Celestial Body** that...
$$Star ~ \equiv ~ CelestialBody ~ \sqcap ~ \dots$$

---

### *N*-ary star

A ***n*-ary star** is a **Star** that orbits *n*-1 **Stars**
\begin{align}
UnaryStar ~ &\equiv ~ Star ~ \sqcap ~ (=0 ~ orbits.Star) \\\\
BinaryStar ~ &\equiv ~ Star ~ \sqcap ~ (=1 ~ orbits.Star) \\\\
TernaryStar ~ &\equiv ~ Star ~ \sqcap ~ (=2 ~ orbits.Star)
\end{align}

*Note:* Is a *n*-ary star the group of stars?

---

### Planet

A **Planet** is a **Celestial Body** that *orbits* a **Star** and  \dots
$$Planet ~ \equiv ~ CelestialBody ~ \sqcap ~ (\leq 1 ~ orbits.Star) ~ \sqcap ~ \dots$$

---

### Satellite

A **Satellite** is a **Celestial Body** that orbits a **Planet**
$$Satellite ~ \equiv ~ CelestialBody ~ \sqcap ~ (\leq 1 ~ orbits.Planet)$$

---

### Moon

A **Moon** is a **Satellite** that is natural
$$Moon ~ \equiv ~ Satellite ~ \sqcap ~ creator.NoOne$$

---

## Relations

### Orbits

*Orbits* is the fact that a **Celestial object** "turns around" one other **Celestial object**. It is symmetric, but not reflexive.
$$orbits: CelestialObject \to CelestialObject$$

---

