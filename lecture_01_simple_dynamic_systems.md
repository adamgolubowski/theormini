
# Coding Theoretical Minimum

## Programmer notes from Leonard Susskind lectures book "The Theoretical Minimum. What you need to know to start doing physics". 

### Introduction

This works started as a personal excercise when reading a book by the charismatic professor of theoretical physics [Leonard Susskind](https://en.wikipedia.org/wiki/Leonard_Susskind). The book was entitled "The Theoretical Minimum. What you need to know to start doing physics". I started reading it because I realised at one moment that I know very little about how really the world works. It became aparent I need to learn. But where does one start? I decided to start from the very basic information about how stuff works: how the universe works? what we are made of? I needed basis for my research so I decided to invest in a handbook and title promissing "minimum" quickly caught my attention. 

Why coding then? For me the road to STEM goes actually from humanities (my first degree was in sociology). I decided to change my career and become an informatician (my second degree was in informatics, software development specialization). At that moment I did not know what exaclty it means. Fortunately I managed to complete studies and I realized that programming is the most satisfying task I ever did. Not until it happened I noticed there is a lot of science, math and physics is going on in the background. When I started to read more about physics I read a lot about particle accelerators, fields, electrons, photons, spins, fermions, bosons and other stuff. I thought then that there is a lot to it that resembles a computer program. Quantum mechanics I mean. Its descreet nature with its own logic that can be followed and decoded. On the other hand it is not fully deterministic. The deterministic common sense view about causes and effects is actually often far from valid on the quantum realm. The "fabric of reality" (David Deutch) is based on probabilitiy, not certanity, on interference, emergent properties. I realised that quantum fields theory tells a lot about the world, explains phenomena that I was not able to understand. And at the same time I tought It was understandable to me because the concept of a field resembled programming data structure. Quantum field is defined as a physical quantity that has a value in each point ([Wikipedia](https://en.wikipedia.org/wiki/Field_(physics)). 


```python
import numpy as np

class Field:
    """ A field is a quantity that has a value in each point.
        Assume 1 dimensonal space. In the definition there is no requirements
        for complex spaces, so we start simple. """
    def __init__(self,type = 'default', points = [0]):
        self.type = type
        self.points = np.array(points)
    
    def __repr__(self):
        return("{} '{}'".format(self.type,self.points))
    

f = Field('my field',[1,0,1,0,0,0,0,1,0,1])
print(f)
        
        

```

    my field '[1 0 1 0 0 0 0 1 0 1]'


The field can have type label but what is more important it has array of points. It has information for every point so item n in the array will represent point n in the space of the field.
