# GitHub Copilot Instructions: Unity C# Style Guide & Naming

This project uses a strict code style guide for consistency. Follow these guidelines when generating code:

## General Guidelines
- **Naming Conventions**: 
  - Classes/Methods: `PascalCase`
  - Private fields: `m_camelCase`
  - Constants: `k_UPPER_SNAKE_CASE`
  - Properties: `PascalCase`
  
- **Spacing**: Use single space after commas, before operators. Don't add spaces inside parentheses.
- **Formatting**: Allman style (opening braces on new line)
- **Max line width**: 120-140 characters

## Field Naming
```csharp
private int m_health;                          // private field with m_ prefix
private static int s_sharedCount;              // static with s_ prefix
private const int k_maxCount = 100;            // constant with k_ prefix

[SerializeField] private bool m_isPlayerDead;  // boolean prefix: is/has/can
```

## Class Organization Order
1. Using statements
2. Namespace
3. Fields
4. Properties
5. Events
6. MonoBehaviour methods (Awake, OnEnable, Start, OnDisable, OnDestroy, FixedUpdate, Update, LateUpdate)
7. Public methods
8. Private methods
9. Other classes

## MonoBehaviour Methods
- **Awake()**: Initialize references, cache GetComponent
- **OnEnable()**: Subscribe to events
- **Start()**: One-time setup depending on other components
- **OnDisable()**: Unsubscribe from events
- **FixedUpdate()**: Physics calculations
- **Update()**: Frame updates, input handling
- **LateUpdate()**: Camera follow, post-processing

## Method Naming
- Action methods: Verb-based (Jump, ApplyDamage, PlaySound)
- Setter methods: `Set` prefix (SetMovementInput)
- Modifier methods: `Change` prefix (ChangeHealth)
- Boolean methods: Is/Has/Can (IsPlayerAlive, CanJump)

## Comments & Events
- Comment **why**, not **what**
- Event names: Past tense (DoorOpened, not OnDoorOpen)
- Event raising methods: On prefix (OnDoorOpened)

## UI Toolkit (UXML/USS)
- Use **kebab-case** for UXML names/classes
- Use **BEM** pattern: `block-name__element-name--modifier-name`
- Centralize selectors as constants

## Interfaces
- Prefix with `I` and use PascalCase: `IDamageable`, `IAudioService`
- One responsibility per interface

## ScriptableObjects
- Suffix: `DataSO` (e.g., WeaponDataSO)
- Store in dedicated folder: `Assets/Data/`

## Unity 6+ Specific
- Prefer `Awaitable` over coroutines
- Use `UnityEngine.Pool.ObjectPool<T>` for object pooling
- Use newer Input System, not Input Manager
