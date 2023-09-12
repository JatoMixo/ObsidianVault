---
tags:
  - unity
  - unity-input
---

### [Official Documentation](https://docs.unity3d.com/ScriptReference/Input.GetAxis.html)

````cs
// Returns a int
Input.GetAxis(AXIS);
````

#### Parameters
 - **AXIS:** The axis taken as an input, the can be configured in **Edit > Project Settings > Input Manager**

The method returns an int telling which key is pressed from the axis specified or a 0 if none of them is pressed.