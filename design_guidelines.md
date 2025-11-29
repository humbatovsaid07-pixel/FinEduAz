# FinEdu AZ Design Guidelines

## Design Approach
**Reference-Based Approach**: Draw inspiration from premium fintech platforms (Stripe, Revolut, N26) with Azerbaijani cultural context. Premium finance aesthetic with modern, minimal, and extremely clean UI.

## Core Design Elements

### A. Typography
- **Primary Font**: Inter or Manrope (Google Fonts) - clean, modern sans-serif
- **Headings**: Bold weight (700), larger sizes for impact
- **Body Text**: Regular (400) and Medium (500) weights
- **Hierarchy**: Clear distinction between hero text, section headers, labels, and body content
- **All UI text** must support Azerbaijani, English, and Russian characters

### B. Layout System
**Spacing Units**: Tailwind units of 2, 4, 6, 8, 12, 16, 20, 24
- Component padding: p-4, p-6, p-8
- Section spacing: py-12, py-16, py-20
- Gap utilities: gap-4, gap-6, gap-8

### C. Component Library

**Landing Page Components**:
- Hero section with gradient background (80vh)
- Large headline: "FinEdu — Şəxsi maliyyəni ağıllı idarə et!"
- Subtitle with value proposition
- Single prominent CTA button: "Başla" (no secondary button)
- Top navigation with: Login, Register, Language switcher (AZ/EN/RU), Light/Dark toggle
- Finance-themed icons from Heroicons

**Dashboard Layout** (Exact Structure):
- Top greeting: "Salam, {UserName}"
- Three summary cards in row: Monthly Expenses, Monthly Income, Goal Progress
- Two-column grid below:
  - Left: Transaction table (Date, Category, Amount, Type) with add/edit/delete actions
  - Right: Monthly Report preview card
- Bottom row: Goals preview section + Finny advice section

**Transaction System**:
- Input form with date picker, category dropdown, amount field, type toggle
- Table with alternating row backgrounds
- Action buttons (edit/delete) with icon-only minimal design

**Monthly Report Page**:
- Summary cards showing totals (income, outcome, savings)
- Comparison section with regional/age average data
- Visual indicators (arrows, percentages) for comparisons
- Finny advice cards with contextual messages

**Goals System**:
- Card-based goal items with progress bars
- Add goal modal with title and target amount fields
- Contribution tracking with add savings button

**Profile Page**:
- User information display
- Edit mode toggle
- Settings section for language and theme preferences

### D. Visual Theme

**Color Strategy** (Applied later, but note structure):
- Primary gradient: Blue to mint tones
- Dark mode: Deep gradients with elevated components
- Light mode: Clean whites with subtle shadows
- Accent for CTAs and interactive elements

**Shadows & Elevation**:
- Cards: shadow-lg for main components, shadow-md for nested elements
- Hover states: Subtle shadow increase (shadow-xl)
- Modal overlays: shadow-2xl

**Animations**:
- Theme toggle: Smooth 300ms transitions
- Page transitions: Fade-in effects (200ms)
- Button hovers: Scale transform (scale-105) with 150ms duration
- Modal appearances: Slide-up or fade-in (250ms)
- Keep animations minimal and professional

### E. Responsive Breakpoints
- Mobile: base (320px+)
- Tablet: md (768px+)
- Desktop: lg (1024px+)
- Wide: xl (1280px+)

**Mobile Adaptations**:
- Stack dashboard cards vertically
- Single-column transaction table
- Collapsible navigation menu
- Bottom-fixed action buttons where appropriate

### F. Icons & Assets
- **Icon Library**: Heroicons (outline and solid variants)
- **Finance Icons**: Chart, wallet, target, calendar, user, settings
- No custom SVG generation needed

**Images**:
- Landing page hero: Abstract financial illustration or gradient background (no specific image needed, use CSS gradients)
- Dashboard: No images required
- Goals section: Optional icon-based representations

### G. Accessibility
- Minimum touch target: 44x44px for mobile
- Clear focus states on all interactive elements
- Sufficient contrast ratios in both light and dark modes
- Proper semantic HTML throughout
- Form labels clearly associated with inputs
- Error messages clearly visible and descriptive

### H. Special Requirements
- Language switcher must work instantly without page reload
- Light/Dark toggle applies across entire application
- All text elements must be extracted to language JSON files
- No placeholder text or lorem ipsum
- Perfect alignment and spacing throughout
- Premium, polished feel matching fintech industry leaders