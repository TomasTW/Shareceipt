# Shareceipt Design System

Comprehensive design system for the Shareceipt application, extracted from Pencil design files. This documentation covers all 13 reusable components, design tokens, and usage guidelines.

## Table of Contents

1. [Design Tokens](#design-tokens)
2. [Components](#components)
3. [Usage Guidelines](#usage-guidelines)
4. [Examples](#examples)

## Design Tokens

### Colors

#### Primary Colors
- **Primary**: `#3000b0` - Main brand color (indigo/purple)
- **Primary Dark**: `#1d027a` - Darker shade for hover states
- **Primary Light**: `#eae6f7` - Lighter shade for backgrounds

#### Neutral Colors
- **White**: `#fffefd` - Main background
- **Light Grey**: `#f9f9fc` - Secondary background
- **Grey Light**: `#bccac0` - Borders and dividers
- **Grey**: `#666666` - Secondary text
- **Grey Dark**: `#2b2b2b` - Primary text
- **Black**: `#1a1a1a` - Dark text

CSS Variables: Use `var(--color-primary)`, `var(--color-grey)`, etc.

### Typography

#### Font Family
- **Primary Font**: Poppins
- **Fallback**: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif

#### Font Sizes
- **XS**: 12px (`--font-size-xs`)
- **SM**: 14px (`--font-size-sm`)
- **Base**: 16px (`--font-size-base`)
- **LG**: 20px (`--font-size-lg`)
- **XL**: 24px (`--font-size-xl`)
- **2XL**: 28px (`--font-size-2xl`)
- **3XL**: 32px (`--font-size-3xl`)

#### Font Weights
- **Normal**: 400 (`--font-weight-normal`)
- **Medium**: 500 (`--font-weight-medium`)
- **Semibold**: 600 (`--font-weight-semibold`)
- **Bold**: 700 (`--font-weight-bold`)
- **Extrabold**: 800 (`--font-weight-extrabold`)

#### Line Heights
- **Tight**: 1.2 (`--line-height-tight`) - For headings
- **Normal**: 1.4 (`--line-height-normal`) - For body text
- **Relaxed**: 1.5 (`--line-height-relaxed`) - For descriptions

### Spacing

Consistent 4px base unit scaling:
- **XS**: 4px (`--spacing-xs`)
- **SM**: 8px (`--spacing-sm`)
- **MD**: 12px (`--spacing-md`)
- **LG**: 16px (`--spacing-lg`)
- **XL**: 24px (`--spacing-xl`)
- **2XL**: 32px (`--spacing-2xl`)

### Border Radius

- **XS**: 4px (`--radius-xs`)
- **SM**: 8px (`--radius-sm`)
- **MD**: 12px (`--radius-md`)
- **LG**: 16px (`--radius-lg`)
- **Full**: 9999px (`--radius-full`)

### Shadows

- **Small**: `var(--shadow-sm)` - Subtle elevation
- **Medium**: `var(--shadow-md)` - Standard elevation
- **Large**: `var(--shadow-lg)` - Prominent elevation
- **Extra Large**: `var(--shadow-xl)` - Maximum elevation (used on cards)

### Transitions

- **Fast**: 150ms (`--transition-fast`) - Hover states
- **Normal**: 250ms (`--transition-normal`) - Standard animations
- **Slow**: 350ms (`--transition-slow`) - Important transitions

## Components

### 1. Card Component

**Class**: `component-card`

**Purpose**: Container for content sections (friends list, shares, etc.)

**Features**:
- White background with subtle border
- Extra large shadow for elevation
- 16px padding
- Blue header section with white text
- 16px border radius

**Structure**:
```html
<div class="component-card">
  <div class="component-card__header">Section Title</div>
  <div class="component-card__content">
    <!-- Content goes here -->
  </div>
</div>
```

**Props/Variants**: None (static component)

---

### 2. Header Component

**Class**: `component-header`

**Purpose**: Page or section headers with title and subtitle

**Features**:
- Title (28px, bold)
- Optional subtitle (14px, grey)
- Vertical spacing of 12px between elements

**Structure**:
```html
<div class="component-header">
  <h1 class="component-header__title">Split the Bill</h1>
  <p class="component-header__subtitle">Manage your expenses and shares</p>
</div>
```

**Props**:
- `title` (required): Main heading text
- `subtitle` (optional): Description text

---

### 3. Avatar Component

**Class**: `component-avatar`

**Purpose**: Display user initials in circular badges

**Features**:
- Circular with full border radius
- Primary blue background
- White text
- Multiple size options

**Structure**:
```html
<div class="component-avatar">AB</div>
<div class="component-avatar component-avatar--sm">CD</div>
<div class="component-avatar component-avatar--lg">EF</div>
```

**Size Variants**:
- **Default**: 48px
- **Small** (`--sm`): 36px
- **Large** (`--lg`): 64px

---

### 4. Receipt Row Component

**Class**: `component-receipt-row`

**Purpose**: Display item-price pairs in bills/receipts

**Features**:
- Horizontal flex layout
- Left-aligned label
- Right-aligned value
- Primary blue price text
- Optional divider line

**Structure**:
```html
<div class="component-receipt-row">
  <span class="component-receipt-row__label">Subtotal</span>
  <span class="component-receipt-row__value">$45.00</span>
</div>
<div class="component-receipt-row__divider"></div>
```

**Props**:
- `label`: Item name (e.g., "Subtotal", "Tax")
- `value`: Amount (e.g., "$45.00")

---

### 5. Button / Primary / Default

**Class**: `component-button component-button--primary`

**Purpose**: Main action button

**Features**:
- Blue primary background
- White text
- 16px padding
- Hover state with darker blue
- Disabled state with grey styling

**Structure**:
```html
<button class="component-button component-button--primary">
  <i class="fa-solid fa-plus"></i>
  Add Item
</button>
```

---

### 6. Button / Primary / Hover

**State**: Applied automatically on hover

**Features**:
- Darker blue background
- Added shadow elevation
- Smooth transition (150ms)

---

### 7. Button / Primary / Disabled

**Modifier**: `:disabled` pseudo-class or `[disabled]` attribute

**Features**:
- Grey background
- Reduced opacity
- Cursor: not-allowed
- No hover effects

---

### 8. Button / Secondary / Default

**Class**: `component-button component-button--secondary`

**Purpose**: Secondary or cancel actions

**Features**:
- White background with grey border
- Grey text
- 16px padding
- Hover state with darker grey

**Structure**:
```html
<button class="component-button component-button--secondary">
  <i class="fa-solid fa-times"></i>
  Cancel
</button>
```

---

### 9. Button / Secondary / Hover

**State**: Applied automatically on hover

**Features**:
- Light grey background
- Darker grey border and text
- Smooth transition

---

### 10. Button / Secondary / Disabled

**State**: `:disabled` pseudo-class

**Features**:
- Light grey background
- Light grey border
- Reduced opacity
- No hover effects

---

### 11. Input / Default

**Class**: `component-input component-input--default`

**Purpose**: Text input field for data entry

**Features**:
- Light grey border
- White background
- Icon support (left-aligned)
- 12px padding
- Poppins font, 16px base size

**Structure**:
```html
<div class="component-input component-input--default">
  <div class="component-input__icon">
    <i class="fa-solid fa-key"></i>
  </div>
  <input class="component-input__field" placeholder="Enter your API key">
</div>
```

---

### 12. Input / Focused

**Class**: `component-input component-input--focused`

**Purpose**: Input field in active/focused state

**Features**:
- Primary blue border
- Blue focus ring (3px light blue shadow)
- Indicates user interaction

---

### 13. Input / Disabled

**Class**: `component-input component-input--disabled`

**Purpose**: Disabled input field

**Features**:
- Light grey background
- Light grey border
- Reduced opacity (60%)
- Cursor: not-allowed
- No interaction possible

---

## Usage Guidelines

### Layout Utilities

Use provided layout classes for consistent spacing:

```html
<!-- Horizontal layout with 16px gap -->
<div class="layout-flex-row">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

<!-- Vertical layout with 16px gap -->
<div class="layout-flex-col">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```

### Color Usage

Always use CSS variables:
```css
color: var(--color-primary);
background-color: var(--color-white);
border-color: var(--color-grey-light);
```

### Typography Usage

Use semantic text classes:
```html
<h1 class="text-heading-1">Main Title</h1>
<h2 class="text-heading-2">Section Title</h2>
<p class="text-body">Body text with regular weight</p>
<span class="text-small">Small caption text</span>
```

### Spacing Guidelines

- **8-16px**: Gap between elements within a container
- **16-24px**: Gap between sections
- **24-32px**: Gap between major sections

### Responsive Behavior

- Mobile-first approach
- Default styles are mobile optimized (max-width: 640px breakpoint)
- Larger screens use standard spacing and sizing

## Examples

### Example 1: Receipt Card

```html
<div class="component-card">
  <div class="component-card__header">Shares</div>
  <div class="component-card__content">
    <div class="component-receipt-row">
      <span class="component-receipt-row__label">Subtotal</span>
      <span class="component-receipt-row__value">$45.00</span>
    </div>
    <div class="component-receipt-row__divider"></div>
    <div class="component-receipt-row">
      <span class="component-receipt-row__label">Tax</span>
      <span class="component-receipt-row__value">$3.60</span>
    </div>
    <div class="component-receipt-row__divider"></div>
    <div class="component-receipt-row">
      <span class="component-receipt-row__label">Total</span>
      <span class="component-receipt-row__value">$48.60</span>
    </div>
  </div>
</div>
```

### Example 2: Form Section

```html
<div class="component-header">
  <h1 class="component-header__title">Enter Details</h1>
  <p class="component-header__subtitle">Add your information</p>
</div>

<div class="layout-flex-col">
  <div class="component-input component-input--default">
    <div class="component-input__icon">
      <i class="fa-solid fa-user"></i>
    </div>
    <input class="component-input__field" placeholder="Your name">
  </div>

  <div class="component-input component-input--default">
    <div class="component-input__icon">
      <i class="fa-solid fa-envelope"></i>
    </div>
    <input class="component-input__field" placeholder="Email address">
  </div>

  <button class="component-button component-button--primary">
    <i class="fa-solid fa-save"></i>
    Save
  </button>
</div>
```

### Example 3: Friends List

```html
<div class="component-card">
  <div class="component-card__header">Friends</div>
  <div class="component-card__content">
    <div class="layout-flex-row">
      <div class="component-avatar">AB</div>
      <div style="flex: 1;">
        <p style="margin: 0; font-weight: 600;">Alice Brown</p>
        <p style="margin: 0; color: var(--color-grey); font-size: 12px;">alice@example.com</p>
      </div>
    </div>
  </div>
</div>
```

## Import Instructions

### In HTML:
```html
<link rel="stylesheet" href="design-tokens.css">
<link rel="stylesheet" href="design-components.css">
<link rel="stylesheet" href="styles.css">
```

### In CSS:
```css
@import url('design-tokens.css');
@import url('design-components.css');
```

## Maintenance

When updating the design system:
1. Update the corresponding variable in `design-tokens.css`
2. Update component styles in `design-components.css`
3. Update this documentation file with new component descriptions
4. Test all component variants in the application

## Version History

- **v1.0.0** (2026-05-21) - Initial design system release
  - 13 core components
  - Complete design token library
  - Full documentation
