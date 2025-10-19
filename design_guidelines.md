# Discord Webhook Bot - Design Guidelines

## Design Approach
**System**: Material Design 3 with Discord-inspired theming
**Rationale**: This utility-focused application requires clear information hierarchy, intuitive forms, and familiar interaction patterns. Material Design provides robust form components while Discord's visual language creates brand alignment and user trust.

## Core Design Elements

### A. Color Palette

**Dark Mode (Primary)**
- Background Base: 222 7% 11% (Discord's dark background)
- Surface Elevated: 223 7% 15% (cards, panels)
- Surface Highest: 225 6% 20% (input fields, elevated elements)
- Primary Brand: 235 86% 65% (Discord blurple - CTAs, active states)
- Primary Hover: 235 86% 70%
- Success: 139 47% 55% (Discord green - message sent confirmations)
- Error: 359 83% 62% (validation errors)
- Text Primary: 210 11% 96% (high contrast headings)
- Text Secondary: 215 9% 72% (body text, labels)
- Text Muted: 218 5% 47% (hints, placeholders)
- Border Subtle: 228 6% 25%

**Light Mode (Secondary - if needed)**
- Background: 0 0% 100%
- Surface: 214 32% 96%
- Text: 222 47% 11%

### B. Typography
**Font Families**: 
- Primary: 'Inter' (Google Fonts) - clean, modern sans-serif for UI
- Monospace: 'JetBrains Mono' - webhook URLs, technical displays

**Type Scale**:
- Hero/Page Title: text-3xl font-bold (30px)
- Section Headers: text-xl font-semibold (20px)
- Body/Labels: text-sm font-medium (14px)
- Helper Text: text-xs (12px)
- Button Text: text-sm font-medium uppercase tracking-wide

### C. Layout System
**Spacing Units**: Use Tailwind units of **4, 6, 8, 12, 16** for consistency
- Component padding: p-6, p-8
- Section gaps: space-y-6, space-y-8
- Input spacing: py-3, px-4
- Card padding: p-8

**Container Strategy**:
- Max width: max-w-4xl mx-auto (optimal for form-focused layouts)
- Main padding: px-6 py-12
- Responsive: full-width mobile, contained desktop

### D. Component Library

**Navigation Header**
- Fixed top bar with backdrop-blur-md
- Logo/title left, webhook status indicator right
- Height: h-16 with border-b border-subtle

**Webhook Configuration Card**
- Prominent surface-elevated card at top
- URL input with lock icon prefix
- "Save Webhook" button (primary brand color)
- Connection status badge (green dot + "Connected")

**Message Composer**
- Large, featured card (surface-elevated)
- Sections: Username input (optional), Avatar URL input (optional), Message textarea
- Textarea: min-h-32, resize-y, with character counter
- Preview pane showing Discord-style message rendering
- Action buttons: "Send Message" (primary), "Clear" (outline)

**Message History Panel**
- Scrollable list of sent messages
- Each message: Discord-style message bubble with timestamp, username, avatar
- Alternating subtle background for readability
- Empty state: illustration + "No messages sent yet"

**Form Inputs**
- Consistent height: h-12
- Border radius: rounded-lg
- Focus states: ring-2 ring-primary with ring-offset-2
- Prefix icons: text-muted, 20px size
- Placeholders: text-muted with helpful examples

**Buttons**
- Primary: bg-primary text-white with hover lift (shadow-lg)
- Outline: border-2 border-primary text-primary
- Heights: h-11 for primary actions, h-9 for secondary
- Full-width on mobile, auto on desktop

**Status Indicators**
- Success toast: slide-in from top-right, auto-dismiss 3s
- Error inline: below relevant field, red text with warning icon
- Loading: Discord-style pulsing dots animation

### E. Layout Composition

**Page Structure** (single-page app):
1. Header (fixed, h-16)
2. Main Container (max-w-4xl, pt-24)
   - Webhook Config Card (mb-8)
   - Message Composer Card (mb-8)
   - Message History Section

**Grid System**:
- Single column layout (form-optimized)
- Two-column within cards: md:grid md:grid-cols-2 md:gap-6 for Username/Avatar inputs
- Stack to single column on mobile

### F. Micro-Interactions
- Button hover: subtle scale (scale-105) + shadow increase
- Input focus: smooth ring animation (transition-all duration-200)
- Message send: brief checkmark animation + success toast
- Form validation: shake animation on error
- No elaborate animations - focus on utility and speed

### G. Accessibility & Quality
- All inputs have visible labels (not just placeholders)
- Minimum touch target: 44px height
- Keyboard navigation: clear focus indicators
- ARIA labels for icon-only buttons
- Error messages linked to inputs via aria-describedby
- High contrast text ratios (WCAG AA compliant)

### H. Discord Visual Identity
- Use Discord's blurple as primary action color
- Message bubbles mimic Discord's chat UI
- Avatar placeholders use Discord's default avatar style
- Success states use Discord green
- Maintain Discord's friendly, approachable tone in UI copy

**Key Principle**: Functional elegance - every element serves a purpose, forms are effortless to complete, and the interface stays out of the user's way while looking polished and professional.