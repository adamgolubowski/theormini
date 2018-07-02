
# Coding Theoretical Minimum

## Programmer notes from Leonard Susskind lectures book "The Theoretical Minimum. What you need to know to start doing physics". 

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
