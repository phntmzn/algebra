Group theory can be a powerful mathematical framework for understanding chord progressions in music theory. In Python, we can use **permutation groups, cyclic groups, and dihedral groups** to analyze chord movements and symmetries in harmonic progressions.

### **1. Cyclic Groups and Chord Progressions**
In music, the **circle of fifths** forms a cyclic group. The **Z/12Z group** (integers modulo 12) is useful for analyzing chords because pitch classes repeat every octave.

#### **Example: Circle of Fifths as a Cyclic Group**
```python
import numpy as np

# Define pitch classes (mod 12)
pitch_classes = np.array([0, 7, 2, 9, 4, 11, 6, 1, 8, 3, 10, 5])  # Circle of Fifths (C-G-D-A-E-B-F#-Db-Ab-Eb-Bb-F)

# Cyclic group operation (mod 12)
def cyclic_shift(pitches, steps):
    return np.mod(pitches + steps, 12)

# Example: Move forward by a fifth (7 semitones)
new_pitch_classes = cyclic_shift(pitch_classes, 7)
print(new_pitch_classes)
```
This models how a chord progression moves along the circle of fifths.

---

### **2. Permutation Groups for Chord Transformations**
Chords can be represented as **sets of pitch classes**, and transformations between chords can be modeled using **permutation groups**.

#### **Example: Chord Inversion as a Permutation**
```python
from sympy.combinatorics import Permutation

# Define a C major chord (C-E-G) using pitch classes
C_major = [0, 4, 7]  # C, E, G

# Define an inversion permutation (swap E and G)
inversion = Permutation([0, 2, 1])  # Maps (C, E, G) -> (C, G, E)

# Apply permutation
C_major_inverted = [C_major[i] for i in inversion.array_form]
print(C_major_inverted)  # Output: [0, 7, 4]
```
This models chord inversions as elements of the **symmetric group** \( S_n \).

---

### **3. Dihedral Groups for Chord Symmetry**
The **dihedral group \( D_12 \)** captures **rotations and reflections**, useful for **modulating** between keys.

#### **Example: Reflection in the Circle of Fifths (Key Change)**
```python
def reflect_pitch(pitch, axis=6):
    """Reflect pitch across an axis in modulo 12 space."""
    return np.mod(2 * axis - pitch, 12)

# Reflect C major (C=0, E=4, G=7) over axis (e.g., F# = 6)
C_major_reflected = [reflect_pitch(p) for p in C_major]
print(C_major_reflected)  # Key transformation
```
This is a useful technique for **neo-Riemannian transformations** (e.g., **L, P, R moves** in the Tonnetz).

---

### **4. Generating Chord Progressions Using Group Actions**
A chord progression can be modeled as a **group action** on a set of chords.

#### **Example: Apply a Group Action to a Chord Progression**
```python
chord_progression = [[0, 4, 7], [5, 9, 0], [7, 11, 2], [9, 0, 4]]  # C, F, G, Am

# Define a transformation (transpose up by 2 semitones)
def transpose(chord, interval):
    return np.mod(np.array(chord) + interval, 12)

# Apply transformation to the whole progression
new_progression = [transpose(chord, 2) for chord in chord_progression]
print(new_progression)
```
This models **modulation and transposition** systematically.

---

### **Further Directions**
- **Tonnetz Representation** using **triadic groups**
- **PLR Transformations** in **neo-Riemannian theory**
- **Hexatonic & Octatonic Groups** for advanced jazz harmony

Would you like an example focusing on a specific genre (e.g., jazz, classical, pop)?
