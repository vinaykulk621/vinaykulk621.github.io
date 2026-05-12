+++
date = '2026-05-12T23:23:10+05:30'
title = 'Merkle Tree'
+++

it's an algorithm to validate the correctness of huge data using hashes of chunks of data

ex:

1. A file of 10GB "**Passwords**" can be broken down into multiple pieces of smaller size,
2. lets call these smaller sizes A, B, C and D.
3. create a merkle tree for this Data chunks in the below manner:

```
hA = hash(A)
hB = hash(B)
hC = hash(C)
hD = hash(D)

hAB = hash(hA + hB)
hCD = hash(hC + hD)

root = hash(hAB + hCD)
```

5. to verify that a random given part of this file X is actually part of this 10GB "**Passwords**" file, we create hash of X viz: `hX = hash(X)` and merkle proof is given: `[hB, hCD]`
6. merkle proof: it's all hashed the siblings of the X which leads up to root
   1. we reach to the root by following the merkle proof
   2. ex: merkle proof in case of [[BitTorent]]:

```bash
[
  {
    position: LEFT/RIGHT,
    hash: sibling_hash
  },
  ...
]
```

7. Here the order LEFT/RIGHT matters as hashes are one way
8. You walk through each of these objects in the given merkle tree,
9. Each object is a sibling you need to has with the given data's hash(viz: X)
10. if `position == LEFT`: `hXS = hash(sibling_hash + hX)`
11. if `position == RIGHT`: `hSX = hash(hX + sibling_hash)`
12. Once you do this for all objects in the given merkle proof, you compare the produced root with actual root of "**Password**" file to validate correctness of the given data

pseudo validation code:

```python
# psuedo merkle path validation
# author: vinakulk621<kulkarnivinay621@gmail.com>

# merkel tree:
#        root
#       /    \
#    hAB      hCD
#   /   \    /   \
# hA    hB  hC    hD

def hash(data):
    return sha256(data)

root_hash = hash("ABCD")  # original root hash for the data
X = "A"  # Given data point
merkle_proof = [
    {"position": "LEFT", "hashed_data": "hB"},  # first sibling
    {"position": "RIGHT", "hashed_data": "hCD"},  # second sibling
]


def merkel_verify(merkle_proof, root_hash, X):
    current = hash(X)
    for sibling in merkle_proof:
        if sibling["position"] == "LEFT":
            current = hash(sibling["hashed_data"] + current)
        else:
            current = hash(current + sibling["hashed_data"])

    return root_hash == current
```
