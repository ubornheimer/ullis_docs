[https://youtu.be/AG3KuqDbmhM](https://youtu.be/AG3KuqDbmhM)

[https://www.youtube.com/watch?v=E8I19uA-wGY](https://www.youtube.com/watch?v=E8I19uA-wGY)

good python style [https://youtu.be/OSGv2VnC0go](https://youtu.be/OSGv2VnC0go)

[https://youtu.be/LEZv-kQUSi4](https://youtu.be/LEZv-kQUSi4)

[https://youtu.be/I52uPJSoAT4](https://youtu.be/I52uPJSoAT4) declarative style

```python
#---------------------------------------- iterate -----------------------------------------------
def iterate_implementation(x, f):
    """for a homomorphism f and initial val x: [x, f(x), f(f(x)), ...].
    Inspired by the excellent talk by Joel Grus on functional Python.
    
    ---- Examples ----
    >>> 42 | iterate[lambda x: x+1]                                         # => [42, 43, 44, ...]
    >>> 
    >>> # find all of Joe's friends on a graph up to third degree
    >>> ([z_joe, ] 
    >>>   | iterate[lambda z: z >> L[RT.FriendOf] | concat | distinct]      # flatten out and remove duplicates
    >>>   | take[3]
    >>> )


    ---- Signature ----
    (T, (T->T)) -> List[T]
    """
    # TODO: assert that fct is an endomorphism on zef_type(x)
    return itertools.accumulate(itertools.repeat(x), lambda fx, _: f(fx))
```

```python
# initial state
s0 = {
    'x': 4,
    'y': 2,
}

# iteration step
def step(s):
    return {
        'x': 4 - 0.1*s['y'],
        'y': 0.5*s['y'] + s['x'],
    }

# how long will we keep going? Look at diff in states
def continue_criterion(s_prev, s_next):
    return abs(s_prev['x'] - s_next['x']) > 1E-6

(s0 
 | iterate[step]                            # do the actual work: infinite sequence
 | take_while_pair[continue_criterion]      # when to stop
 | collect                                  # trigger evaluation
 )

Thursday, June 2nd
```