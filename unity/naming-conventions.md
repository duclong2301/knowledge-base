# Unity Naming Conventions

> Quy ước đặt tên toàn diện cho Unity Project

## Mục Lục

1. [Nguyên Tắc Chung](#nguyên-tắc-chung)
2. [Scripts (C# Files)](#scripts-c-files)
3. [Prefabs](#prefabs)
4. [Textures & Materials](#textures--materials)
5. [Sprites & Sprite Sheets](#sprites--sprite-sheets)
6. [Materials](#materials)
7. [3D Models](#3d-models)
8. [Audio Files](#audio-files)
9. [Animation Files](#animation-files)
10. [Scenes](#scenes)
11. [Shader Files](#shader-files)
12. [ScriptableObjects](#scriptableobjects)
13. [Particle Systems](#particle-systems)
14. [Bảng Tổng Hợp Convention](#bảng-tổng-hợp-convention)
15. [Cấu Trúc Thư Mục Mẫu](#cấu-trúc-thư-mục-mẫu)
16. [Version Control Naming](#version-control-naming)
17. [Platform-Specific Suffixes](#platform-specific-suffixes)
18. [Quality/Size Variants](#qualitysize-variants)
19. [Special Cases](#special-cases)
20. [Checklist - Quy Tắc Vàng](#checklist---quy-tắc-vàng)

---

## Nguyên Tắc Chung

### Quy Tắc Cơ Bản

| Quy Tắc | Mô Tả | Ví Dụ |
|---------|-------|-------|
| **PascalCase** | Viết hoa chữ cái đầu mỗi từ, không có khoảng trắng | `PlayerController`, `GameManager` |
| **camelCase** | Viết thường chữ cái đầu, viết hoa các từ tiếp theo | `playerHealth`, `currentScore` |
| **snake_case** | Viết thường, ngăn cách bằng dấu gạch dưới | `player_idle`, `enemy_attack` |
| **SCREAMING_SNAKE_CASE** | Viết hoa tất cả, ngăn cách bằng dấu gạch dưới | `MAX_HEALTH`, `PLAYER_SPEED` |

### Nguyên Tắc Đặt Tên

1. **Rõ ràng và mô tả** - Tên phải thể hiện rõ mục đích
2. **Nhất quán** - Tuân thủ convention trong toàn bộ project
3. **Tránh viết tắt** - Trừ khi là viết tắt phổ biến (UI, AI, HP, MP)
4. **Sử dụng tiếng Anh** - Đảm bảo tính tương thích và chuyên nghiệp
5. **Prefix/Suffix có ý nghĩa** - Giúp nhóm và tìm kiếm asset dễ dàng

---

## Scripts (C# Files)

### MonoBehaviour Scripts

| Loại | Convention | Ví Dụ |
|------|------------|-------|
| Controllers | `[Object]Controller.cs` | `PlayerController.cs`, `CameraController.cs` |
| Managers | `[System]Manager.cs` | `GameManager.cs`, `AudioManager.cs` |
| Handlers | `[Action]Handler.cs` | `InputHandler.cs`, `CollisionHandler.cs` |
| Systems | `[Feature]System.cs` | `InventorySystem.cs`, `QuestSystem.cs` |

### Non-MonoBehaviour Scripts

| Loại | Convention | Ví Dụ |
|------|------------|-------|
| Interfaces | `I[Name].cs` | `IInteractable.cs`, `IDamageable.cs` |
| Abstract Classes | `Base[Name].cs` hoặc `[Name]Base.cs` | `BaseEnemy.cs`, `WeaponBase.cs` |
| Enums | `[Name]Type.cs` hoặc `[Name]State.cs` | `WeaponType.cs`, `GameState.cs` |
| Static Classes | `[Name]Utility.cs` hoặc `[Name]Helper.cs` | `MathUtility.cs`, `StringHelper.cs` |
| Data Classes | `[Name]Data.cs` | `PlayerData.cs`, `LevelData.cs` |

### Ví Dụ Code

```csharp
// ✅ GOOD
public class PlayerController : MonoBehaviour
{
    private int currentHealth;
    private const int MAX_HEALTH = 100;
    
    public void TakeDamage(int damage) { }
}

// ❌ BAD
public class player : MonoBehaviour
{
    private int hp;
    private const int maxhp = 100;
    
    public void takedmg(int dmg) { }
}
```

---

## Prefabs

### Theo Category

| Category | Prefix | Ví Dụ |
|----------|--------|-------|
| Characters | `CHAR_` | `CHAR_Player`, `CHAR_Enemy_Zombie` |
| Props | `PROP_` | `PROP_Chair`, `PROP_Table` |
| UI Elements | `UI_` | `UI_Button_Start`, `UI_Panel_Inventory` |
| Environment | `ENV_` | `ENV_Tree_Oak`, `ENV_Rock_Large` |
| Effects | `FX_` | `FX_Explosion`, `FX_Smoke` |
| Pickups | `PICKUP_` | `PICKUP_HealthPotion`, `PICKUP_Coin` |
| Weapons | `WPN_` | `WPN_Sword_Iron`, `WPN_Gun_Pistol` |

### Variant Naming

```
Base_Prefab_Variant
├── CHAR_Enemy_Base
├── CHAR_Enemy_Fast
├── CHAR_Enemy_Tank
└── CHAR_Enemy_Boss
```

### Folder Structure

```
Prefabs/
├── Characters/
│   ├── Player/
│   └── Enemies/
├── Environment/
│   ├── Nature/
│   └── Urban/
├── UI/
│   ├── Buttons/
│   └── Panels/
└── FX/
```

---

## Textures & Materials

### Texture Types

| Texture Type | Suffix | Ví Dụ |
|--------------|--------|-------|
| Diffuse/Albedo | `_D` hoặc `_Albedo` | `Wood_D`, `Metal_Albedo` |
| Normal Map | `_N` | `Brick_N` |
| Height/Bump | `_H` | `Stone_H` |
| Roughness | `_R` | `Metal_R` |
| Metallic | `_M` | `Steel_M` |
| Ambient Occlusion | `_AO` | `Concrete_AO` |
| Emissive | `_E` | `Lamp_E` |
| Opacity/Alpha | `_A` | `Glass_A` |
| Specular | `_S` | `Plastic_S` |

### Resolution Suffix

| Resolution | Suffix | Ví Dụ |
|------------|--------|-------|
| 4K | `_4K` | `Terrain_D_4K` |
| 2K | `_2K` | `Wood_N_2K` |
| 1K | `_1K` | `Metal_D_1K` |
| 512 | `_512` | `Icon_D_512` |

### Complete Example

```
T_Character_Hero_D_2K.png
T_Character_Hero_N_2K.png
T_Character_Hero_R_2K.png
M_Character_Hero.mat
```

---

## Sprites & Sprite Sheets

### Single Sprites

| Category | Prefix | Ví Dụ |
|----------|--------|-------|
| UI Icons | `ICO_` | `ICO_Health`, `ICO_Mana` |
| Characters | `SPR_` | `SPR_Player_Idle`, `SPR_Enemy_Walk` |
| Items | `ITEM_` | `ITEM_Sword`, `ITEM_Potion` |
| Backgrounds | `BG_` | `BG_Forest`, `BG_Cave` |

### Animation Frames

```
SPR_Character_Action_FrameNumber
├── SPR_Player_Idle_00
├── SPR_Player_Idle_01
├── SPR_Player_Idle_02
└── SPR_Player_Idle_03

SPR_Enemy_Walk_00
SPR_Enemy_Walk_01
SPR_Enemy_Attack_00
SPR_Enemy_Attack_01
```

### Sprite Atlas

```
ATLAS_Characters_Heroes
ATLAS_UI_Icons
ATLAS_Environment_Props
```

---

## Materials

### 3D Materials

| Type | Prefix | Ví Dụ |
|------|--------|-------|
| Standard Material | `M_` | `M_Wood_Oak`, `M_Metal_Steel` |
| Transparent | `M_` + suffix `_Trans` | `M_Glass_Trans` |
| Emissive | `M_` + suffix `_Emit` | `M_Lava_Emit` |

### UI Materials

| Type | Prefix | Ví Dụ |
|------|--------|-------|
| UI Material | `M_UI_` | `M_UI_Button`, `M_UI_Panel` |

---

## 3D Models

### Model Naming

| Type | Prefix | Ví Dụ |
|------|--------|-------|
| Static Mesh | `SM_` | `SM_Chair`, `SM_Building` |
| Skeletal Mesh | `SK_` | `SK_Character_Hero` |
| Collision Mesh | `UCX_` | `UCX_Chair`, `UCX_Building` |

### LOD Naming

```
SM_Building_LOD0  // Highest detail
SM_Building_LOD1  // Medium detail
SM_Building_LOD2  // Low detail
SM_Building_LOD3  // Lowest detail
```

### Parts/Modular

```
SM_Modular_Wall_Straight
SM_Modular_Wall_Corner
SM_Modular_Floor_Square
SM_Modular_Ceiling_Panel
```

---

## Audio Files

### Audio Categories

| Category | Prefix | Ví Dụ |
|----------|--------|-------|
| Music | `MUS_` | `MUS_MainTheme`, `MUS_BattleLoop` |
| Sound Effects | `SFX_` | `SFX_Explosion`, `SFX_Footstep` |
| Voice/Dialog | `VO_` | `VO_Player_Hurt`, `VO_NPC_Greeting` |
| Ambience | `AMB_` | `AMB_Forest`, `AMB_City` |
| UI Sounds | `UI_SFX_` | `UI_SFX_Click`, `UI_SFX_Hover` |

### Variations

```
SFX_Footstep_Grass_01
SFX_Footstep_Grass_02
SFX_Footstep_Wood_01
SFX_Explosion_Small
SFX_Explosion_Large
```

### Audio Folder Structure

```
Audio/
├── Music/
│   ├── MainMenu/
│   ├── Gameplay/
│   └── Boss/
├── SFX/
│   ├── Weapons/
│   ├── Characters/
│   └── Environment/
├── Voice/
└── Ambience/
```

---

## Animation Files

### Animation Clips

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Character Animations | `ANIM_[Character]_[Action]` | `ANIM_Player_Idle`, `ANIM_Player_Run` |
| Looping | Suffix `_Loop` | `ANIM_Enemy_Walk_Loop` |
| One-shot | No suffix | `ANIM_Player_Jump` |

### Animation Controllers

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Animator Controller | `AC_[Character]` | `AC_Player`, `AC_Enemy_Zombie` |
| Override Controller | `AC_[Character]_Override` | `AC_Enemy_Fast_Override` |

### State Names

```csharp
// Animation states trong Animator
Idle
Walk
Run
Jump
Attack
Death
```

---

## Scenes

### Scene Naming

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Main Scenes | `[Name]` | `MainMenu`, `Gameplay`, `Settings` |
| Levels | `Level_[Number]_[Name]` | `Level_01_Forest`, `Level_02_Cave` |
| Test Scenes | `TEST_[Feature]` | `TEST_Combat`, `TEST_AI` |
| Prototype | `PROTO_[Feature]` | `PROTO_Movement` |

### Build Index Order

```
0. Bootloader
1. MainMenu
2. Level_01_Tutorial
3. Level_02_Forest
4. Level_03_Boss
```

---

## Shader Files

### Shader Naming

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Shader | `SH_[Name]` | `SH_Toon`, `SH_Water` |
| Shader Graph | `SG_[Name]` | `SG_Dissolve`, `SG_Hologram` |
| Compute Shader | `CS_[Name]` | `CS_ParticleSimulation` |

### Examples

```
SH_Toon_Character
SH_Water_Realistic
SG_Dissolve_Effect
CS_FluidSimulation
```

---

## ScriptableObjects

### ScriptableObject Naming

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Data | `SO_[Type]Data` | `SO_WeaponData`, `SO_EnemyData` |
| Config | `SO_[System]Config` | `SO_GameConfig`, `SO_AudioConfig` |
| Database | `SO_[Type]Database` | `SO_ItemDatabase` |

### Examples

```csharp
// Script file
WeaponData.cs

// ScriptableObject instances
SO_Weapon_Sword_Iron
SO_Weapon_Sword_Steel
SO_Weapon_Bow_Wooden
```

---

## Particle Systems

### Effect Naming

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Effects | `FX_[Type]_[Name]` | `FX_Explosion_Small`, `FX_Magic_Fire` |
| Trails | `FX_Trail_[Name]` | `FX_Trail_Sword`, `FX_Trail_Bullet` |
| Ambient | `FX_Ambient_[Name]` | `FX_Ambient_Dust`, `FX_Ambient_Rain` |

### Effect Categories

```
FX_Explosion_Small
FX_Explosion_Medium
FX_Explosion_Large

FX_Magic_Fire
FX_Magic_Ice
FX_Magic_Lightning

FX_Hit_Spark
FX_Hit_Blood
FX_Hit_Dust
```

---

## Bảng Tổng Hợp Convention

### Quick Reference Table

| Asset Type | Prefix/Suffix | Example |
|------------|---------------|---------|
| **Scripts** |
| MonoBehaviour | `[Name]Controller/Manager` | `PlayerController.cs` |
| Interface | `I[Name]` | `IInteractable.cs` |
| **Prefabs** |
| Character | `CHAR_` | `CHAR_Player` |
| UI | `UI_` | `UI_Button_Start` |
| Props | `PROP_` | `PROP_Chair` |
| **Textures** |
| Diffuse | `_D` or `_Albedo` | `Wood_D` |
| Normal | `_N` | `Brick_N` |
| **Audio** |
| Music | `MUS_` | `MUS_MainTheme` |
| SFX | `SFX_` | `SFX_Explosion` |
| **3D Models** |
| Static Mesh | `SM_` | `SM_Building` |
| Skeletal | `SK_` | `SK_Character` |
| **Animations** |
| Animation | `ANIM_` | `ANIM_Player_Run` |
| Controller | `AC_` | `AC_Player` |
| **Materials** |
| Material | `M_` | `M_Wood_Oak` |
| **Scenes** |
| Level | `Level_[##]_[Name]` | `Level_01_Forest` |
| **Shaders** |
| Shader | `SH_` | `SH_Toon` |
| **ScriptableObjects** |
| Data | `SO_[Type]Data` | `SO_WeaponData` |

---

## Cấu Trúc Thư Mục Mẫu

### Complete Project Structure

```
Assets/
├── _Project/
│   ├── Animations/
│   │   ├── Characters/
│   │   │   ├── Player/
│   │   │   │   ├── AC_Player.controller
│   │   │   │   ├── ANIM_Player_Idle.anim
│   │   │   │   ├── ANIM_Player_Walk.anim
│   │   │   │   └── ANIM_Player_Run.anim
│   │   │   └── Enemies/
│   │   └── UI/
│   │
│   ├── Audio/
│   │   ├── Music/
│   │   │   ├── MUS_MainTheme.mp3
│   │   │   └── MUS_BattleLoop.mp3
│   │   ├── SFX/
│   │   │   ├── Weapons/
│   │   │   │   ├── SFX_Sword_Swing.wav
│   │   │   │   └── SFX_Gun_Shot.wav
│   │   │   └── Characters/
│   │   │       ├── SFX_Footstep_Grass_01.wav
│   │   │       └── SFX_Jump.wav
│   │   └── Voice/
│   │
│   ├── Materials/
│   │   ├── Characters/
│   │   │   └── M_Player.mat
│   │   ├── Environment/
│   │   │   ├── M_Wood_Oak.mat
│   │   │   └── M_Stone_Grey.mat
│   │   └── UI/
│   │
│   ├── Models/
│   │   ├── Characters/
│   │   │   ├── SK_Player.fbx
│   │   │   └── SK_Enemy_Zombie.fbx
│   │   ├── Props/
│   │   │   ├── SM_Chair.fbx
│   │   │   └── SM_Table.fbx
│   │   └── Environment/
│   │       ├── SM_Tree_Oak.fbx
│   │       └── SM_Rock_Large.fbx
│   │
│   ├── Prefabs/
│   │   ├── Characters/
│   │   │   ├── CHAR_Player.prefab
│   │   │   └── CHAR_Enemy_Zombie.prefab
│   │   ├── Environment/
│   │   │   ├── ENV_Tree_Oak.prefab
│   │   │   └── ENV_Rock_Large.prefab
│   │   ├── UI/
│   │   │   ├── UI_Button_Start.prefab
│   │   │   └── UI_Panel_Inventory.prefab
│   │   └── FX/
│   │       ├── FX_Explosion_Small.prefab
│   │       └── FX_Magic_Fire.prefab
│   │
│   ├── ScriptableObjects/
│   │   ├── Items/
│   │   │   ├── SO_Item_HealthPotion.asset
│   │   │   └── SO_Item_Sword_Iron.asset
│   │   ├── Enemies/
│   │   │   └── SO_Enemy_Zombie.asset
│   │   └── Config/
│   │       └── SO_GameConfig.asset
│   │
│   ├── Scripts/
│   │   ├── Characters/
│   │   │   ├── PlayerController.cs
│   │   │   └── EnemyController.cs
│   │   ├── Managers/
│   │   │   ├── GameManager.cs
│   │   │   ├── AudioManager.cs
│   │   │   └── UIManager.cs
│   │   ├── Systems/
│   │   │   ├── InventorySystem.cs
│   │   │   └── QuestSystem.cs
│   │   ├── Interfaces/
│   │   │   ├── IInteractable.cs
│   │   │   └── IDamageable.cs
│   │   └── Utilities/
│   │       ├── MathUtility.cs
│   │       └── StringHelper.cs
│   │
│   ├── Scenes/
│   │   ├── Bootloader.unity
│   │   ├── MainMenu.unity
│   │   ├── Level_01_Tutorial.unity
│   │   ├── Level_02_Forest.unity
│   │   └── TEST_Combat.unity
│   │
│   ├── Shaders/
│   │   ├── SH_Toon_Character.shader
│   │   ├── SG_Dissolve_Effect.shadergraph
│   │   └── CS_ParticleSimulation.compute
│   │
│   ├── Sprites/
│   │   ├── Characters/
│   │   │   ├── SPR_Player_Idle_00.png
│   │   │   ├── SPR_Player_Walk_00.png
│   │   │   └── ATLAS_Characters.spriteatlas
│   │   ├── UI/
│   │   │   ├── ICO_Health.png
│   │   │   ├── ICO_Mana.png
│   │   │   └── ATLAS_UI_Icons.spriteatlas
│   │   └── Items/
│   │
│   └── Textures/
│       ├── Characters/
│       │   ├── T_Player_D_2K.png
│       │   ├── T_Player_N_2K.png
│       │   └── T_Player_R_2K.png
│       ├── Environment/
│       │   ├── T_Wood_Oak_D_2K.png
│       │   ├── T_Wood_Oak_N_2K.png
│       │   └── T_Stone_Grey_D_1K.png
│       └── UI/
│
├── Plugins/
└── ThirdParty/
```

---

## Version Control Naming

### Git Branch Naming

| Type | Convention | Ví Dụ |
|------|------------|-------|
| Feature | `feature/[name]` | `feature/inventory-system` |
| Bugfix | `bugfix/[name]` | `bugfix/player-jump` |
| Hotfix | `hotfix/[name]` | `hotfix/critical-crash` |
| Release | `release/[version]` | `release/1.0.0` |
| Experimental | `experimental/[name]` | `experimental/ai-behavior` |

### Commit Messages

```
feat: Add inventory system
fix: Fix player jump bug
docs: Update naming conventions
refactor: Reorganize folder structure
test: Add unit tests for combat system
```

### Tag Naming

```
v1.0.0          // Release version
v1.0.0-alpha    // Alpha version
v1.0.0-beta.1   // Beta version
v1.0.0-rc.1     // Release candidate
```

---

## Platform-Specific Suffixes

### Platform Identifiers

| Platform | Suffix | Ví Dụ |
|----------|--------|-------|
| PC/Windows | `_PC` | `M_Character_PC`, `T_UI_Button_PC` |
| Mobile | `_Mobile` | `M_Character_Mobile` |
| Console (General) | `_Console` | `CHAR_Player_Console` |
| PlayStation | `_PS` | `T_Icon_PS` |
| Xbox | `_Xbox` | `T_Icon_Xbox` |
| Nintendo Switch | `_Switch` | `T_Icon_Switch` |
| VR | `_VR` | `CHAR_Player_VR` |
| WebGL | `_WebGL` | `Scene_WebGL` |

### Examples

```
// Different quality for different platforms
M_Character_Hero_PC.mat
M_Character_Hero_Mobile.mat

// Platform-specific prefabs
CHAR_Player_PC.prefab
CHAR_Player_Mobile.prefab
CHAR_Player_VR.prefab

// UI variations
UI_Button_Touch_Mobile.prefab
UI_Button_Keyboard_PC.prefab
```

---

## Quality/Size Variants

### Quality Levels

| Quality | Suffix | Use Case |
|---------|--------|----------|
| High Quality | `_HQ` | PC, Consoles |
| Medium Quality | `_MQ` | Mid-range devices |
| Low Quality | `_LQ` | Mobile, low-end |

### Size Variants

| Size | Suffix | Use Case |
|------|--------|----------|
| Large | `_L` | Main characters, important objects |
| Medium | `_M` | Secondary objects |
| Small | `_S` | Background, minor details |

### Examples

```
// Quality variants
T_Environment_Tree_D_HQ_4K.png
T_Environment_Tree_D_MQ_2K.png
T_Environment_Tree_D_LQ_512.png

// Size variants
PROP_Rock_L.prefab
PROP_Rock_M.prefab
PROP_Rock_S.prefab

// Combined
SM_Building_House_HQ_LOD0
SM_Building_House_LQ_LOD2
```

---

## Special Cases

### Temporary Files

| Type | Prefix | Ví Dụ |
|------|--------|-------|
| Temporary | `TEMP_` | `TEMP_TestScript.cs` |
| Work in Progress | `WIP_` | `WIP_NewFeature.cs` |
| Backup | `BACKUP_` | `BACKUP_OldScript.cs` |

### Deprecated Files

```
DEPRECATED_OldSystem.cs
LEGACY_OldController.cs
OLD_PreviousVersion.prefab
```

### Reference Files

```
REF_CharacterConcept.png
REF_LevelLayout.png
GUIDE_FolderStructure.txt
```

### Testing Assets

```
TEST_PlayerController.cs
TEST_Scene.unity
DEBUG_ShowColliders.cs
```

---

## Checklist - Quy Tắc Vàng

### ✅ Before Committing

- [ ] Tất cả file đều tuân theo naming convention
- [ ] Không có tên chứa khoảng trắng
- [ ] Không có ký tự đặc biệt (trừ `_` và `-`)
- [ ] Prefix/Suffix phù hợp với loại asset
- [ ] File được đặt trong thư mục đúng
- [ ] Không có file tạm hoặc backup trong commit

### ✅ Asset Organization

- [ ] Scripts được nhóm theo chức năng
- [ ] Prefabs có cấu trúc rõ ràng
- [ ] Textures được tổ chức theo object
- [ ] Materials liên kết đúng với textures
- [ ] Audio files được phân loại rõ ràng

### ✅ Naming Best Practices

- [ ] Tên dễ đọc và dễ hiểu
- [ ] Tên mô tả đúng chức năng
- [ ] Sử dụng prefix cho dễ tìm kiếm
- [ ] Suffix thể hiện variant hoặc platform
- [ ] Version number khi cần thiết

### ✅ Documentation

- [ ] Script có summary comments
- [ ] Complex logic có inline comments
- [ ] README trong folder quan trọng
- [ ] Update changelog khi cần

### ✅ Performance Considerations

- [ ] Texture resolution phù hợp
- [ ] LOD được đặt tên đúng
- [ ] Quality variants cho platforms
- [ ] Compressed audio formats

---

## Tài Liệu Tham Khảo

### Style Guides
- [Unity Style Guide - Game Dev Guide](https://github.com/stillwwater/UnityStyleGuide)
- [Unreal Engine Naming Convention](https://docs.unrealengine.com/en-US/ProductionPipelines/AssetNaming/index.html)
- [Game Dev Best Practices](https://www.gamedeveloper.com/disciplines/unity-best-practices)

### Tools
- **Asset Renamer** - Batch rename assets
- **Folder Pro** - Better folder management
- **Project Cleaner** - Remove unused assets

---

**Last Updated**: January 2026  
**Version**: 1.0.0  
**Contributors**: DucLong

*This document is a living guide and will be updated as new conventions are established.*
