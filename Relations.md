# Relations
## This was a Jupyter notebook (converted into Markdown) about binary relation and its properties. Hopefully, this can help you understand the difference between each properties, and how to determine which property/properties a Relation possesses.
### Properties of Relation:
1. Reflexive
2. Irreflexive
3. Symmetric
4. Asymmetric
5. Antisymmetric
6. Transitive
### Reflexive
#### (a,a) ∈ R for every element a ∈ A
As long as every possible (a, a) is in the Relation, it is Reflexive.

```
# List the Binary Relation to evaluate
to_eval = [(1,1), (1,2), (1,4), (2,1), (2,2), (3,3), (4,1), (4,4)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (3, 3), (4, 1), (4, 4)]

```
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

Unique values:  [1, 2, 4, 3]

```
# Determine the reflexive elements it must posses
reflexive_elements = []
for index in range(len(unique)):
    a = unique[index]
    reflexive_elements.append((a,a))
print("Reflexive elements: ", reflexive_elements)
```

Reflexive elements:  [(1, 1), (2, 2), (4, 4), (3, 3)]

```
# Determine if the Relation is reflexive
reflexive = []
for index in range(len(reflexive_elements)):
    if not reflexive_elements[index] in to_eval:
        reflexive.append(True) 
        break   
if len(reflexive) > 0:
    print("The Relation is not reflexive")
else:
    print("The Relation is reflexive")
```

The Relation is reflexive

### Irreflexive
#### ∀a [ (a,a) ∉ R ]
As long as there is no (a, a) in the Relation, it is Irreflexive.

```
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (2,1), (4,1)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 2), (1, 4), (2, 1), (4, 1)]

```
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

Unique values:  [1, 2, 4]

```
# Determine the reflexive elements it must not posses
reflexive_elements = []
for index in range(len(unique)):
    a = unique[index]
    reflexive_elements.append((a,a))
print("Reflexive elements: ", reflexive_elements)
```

Reflexive elements:  [(1, 1), (2, 2), (4, 4)]

```
# Determine if the Relation is irreflexive:
irreflexive = []
for index in range(len(reflexive_elements)):
    if reflexive_elements[index] in to_eval:
        irreflexive.append(True)
        break
if len(irreflexive) > 0:
    print("The Relation is not irreflexive")
else:
    print("The Relation is irreflexive")
```

The Relation is irreflexive

### Symmetric
#### ∀a ∀b [ (a,b) ∈ R -> (b,a) ∈ R ]
If (a, b) was mentioned in the Relation, (b, a) must also be in the Relation, otherwise it is not Symmetric.

```
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (2,1), (4,1)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 2), (1, 4), (2, 1), (4, 1)]

```
# Determine if the Relation is symmetric
symmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if not (b, a) in to_eval:
        symmetric.append(True)
        break
if len(symmetric) > 0:
    print("The Relation is not symmetric")
else:
    print("The Relation is symmetric")
```

The Relation is symmetric

### Asymmetric
#### ∀a ∀b [ (a,b) ∈ R -> (b,a) ∉ R ]
For all (a, b) mentioned, the relation must not have (b, a).

```
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (1, 3)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 2), (1, 4), (1, 3)]

```
# Determine if asymmetric
asymmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if (b, a) in to_eval:
        asymmetric.append(True)
        break
if len(asymmetric) > 0:
    print("The Relation is not asymmetric")
else:
    print("The Relation is asymmetric")
```

The Relation is asymmetric

### Antisymmetric
#### ∀a ∀b [ ( (a,b) ∈ R & (b,a) ∉ R) -> (a = b) ]
If (a, b) and (b, a) is in the Relation, a must be equal to b.

```
# List the Relation to evaluate
to_eval = [(1,1), (1,2), (2,2), (3,1), (3,3)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 1), (1, 2), (2, 2), (3, 1), (3, 3)]

```
# Determine if the Relation is antisymmetric
antisymmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if (b, a) in to_eval and a != b:
        antisymmetric.append(True)
        break
