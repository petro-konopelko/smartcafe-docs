# Menu Grid UI - User Experience

This document describes the menu management interface for cafe owners.

---

## Menu Grid View

The main interface shows all menus in a grid/card layout:

```
┌─────────────────────────────────────────────────────────────────────┐
│  Menu Manager                                    [+ Create New Menu] │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────────────┐  ┌─────────────────────┐  ┌──────────────┐│
│  │ 🌞 Summer Menu 2025 │  │ ❄️  Winter Menu     │  │ 🎄 Holiday   ││
│  │ ✅ ACTIVE           │  │ 📝 PUBLISHED        │  │ 📝 DRAFT     ││
│  │                     │  │                     │  │              ││
│  │ 5 Sections          │  │ 4 Sections          │  │ 2 Sections   ││
│  │ 32 Items            │  │ 28 Items            │  │ 8 Items      ││
│  │                     │  │                     │  │              ││
│  │ Activated:          │  │ Published:          │  │ Created:     ││
│  │ May 15, 2025        │  │ Nov 1, 2025         │  │ Dec 5, 2025  ││
│  │                     │  │                     │  │              ││
│  │ [Edit] [Deactivate] │  │ [Edit] [Activate]   │  │ [Edit]       ││
│  │        [Clone]      │  │        [Clone]      │  │ [Publish]    ││
│  └─────────────────────┘  └─────────────────────┘  │ [Delete]     ││
│                                                     └──────────────┘│
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Menu States & Badges

### 1. **Draft** 📝
- Menu is being created or edited
- Not visible to customers
- Can be edited freely
- Can be deleted
- Can be published

### 2. **Published** 📚
- Menu is ready but not currently active
- Not visible to customers yet
- Can be activated
- Can be cloned
- Cannot be deleted

### 3. **Active** ✅
- Currently displayed to customers
- Only one menu can be active at a time
- Can be deactivated (must activate another menu first)
- Can be cloned
- Cannot be deleted

---

## User Workflows

### Workflow 1: Create New Seasonal Menu

```
1. User clicks [+ Create New Menu]
   ↓
2. Modal appears: "Create New Menu"
   - Name: [Winter Menu_____________]
   - [Create from scratch] or [Clone existing menu ▼]
   ↓
3. User clicks "Create from scratch"
   ↓
4. Editor page opens with empty menu
   ↓
5. User adds sections and items
   ↓
6. User clicks [Save Draft] (auto-saves every 30s)
   ↓
7. User clicks [Publish]
   ↓
8. Confirmation: "Publish Winter Menu?"
   - This will make it available for activation
   ↓
9. Menu card shows "📝 PUBLISHED" badge
```

### Workflow 2: Activate Seasonal Menu

```
1. User sees menu grid:
   - Summer Menu (ACTIVE)
   - Winter Menu (PUBLISHED)
   
2. November arrives, time to switch to winter menu
   ↓
3. User clicks [Activate] on "Winter Menu" card
   ↓
4. Confirmation modal:
   "Activate Winter Menu?"
   
   This will:
   ✓ Make "Winter Menu" active for customers
   ✓ Deactivate "Summer Menu"
   
   [Cancel] [Activate Menu]
   ↓
5. User clicks [Activate Menu]
   ↓
6. Menu grid updates:
   - Summer Menu (PUBLISHED) ← no longer active
   - Winter Menu (ACTIVE) ✅ ← now active
   ↓
7. Customers immediately see Winter Menu
```

### Workflow 3: Clone Menu for Next Season

```
1. User clicks [Clone] on "Summer Menu 2025"
   ↓
2. Modal appears: "Clone Menu"
   - New name: [Summer Menu 2026_____]
   - ☑ Include all sections and items
   - ☐ Include images
   ↓
3. User clicks [Clone Menu]
   ↓
4. New menu card appears:
   "Summer Menu 2026" (DRAFT)
   ↓
5. User clicks [Edit] to update for 2026 season
   ↓
6. User updates prices, items, images
   ↓
7. User clicks [Publish] when ready
```

### Workflow 4: Quick Price Update

```
1. User clicks [Edit] on active menu card
   ↓
