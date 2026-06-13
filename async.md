[https://realpython.com/async-io-python/](https://realpython.com/async-io-python/)

[https://www.terriblecode.com/blog/asynchronous-http-requests-in-python/](https://www.terriblecode.com/blog/asynchronous-http-requests-in-python/)

```python
async def factorial(name, number):
    f = 1
    for i in range(2, number + 1):
        print(f"Task {name}: Compute factorial({i})...")
        await asyncio.sleep(1)
        f *= i
    print(f"Task {name}: factorial({number}) = {f}")
    return f
    
async def run_gather_kwargs(my_dict: dict):
    res = await asyncio.gather(     #executes and collects in parallel. Returns a list with the individual results
        *[factorial(**my_dict) for k in range(7)]
    )
    print(res)
asyncio.run(run_gather_kwargs({'name': 'Luna', 'number': 5}))
```
