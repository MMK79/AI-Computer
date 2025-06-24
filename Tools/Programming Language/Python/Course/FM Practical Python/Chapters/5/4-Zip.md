* To iterate over bunch of list at a same time
	* lists should have same length (or else it will terminate base on the smallest list length)
 * Zip is a [[2-Generator Expression|Generator type]], it will get exhaust after first iteration through it

```
names = ["Bob", "Alice", "Eve"]
scores = [42, 97, 68]

for name, score in zip(names, scores):
    print(f"{name} has {score} score")
```