Below is an example in Python that demonstrates how the cyclic group \(\mathbb{Z}_{12}\) is used to model transpositions in music theory. In this example, we represent a chord as a list of pitch classes and define a function to transpose the chord by a given interval modulo 12. This highlights the commutative (abelian) nature of the transposition operation.

```python
def transpose(pitch_classes, interval):
    """
    Transposes a list of pitch classes by the given interval.
    
    Parameters:
        pitch_classes (list of int): The original pitch classes (0-11).
        interval (int): The transposition interval (in semitones).
        
    Returns:
        list of int: The transposed pitch classes.
    """
    # Add the interval to each pitch class and take modulo 12 to wrap around
    return [(p + interval) % 12 for p in pitch_classes]

# Example: C major triad represented in pitch classes [C, E, G] = [0, 4, 7]
c_major = [0, 4, 7]

# Transpose the chord by 3 semitones
transposed_chord = transpose(c_major, 3)
print("Original C major triad (pitch classes):", c_major)
print("Transposed triad (by 3 semitones):", transposed_chord)

# Demonstrating the commutativity of transposition
# Transposing by 3 then 4 semitones should equal transposing by 4 then 3 semitones.
first_transposition = transpose(transpose(c_major, 3), 4)
second_transposition = transpose(transpose(c_major, 4), 3)
print("\nTransposing by 3 then 4 semitones:", first_transposition)
print("Transposing by 4 then 3 semitones:", second_transposition)
```

### Explanation

1. **Transposition Function:**  
   The `transpose` function takes a list of pitch classes and an interval, adds the interval to each pitch, and then takes the result modulo 12. This ensures that the pitch classes "wrap around" correctly within the set \(\{0, 1, \dots, 11\}\).

2. **C Major Triad:**  
   The C major triad is represented as `[0, 4, 7]`, corresponding to the pitch classes for C, E, and G.

3. **Transposition Example:**  
   When transposing the C major triad by 3 semitones, the function outputs the new set of pitch classes. 

4. **Commutativity Check:**  
   The code demonstrates that transposing by 3 semitones followed by 4 semitones yields the same result as transposing by 4 semitones followed by 3 semitones. This reflects the abelian (commutative) nature of the group operation in \(\mathbb{Z}_{12}\).

This simple Python example captures how abelian group properties are applied in music theory, particularly in the context of pitch class transposition.
