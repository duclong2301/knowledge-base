# Code Style Guide for V09N Project

This repository follows a strict code style guide to ensure consistency and help AI agents (like GitHub Copilot) generate properly formatted code.

## Quick Reference

### Naming Conventions
| Type | Pattern | Example |
|------|---------|---------|
| Class | PascalCase | `PlayerController` |
| Method | PascalCase + Verb | `UpdateAnimation()`, `ApplyDamage()` |
| Private Field | `m_` + camelCase | `m_health`, `m_isActive` |
| Static Field | `s_` + camelCase | `s_instanceCount` |
| Constant | `k_` + UPPER_SNAKE_CASE | `k_MAX_HEALTH` |
| Property | PascalCase | `Health`, `IsGrounded` |
| Local Variable | camelCase | `speed`, `targetPosition` |

### File Organization in a C# Class
```csharp
namespace MyGame.Characters
{
    using System;
    using UnityEngine;
    
    public class Player : MonoBehaviour
    {
        // 1. Fields
        [SerializeField] private int m_health = 100;
        private float m_speed;
        private const float k_maxSpeed = 10f;
        
        // 2. Properties
        public int Health => m_health;
        
        // 3. Events
        public event Action<int> HealthChanged;
        
        // 4. MonoBehaviour Methods (Execution Order)
        private void Awake() { }
        private void OnEnable() { }
        private void Start() { }
        private void OnDisable() { }
        private void Update() { }
        private void LateUpdate() { }
        
        // 5. Public Methods
        public void TakeDamage(int amount) { }
        
        // 6. Private Methods
        private void UpdateHealth() { }
    }
}
```

### Spacing & Formatting
✅ **Do:**
```csharp
public void ProcessItems(List<Item> items, int startIndex)
{
    for (int i = startIndex; i < items.Count; i++)
    {
        ProcessItem(items[i]);
    }
}
```

❌ **Don't:**
```csharp
public void ProcessItems ( List<Item>items,int startIndex ) { for(int i=startIndex;i<items.Count;i++) { ProcessItem( items [ i ] ); } }
```

### Comments
- Comment the **why**, not the **what**
- Use `[Tooltip]` for serialized fields
- Use `Debug.Log(..., gameObject)` to pass context

### Events
```csharp
public event Action DoorOpened;  // Past tense
public event Action<int> PointsScored;

public void OnDoorOpened()  // On prefix for raising
{
    DoorOpened?.Invoke();  // Null-conditional operator
}
```

### MonoBehaviour Methods Order
1. **Awake()** - Cache GetComponent, initialize references
2. **OnEnable()** - Subscribe to events
3. **Start()** - One-time setup
4. **OnDisable()** - Unsubscribe from events
5. **OnDestroy()** - Cleanup
6. **FixedUpdate()** - Physics calculations
7. **Update()** - Frame updates, input
8. **LateUpdate()** - Camera follow, post-updates

## Copilot Integration

Copilot reads `.github/copilot-instructions.md` automatically. Include this file in your repo to guide AI code generation.

## UI Toolkit Guidelines

### UXML Naming (kebab-case)
```xml
<ui:VisualElement name="player-hud" class="player-hud">
    <ui:Button name="player-hud__pause-button" class="player-hud__pause-button button button--primary"/>
</ui:VisualElement>
```

### BEM Pattern
- **Block**: `navbar-menu`
- **Element**: `navbar-menu__item`
- **Modifier**: `navbar-menu__item--active`

### Centralizing Selectors
```csharp
public static class UiSelectors
{
    public const string PlayerHud = "player-hud";
    public const string PauseButton = "player-hud__pause-button";
}
```

## Further Reading

For complete details, see the [Unity Code Style Guide](https://github.com/krogh-jacobsen/unity-code-style-guide/blob/main/CodeStyleGuide.md)

---

**Questions?** Check the Copilot instructions at `.github/copilot-instructions.md`