if len(antisymmetric) > 0:
    print("The Relation is not antisymmetric")
else:
    print("The Relation is antisymmetric")
```

The Relation is antisymmetric

### Transitive
#### (a,b) ∈ R and (b,c) ∈ R, then (a,c) ∈ R, for all a,b,c ∈ A
if (a, b) and (b, c) is in the Relation, (a, c) must also be in the Relation.

```
# List the Relation to evaluate
to_eval = [(1,1), (1,2), (1,4), (2,1), (2,2), (2,4), (3,3), (4,1), (4,2), (4,4)]
print("The given Relation: ", to_eval)
```

The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (2, 4), (3, 3), (4, 1), (4, 2), (4, 4)]

```
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

Unique values:  [1, 2, 4, 3]

```
# Determine if the Relation is transitive
transitive = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    for inner in range(len(unique)):
        c = unique[inner]
        if (b, c) in to_eval and (a, c) not in to_eval:
            transitive.append(True)
            break
if len(transitive) > 0:
    print("The Relation is not transitive")
else:
    print("The Relation is transitive")
```

The Relation is transitive

---

#### This is the end of the discussion.
You can use the code below to determine which property/properties a Relation posses. You can copy it then paste it [here](https://www.programiz.com/python-programming/online-compiler/). 

```
# List the Relation to evaluate
to_eval = [(1,1), (1,2), (1,4), (2,1), (2,2), (2,4), (3,3), (4,1), (4,4)]
print("The given Relation: ", to_eval)

# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)

# Determine the reflexive elements it must posses
reflexive_elements = []
for index in range(len(unique)):
    a = unique[index]
    reflexive_elements.append((a,a))
print("Reflexive elements: ", reflexive_elements)

# Determine if the Relation is reflexive
reflexive = []
for index in range(len(reflexive_elements)):
    if not reflexive_elements[index] in to_eval:
        reflexive.append(True) 
        break   
if len(reflexive) > 0:
    print("The Relation is not reflexive")
else:
    print("The Relation is reflexive")

# Determine if the Relation is irreflexive:
irreflexive = []
for index in range(len(reflexive_elements)):
    if reflexive_elements[index] in to_eval:
        irreflexive.append(True)
        break
if len(irreflexive) > 0:
    print("The Relation is not irreflexive")
else:
    print("The Relation is irreflexive")

# Determine if the Relation is symmetric
symmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if not (b, a) in to_eval:
        symmetric.append(True)
        break
if len(symmetric) > 0:
    print("The Relation is not symmetric")
else:
    print("The Relation is symmetric")

# Determine if asymmetric
asymmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if (b, a) in to_eval:
        asymmetric.append(True)
        break
if len(asymmetric) > 0:
    print("The Relation is not asymmetric")
else:
    print("The Relation is asymmetric")

# Determine if the Relation is antisymmetric
antisymmetric = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    if (b, a) in to_eval and a != b:
        antisymmetric.append(True)
        break
if len(antisymmetric) > 0:
    print("The Relation is not antisymmetric")
else:
    print("The Relation is antisymmetric")

# Determine if the Relation is transitive
transitive = []
for index in range(len(to_eval)):
    a = to_eval[index][0]
    b = to_eval[index][1]
    for inner in range(len(unique)):
        c = unique[inner]
        if (b, c) in to_eval and (a, c) not in to_eval:
            transitive.append(True)            
            break
if len(transitive) > 0:
    print("The Relation is not transitive")
else:
    print("The Relation is transitive")
```

The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (2, 4), (3, 3), (4, 1), (4, 4)]

Unique values:  [1, 2, 4, 3]

Reflexive elements:  [(1, 1), (2, 2), (4, 4), (3, 3)]

The Relation is reflexive

The Relation is not irreflexive

The Relation is not symmetric

The Relation is not asymmetric

The Relation is not antisymmetric

The Relation is not transitive