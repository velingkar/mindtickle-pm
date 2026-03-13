# Lo-Fi Prototype Design System

Apply these tokens to every prototype. This creates a consistent hand-drawn sketch aesthetic across all screens.

---

## Color Tokens

```
Background:        #f5f0e8   (warm off-white, like paper)
Surface / cards:   #fdfaf4
Text primary:      #1a1a1a
Text secondary:    #555
Text light:        #888
Accent:            #2a2aaa   (links, active states, focus rings)
Accent background: #e8e8f8
Annotation:        #fffbe6   (sticky-note yellow)
```

## Border Tokens

```
Border strong:     2px solid #1a1a1a   (default — hand-drawn feel)
Border light:      1.5px solid #555
Border dashed:     2px dashed #aaa     (placeholder regions, optional areas)
Border radius:     3px                 (nearly square — no rounded cards)
```

## Shadow Tokens

```
Shadow default:    3px 3px 0 #1a1a1a   (offset, not blurred — sketch feel)
Shadow small:      2px 2px 0 #1a1a1a
```

Use shadows on cards, modals, dropdowns, and buttons — never `box-shadow: blur`.

## Typography

```
Font family:    system-ui, 'Segoe UI', sans-serif
Heading 1:      22–24px, font-weight 700
Heading 2:      18px, font-weight 600
Body:           14–15px, font-weight 400
Label / meta:   12–13px, color: #555
```

---

## Component Patterns

### Buttons

Three variants — all have offset box-shadow:

```
Primary:    background #1a1a1a, color white, border 2px solid #1a1a1a, shadow 2px 2px 0 #555
Secondary:  background #fdfaf4, color #1a1a1a, border 2px solid #1a1a1a, shadow 2px 2px 0 #555
Accent:     background #e8e8f8, color #2a2aaa, border 2px solid #2a2aaa, shadow 2px 2px 0 #2a2aaa
Disabled:   any variant, opacity 0.4, cursor not-allowed
```

### Inputs and Form Fields

```
Background:      #fdfaf4
Border:          2px solid #1a1a1a
Border radius:   3px
Padding:         8px 12px
Focus:           border-color #2a2aaa, outline none
Placeholder:     color #888
```

### Sidebar

```
Collapsed (task/editor screens):  width 52px, icons only, tooltip on hover
Expanded (listing/overview):      width 200px, icons + labels
Active nav item:  accent border-left (3px solid #2a2aaa) + accent background (#e8e8f8)
```

### Cards

```
Background:    #fdfaf4
Border:        2px solid #1a1a1a
Border radius: 3px
Shadow:        3px 3px 0 #1a1a1a
Padding:       16px
```

### Modals / Overlays

```
Backdrop:       rgba(0,0,0,0.4), position fixed, full viewport
Modal panel:    background #fdfaf4, border 2px solid #1a1a1a, shadow 4px 4px 0 #1a1a1a
                max-width 560px, border-radius 3px
Header:         border-bottom 2px solid #1a1a1a, padding 16px 20px
Footer:         border-top 2px solid #1a1a1a, padding 12px 20px, flex row-reverse
```

### Tables

```
Header row:     background #f5f0e8, border-bottom 2px solid #1a1a1a, font-weight 600
Body rows:      border-bottom 1.5px solid #ccc
Hover row:      background #f0ede4
Checkbox col:   width 40px
```

### Tabs

```
Active tab:     border-bottom 3px solid #1a1a1a, font-weight 600
Inactive tab:   color #555, border-bottom 3px solid transparent
Tab bar:        border-bottom 2px solid #1a1a1a
```

---

## Placeholder Images and Thumbnails

Never use broken `<img>` tags. Use hatching + emoji instead:

```css
background: repeating-linear-gradient(
  45deg,
  transparent 0 3px,
  rgba(0,0,0,0.04) 3px 6px
);
border: 2px solid #1a1a1a;
display: flex;
align-items: center;
justify-content: center;
font-size: 2rem; /* emoji */
color: #888;
```

---

## Annotation Sticky Notes

Use sparingly — maximum 1–2 per screen. Label key design decisions, not obvious elements.

```css
background: #fffbe6;
border: 1.5px solid #1a1a1a;
box-shadow: 2px 2px 0 #1a1a1a;
padding: 6px 10px;
font-size: 12px;
color: #555;
transform: rotate(-1.5deg);  /* or +1.5deg for variety */
max-width: 160px;
```

Prefix annotation text with ✎.

---

## Interactive States

```
Hover (buttons, rows):   slight background shift — e.g. #f0ede4 on paper, #1a1a1a10 on white
Selected / active:       accent border + accent background (#e8e8f8)
Focus:                   border-color #2a2aaa
Disabled:                opacity 0.4, cursor not-allowed
Loading:                 animated dots or spinner using border-color trick, no external libs
```

---

## Spacing Scale

```
xs:    4px
sm:    8px
md:    12px
base:  16px
lg:    24px
xl:    32px
2xl:   48px
```

Use multiples of 4px throughout.