2. Editor page opens (menu is still active, customers see it)
   ↓
3. User finds "Caesar Salad"
   ↓
4. User clicks on price: $12.00
   ↓
5. Inline edit: [$13.50_]
   ↓
6. User clicks outside or presses Enter
   ↓
7. Auto-save triggers
   ↓
8. Confirmation banner: "Menu updated. Changes are live."
   
Note: For active menus, changes go live immediately!
For draft/published menus, changes are saved but not visible.
```

---

## Menu Editor Page

When editing a menu:

```
┌─────────────────────────────────────────────────────────────────────┐
│ ← Back to Menu Grid                          [Save Draft] [Publish] │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  Menu Name: [Summer Menu 2025_________________]                     │
│  Status: ✅ ACTIVE (Activated on May 15, 2025)                      │
│                                                                      │
│  ┌─ 🌅 Breakfast (9:00 AM - 1:00 PM) ──────────────── [↑][↓][×]    │
│  │                                                                   │
│  │  ⋮⋮ Pancakes ────────────────────────────────── $8.50 [×] [✎]   │
│  │     Fluffy buttermilk pancakes                                   │
│  │     🥬 Vegetarian  [🖼️ Image]                                     │
│  │                                                                   │
│  │  ⋮⋮ French Toast ────────────────────────────── $9.00 [×] [✎]   │
│  │     Thick-cut brioche with berries                               │
│  │     🥬 Vegetarian  [🖼️ Image]                                     │
│  │                                                                   │
│  │  [+ Add Item to Breakfast]                                       │
│  └──────────────────────────────────────────────────────────────────│
│                                                                      │
│  ┌─ 🍽️ Lunch (11:00 AM - 4:00 PM) ────────────────── [↑][↓][×]     │
│  │  ...                                                              │
│  └──────────────────────────────────────────────────────────────────│
│                                                                      │
│  [+ Add Section]                                                    │
│                                                                      │
│  Last saved: 2 minutes ago                   [Discard] [Save Draft] │
└─────────────────────────────────────────────────────────────────────┘

Legend:
⋮⋮ = Drag handle (reorder items)
[↑][↓] = Move section up/down
[×] = Delete
[✎] = Edit inline
```

---

## Benefits of Grid View

### For Users:
✅ **Overview at a glance** - See all menus and their status  
✅ **Visual status** - Clear badges (Draft, Published, Active)  
✅ **Seasonal planning** - Prepare next season's menu in advance  
✅ **Quick switching** - Activate different menus with one click  
✅ **Safe experimentation** - Work on drafts without affecting active menu  
✅ **Easy cloning** - Copy successful menus for new seasons  

### For Business:
✅ **Seasonal flexibility** - Different menus for different times of year  
✅ **Event menus** - Special menus for holidays, events  
✅ **Menu testing** - Prepare and preview before going live  
✅ **Historical record** - See what was offered in past seasons  
✅ **Quick rollback** - Reactivate previous menu if needed  

---

## Example Scenarios

### Scenario: Italian Restaurant

**Menus:**
1. **"Regular Menu"** (ACTIVE) - Year-round classics
2. **"Summer Specials"** (PUBLISHED) - Light salads, cold dishes
3. **"Winter Warmers"** (PUBLISHED) - Hearty soups, pasta
4. **"Valentine's Day"** (DRAFT) - Special tasting menu

**Actions:**
- In June: Activate "Summer Specials"
- In November: Activate "Winter Warmers"
- In February: Publish and activate "Valentine's Day" for Feb 14-15
- After event: Reactivate "Winter Warmers"

### Scenario: Cafe with Day/Night Menus

**Menus:**
1. **"Breakfast & Lunch"** (ACTIVE 6am-5pm)
2. **"Dinner & Drinks"** (ACTIVE 5pm-10pm)

*Note: For time-based activation, use section availability hours within a single menu instead of multiple menus*

---

## References

- [Menu Service Overview](./menu.md)
- [Menu Service Architecture](../20-architecture/menu-service.md)
- [Business Domain Overview](./README.md)
