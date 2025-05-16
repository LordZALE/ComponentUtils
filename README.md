# Unity Component Utils

# Overview

### RequireComponentGetters
Create getters for each RequireComponent type on a MonoBehaviour. The MonoBehaviour class must be marked with `partial`.

Each getter will lazily cache component references.
```csharp
[RequireComponent(typeof(Rigidbody))]
[RequireComponentGetters]
public partial class MyBehaviour : MonoBehaviour
{
    // Generates:
    // private Rigidbody _rigidbody;
    // public Rigidbody Rigidbody => _rigidbody ??= GetComponent<Rigidbody>();
}
```
Getter visibility can also be specified (as a literal string):
```csharp
[RequireComponent(typeof(MeshFilter))]
[RequireComponentGetters("protected internal")]
public partial class MyBehaviour : MonoBehaviour
{
    // Generates:
    // private MeshFilter _meshFilter;
    // protected internal MeshFilter MeshFilter => _meshFilter ??= GetComponent<MeshFilter>();
}
```
