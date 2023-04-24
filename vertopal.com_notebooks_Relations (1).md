---
jupyter:
  kernelspec:
    display_name: Python (Pyodide)
    language: python
    name: python
  language_info:
    codemirror_mode:
      name: python
      version: 3
    file_extension: .py
    mimetype: text/x-python
    name: python
    nbconvert_exporter: python
    pygments_lexer: ipython3
    version: 3.8
  nbformat: 4
  nbformat_minor: 5
---

::: {#c1a2610b-2e69-459e-b621-93f11c90b1ff .cell .markdown}
# This was a Jupyter notebook (coverterd into Markdown) about binary relation and its properties. Hopefully, this can help you understand the difference between each properties, and how to determine which property/properties a Relation possesses. {#this-was-a-jupyter-notebook-coverterd-into-markdown-about-binary-relation-and-its-properties-hopefully-this-can-help-you-understand-the-difference-between-each-properties-and-how-to-determine-which-propertyproperties-a-relation-possesses}

## Properties of Relation:

1.  Reflexive
2.  Irreflexive
3.  Symmetric
4.  Asymmetric
5.  Antisymmetric
6.  Transitive
:::

::: {#93999f7c-10c2-40f4-aff7-03cb3060f9ec .cell .markdown}
### Reflexive

#### (a,a) ∈ R for every element a ∈ A {#aa--r-for-every-element-a--a}

##### As long as every possible (a, a) is in the Relation, it is Reflexive. {#as-long-as-every-possible-a-a-is-in-the-relation-it-is-reflexive}
:::

::: {#ecfa2e8c-d873-4ff1-b91f-ecac68254cec .cell .code execution_count="1" trusted="true"}
``` python
# List the Binary Relation to evaluate
to_eval = [(1,1), (1,2), (1,4), (2,1), (2,2), (3,3), (4,1), (4,4)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (3, 3), (4, 1), (4, 4)]
:::
:::

::: {#73106794-f819-4295-a7df-2cd8201f8ae6 .cell .code execution_count="2" trusted="true"}
``` python
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

::: {.output .stream .stdout}
    Unique values:  [1, 2, 4, 3]
:::
:::

::: {#6b128dfe-3e06-4fe2-a389-a788baa4a51d .cell .code execution_count="3" trusted="true"}
``` python
# Determine the reflexive elements it must posses
reflexive_elements = []
for index in range(len(unique)):
    a = unique[index]
    reflexive_elements.append((a,a))
print("Reflexive elements: ", reflexive_elements)
```

::: {.output .stream .stdout}
    Reflexive elements:  [(1, 1), (2, 2), (4, 4), (3, 3)]
:::
:::

::: {#d43a9867-aff8-4183-850c-aeb08a512dd2 .cell .code execution_count="4" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is reflexive
:::
:::

::: {#bad2bf5c-7741-49c4-9783-69278c443e8d .cell .markdown}
### Irreflexive

#### ∀a \[ (a,a) ∉ R \] {#a--aa--r-}

##### As long as there is no (a, a) in the Relation, it is Irreflexive. {#as-long-as-there-is-no-a-a-in-the-relation-it-is-irreflexive}
:::

::: {#14d291a8-ab59-4c65-9bb1-70226fd4fbfd .cell .code execution_count="5" trusted="true"}
``` python
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (2,1), (4,1)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 2), (1, 4), (2, 1), (4, 1)]
:::
:::

::: {#9c6454cf-86fd-4a5f-bcc5-bdf2f35d8e0b .cell .code execution_count="6" trusted="true"}
``` python
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

::: {.output .stream .stdout}
    Unique values:  [1, 2, 4]
:::
:::

::: {#675373f9-9054-4c71-a8a4-69e5c747db46 .cell .code execution_count="7" trusted="true"}
``` python
# Determine the reflexive elements it must not posses
reflexive_elements = []
for index in range(len(unique)):
    a = unique[index]
    reflexive_elements.append((a,a))
print("Reflexive elements: ", reflexive_elements)
```

::: {.output .stream .stdout}
    Reflexive elements:  [(1, 1), (2, 2), (4, 4)]
:::
:::

::: {#a15dc793-dcc2-4828-aebc-3753e8c132de .cell .code execution_count="8" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is irreflexive
:::
:::

::: {#d8632cbc-348c-4719-85e9-6dd4206e3512 .cell .markdown}
### Symmetric

#### ∀a ∀b \[ (a,b) ∈ R -\> (b,a) ∈ R \] {#a-b--ab--r---ba--r-}

##### If (a, b) was mentioned in the Relation, (b, a) must also be in the Relation, otherwise it is not Symmetric. {#if-a-b-was-mentioned-in-the-relation-b-a-must-also-be-in-the-relation-otherwise-it-is-not-symmetric}
:::

::: {#a34e5bcc-ae46-4eaa-8809-0c34e5975451 .cell .code execution_count="9" trusted="true"}
``` python
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (2,1), (4,1)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 2), (1, 4), (2, 1), (4, 1)]
:::
:::

::: {#57622dc3-988d-4426-967c-46cbc4b49f47 .cell .code execution_count="10" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is symmetric
:::
:::

::: {#e56ed920-fc96-4030-8c07-627f752f71c9 .cell .markdown}
### Asymmetric

#### ∀a ∀b \[ (a,b) ∈ R -\> (b,a) ∉ R \] {#a-b--ab--r---ba--r-}

##### For all (a, b) mentioned, the relation must not have (b, a). {#for-all-a-b-mentioned-the-relation-must-not-have-b-a}
:::

::: {#c0ff34bf-b976-4132-915f-e31e56bc094a .cell .code execution_count="11" trusted="true"}
``` python
# List the Relation to evaluate
to_eval = [(1,2), (1,4), (1, 3)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 2), (1, 4), (1, 3)]
:::
:::

::: {#d2a66c76-d1f2-4d29-bbbb-70b027247245 .cell .code execution_count="12" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is asymmetric
:::
:::

::: {#c663d26f-c21c-4c02-b847-00b937002e44 .cell .markdown}
### Antisymmetric

#### ∀a ∀b \[ ( (a,b) ∈ R & (b,a) ∉ R) -\> (a = b) \] {#a-b---ab--r--ba--r---a--b-}

##### If (a, b) and (b, a) is in the Relation, a must be equal to b. {#if-a-b-and-b-a-is-in-the-relation-a-must-be-equal-to-b}
:::

::: {#83b5b61e-7216-4201-ac9a-8347cac0c256 .cell .code execution_count="13" trusted="true"}
``` python
# List the Relation to evaluate
to_eval = [(1,1), (1,2), (2,2), (3,1), (3,3)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 1), (1, 2), (2, 2), (3, 1), (3, 3)]
:::
:::

::: {#1b2b1b36-62e3-495a-8826-b39a3efc4048 .cell .code execution_count="14" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is antisymmetric
:::
:::

::: {#714c2a18-a5dc-4ea5-8128-09c68c54edba .cell .markdown}
### Transitive

#### (a,b) ∈ R and (b,c) ∈ R, then (a,c) ∈ R, for all a,b,c ∈ A {#ab--r-and-bc--r-then-ac--r-for-all-abc--a}

##### If (a, b) and (b, c) is in the Relation, (a, c) must also be in the Relation. {#if-a-b-and-b-c-is-in-the-relation-a-c-must-also-be-in-the-relation}
:::

::: {#7e39390c-d42e-49cb-b3d0-a7fa615c3dc2 .cell .code execution_count="15" trusted="true"}
``` python
# List the Relation to evaluate
to_eval = [(1,1), (1,2), (1,4), (2,1), (2,2), (2,4), (3,3), (4,1), (4,2), (4,4)]
print("The given Relation: ", to_eval)
```

::: {.output .stream .stdout}
    The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (2, 4), (3, 3), (4, 1), (4, 2), (4, 4)]
:::
:::

::: {#03118929-6761-4aa9-b5b5-b721467e98df .cell .code execution_count="16" trusted="true"}
``` python
# Determine the unique values in the Relation
unique = []
for index in range(len(to_eval)):
    if not to_eval[index][0] in unique:
        unique.append(to_eval[index][0])
    if not to_eval[index][1] in unique:
        unique.append(to_eval[index][1])
print("Unique values: ", unique)
```

::: {.output .stream .stdout}
    Unique values:  [1, 2, 4, 3]
:::
:::

::: {#97448a10-4084-4c26-a083-ec8e7bf9c332 .cell .code execution_count="17" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The Relation is transitive
:::
:::

::: {#58009331-a95a-4bdb-8845-dfda36c6b2c0 .cell .markdown}
## This is the end of the discussion. {#this-is-the-end-of-the-discussion}

### You can use the code below to determine which property/properties a Relation posses. You can copy the code below and paste it here. {#you-can-use-the-code-below-to-determine-which-propertyproperties-a-relation-posses-you-can-copy-the-code-below-and-paste-it-here}
:::

::: {#c2740d35-53a8-448d-9731-cbbbab571030 .cell .code execution_count="18" trusted="true"}
``` python
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

::: {.output .stream .stdout}
    The given Relation:  [(1, 1), (1, 2), (1, 4), (2, 1), (2, 2), (2, 4), (3, 3), (4, 1), (4, 4)]
    Unique values:  [1, 2, 4, 3]
    Reflexive elements:  [(1, 1), (2, 2), (4, 4), (3, 3)]
    The Relation is reflexive
    The Relation is not irreflexive
    The Relation is not symmetric
    The Relation is not asymmetric
    The Relation is not antisymmetric
    The Relation is not transitive
:::
:::
