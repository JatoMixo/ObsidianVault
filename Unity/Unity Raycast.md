---
tags:
  - unity
  - raycast
---

### [Official Documentation](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)


The function returns a boolean telling if the ray hit something.
````cs
// Returns a boolean
Physics.Raycast(STARTING_POSITION, DIRECTION, out hit, LENGTH, LAYER_MASK);
````

#### Parameters:
 - **STARTING_POSITION:** Vector3 with the initial position of the raycast
 - **DIRECTION:** Vector3 for the direction of the ray
 - **LENGTH:** Float with the length of the raycast
 - **LAYER MASK:** The only layer mask it will detect