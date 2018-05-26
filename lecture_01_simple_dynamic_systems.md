
# Coding Theoretical Minimum

## Programmer notes from Leonard Susskind lectures book "The Theoretical Minimum. What you need to know to start doing physics". 

### Introduction

This works started as a personal excercise when reading a book by the charismatic professor of theoretical physics [Leonard Susskind](https://en.wikipedia.org/wiki/Leonard_Susskind). The book was entitled "The Theoretical Minimum. What you need to know to start doing physics". I started reading it because I realised at one moment that I know very little about how really the world works. It became aparent I need to learn. But where does one start? I decided to start from the very basic information about how stuff works: how the universe works? what we are made of? I needed basis for my research so I decided to invest in a handbook and title promissing "minimum" quickly caught my attention. 

Why coding then? For me the road to STEM goes actually from humanities (my first degree was in sociology). I decided to change my career and become an informatician (my second degree was in informatics, software development specialization). At that moment I did not know what exaclty it means. Fortunately I managed to complete studies and I realized that programming is the most satisfying task I ever did. Not until it happened I noticed there is a lot of science, math and physics is going on in the background. When I started to read more about physics I read a lot about particle accelerators, fields, electrons, photons, spins, fermions, bosons and other stuff. I thought then that there is a lot to it that resembles a computer program. Quantum mechanics I mean. Its descreet nature with its own logic that can be followed and decoded. On the other hand it is not fully deterministic. The deterministic common sense view about causes and effects is actually often far from valid on the quantum realm. The "fabric of reality" (David Deutch) is based on probabilitiy, not certanity, on interference, emergent properties. I realised that quantum fields theory tells a lot about the world, explains phenomena that I was not able to understand. And at the same time I tought It was understandable to me because the concept of a field resembled programming data structure. Quantum field is defined as a physical quantity that has a value in each point ([Wikipedia](https://en.wikipedia.org/wiki/Field_(physics))). 


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
    
    def __len__(self):
        return(len(self.points))
    
    def __getitem__(self,key):
        return(self.points[key])
    
    def __iter__(self):
        for point in self.points:
            yield(point)
            
    def states(self):
        return(np.unique(self.points))

f = Field('my field',[1,0,1,0,0,0,0,1,0,1])
assert(len(f) == 10)
assert(f[0] == 1)
assert(f[1] == 0)
assert([x for x in f] == [1,0,1,0,0,0,0,1,0,1])
np.testing.assert_array_equal(f.states(),np.array([0,1]))
```

The field can have type label but what is more important it has array of points. It has information for every point so item n in the array will represent point n in the space of the field. The field modeled above has only two states (possible values). For me this type of thinking helped a lot in understanding the theoretical concept. What is more, I immediately saw its applications. I quickly noticed how this explains a lot of things I could not understand without such a mind model. If this description seems pleasant to you then I hope you will find the rest of the stuff interesting.

### Simple dynamic systems and state space
Leonard Susskind starts his lectures with the simplest model there can be. He begins by saying that a system is a collection of objects.


```python
class System:
    """ A system is a collection of objects """
    def __init__(self,objects = []):
        self.objects = objects
    
    def __len__(self):
        return(len(self.objects))
    
    def __getitem__(self,key):
        return(self.objects[key])
    
    def __iter__(self):
        for object in self.objects:
            yield(object)
    
    def __repr__(self):
        return("{}".format(str(self.objects)))
```

    ['a', 'b', 'c']


Notice that we may think about a system that contains everything or is so much isolated that it seems nothing else exists for the system. We call this kind of system a closed system. We may think aobut this as an immutable data structure. We may look at the object, we may ask questions, but we cannot do anything else about it. We can just observe. 


```python
class Closed_system:
    """ A system that is immutable and isolated from the outside """
    def __init__(self,objects = ()):
        self.objects = objects
    
    def __repr__(self):
        return("{}".format(str(self.objects)))
    
    def __iter__(self):
        for object in self.objects:
            yield(object)
    
c = Closed_system(objects = ('a','b','c'))
assert(list([x for x in c]) == ['a','b','c'])
```

Objects may carry information about state. That's like state machine in programming. The complete set of states that an object can have is called state space of the system. Let us start with the most simple case: an object that has only one state, that is it has no state. It is stateless.


```python
class Stateless:
    """ system with state space containing single element """
    def __init__(self):
        self.state_space = ['O']
        self.value = 'O'
    
    def __repr__(self):
        return("{}".format(self.value))
        
s = Stateless()
for x in range(0,5):
    print(s)
```

    O
    O
    O
    O
    O


At the first sight it may seem banal or boring, but it is actually useful. Notice that we can repeat actions and result will always be the same, guaranteed. This means potential for parrallelism and scalability. 
