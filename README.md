# Website Design Brief - Edge Functions Platform

## Project Overview
We're building a marketplace website for edge functions - a platform offering 500+ pre-built API functions that developers can use in any programming language. Think of it as a library of ready-to-use tools (JSON converters, HTML processors, QR code generators, etc.) accessible via API.

---

## Website Structure

### **Main Domain Architecture**
- `domain.com` � Main marketing website (NOT part of this brief)
- `domain.com/products/functions` � Product landing page (NOT part of this brief)
- **`domain.com/functions`** � **Functions Marketplace**  THIS BRIEF
- `domain.com/workers` � Future feature (ignore for now)
- `domain.com/agents` � Future feature (ignore for now)

---

## Pages to Design

### **Page 1: Marketplace** (`/functions`)
The main hub where users browse and search all available functions.

### **Page 2: Category Page** (`/functions/{category-name}`)
Shows all functions within a specific category (e.g., all JSON-related functions).

### **Page 3: Function Detail Page** (`/functions/{function-name}`)
Individual page for each function with playground, documentation, and metrics.

---

## Detailed Page Specifications

---

## PAGE 1: Marketplace (`/functions`)

### Purpose
Browse and search all 500+ functions across 16 categories.

### Page Sections (Top to Bottom)

#### **1. Header Section**
- Large search bar with placeholder: "Search functions... (e.g., json prettify, html minify)"
- Search should feel prominent and inviting
- Include autocomplete/suggestions dropdown when typing

#### **2. Category Filter Section**
- Horizontal row of category pills/tabs
- 16 categories: Color, Country, CSS, CSV, Diff, Distance, HTML, JavaScript, JSON, Levenshtein, Markdown, Punycode, QRCode, Text, XML, YAML
- Visual design: Pills or tabs that can be clicked to filter
- "All" option to show everything
- Active state should be clearly visible

#### **3. Functions Grid**
- Grid layout (3-4 columns on desktop, 1-2 on mobile)
- Each function displays as a card

**Function Card Contains:**
- **Category Badge** (top corner, color-coded by category)
- **Function Name** (bold, prominent)
- **Short Description** (1-2 lines of text)
- **Performance Indicator** (e.g., "� 8ms avg")
- **Popularity Indicator** (e.g., "=% Popular" or usage count)
- **CTA Button**: "Try Playground �"

**Card Interaction:**
- Hover state shows slight elevation/shadow
- Entire card is clickable (goes to function detail page)

#### **4. Sorting Options**
- Sort by: Popular / Alphabetical / Recently Added
- Small dropdown or tab selector

---

## PAGE 2: Category Page (`/functions/{category-name}`)

### Purpose
Show all functions within a specific category (e.g., all JSON functions).

### Page Sections (Top to Bottom)

#### **1. Category Header**
- **Category Name** (large, prominent - e.g., "JSON Functions")
- **Category Description** (rich text/HTML content explaining what this category is for)
- **Breadcrumb Navigation**: Home > Functions > JSON

#### **2. Functions Grid**
- Same card design as Marketplace page
- Only shows functions from this specific category
- Same sorting options (Popular / A-Z / Recent)

#### **3. Related Categories** (Optional Section)
- "Explore related categories" with links to similar categories
- E.g., on JSON page: show XML, YAML, CSV categories

---

## PAGE 3: Function Detail Page (`/functions/{function-name}`)

### Purpose
Complete information about a single function with interactive playground, documentation, and usage metrics.

### Page Sections (Top to Bottom)

#### **1. Function Header**
- **Breadcrumb**: Home > Functions > {Category} > {Function Name}
- **Category Badge** (same as cards, color-coded)
- **Function Name** (large, prominent - e.g., "JSON Prettify")
- **Short Description** (1-2 sentence summary)
- **HTML Content Section** (rich text content with detailed explanation, use cases, how it works)
- **Quick Stats Bar** (horizontal row showing):
  - Average response time (e.g., "8ms avg")
  - Total monthly uses (e.g., "1.2M uses/month")
  - Uptime percentage (e.g., "99.9% uptime")
  - Supported protocols (HTTP, gRPC, Socket.io icons)

#### **2. Tab Navigation**
Three main tabs that switch content below:

**Tab 1: Playground** (default active)
**Tab 2: Integration**
**Tab 3: Metrics**

---

### TAB 1: Playground

**Purpose:** Let users test the function for free with live results.

**Layout:**
- Two-column layout (or stacked on mobile)
- **Left Column: Input Section**
  - Form fields based on function requirements
  - Example: for "json-prettify" � large textarea for JSON input
  - "Clear" button to reset
  - Pre-filled example data by default

- **Right Column: Output Section**
  - Shows result after execution
  - For simple functions: formatted output display
  - For visual functions (like text-diff): GitHub-style visual diff
  - Display execution metadata below result:
    - "Executed in 12ms"
    - Gateway location used
    - Timestamp
  - "Copy Result" button
  - "Share Result" button (generates permalink)

**Execute Button:**
- Large, prominent "Run Function" button between input/output
- Loading state when processing
- **Limitation Notice** (small text): "Free playground: 1 request at a time, unlimited use, no account needed"

**Different Playground Layouts for Different Functions:**
- **Simple transforms** (json-prettify): Input textarea � Output textarea
- **Visual functions** (text-diff): Side-by-side diff view with color highlighting
- **Generators** (qrcode-generate): Form inputs � Visual preview (show QR code image)
- **Multi-output** (color-palette): Input � Multiple result cards/swatches

---

### TAB 2: Integration

**Purpose:** Show developers how to use this function via API.

**Layout Sections (vertical stack):**

#### **Protocol Selector**
- Toggle/tabs to switch between: HTTP API / gRPC / Socket.io
- Changes all code examples below

#### **Language Selector**
- Dropdown to select: cURL, JavaScript, Python, PHP, Go, Ruby, etc.
- Changes code example format

#### **Quick Reference Card**
- Endpoint URL (e.g., `https://api.domain.com/functions/json-prettify`)
- Method (POST/GET)
- Authentication header format
- Rate limits (e.g., "Unlimited on $39/month plan")

#### **Code Example Section**
- Large code block showing complete example in selected language
- Syntax highlighting
- "Copy Code" button
- Shows: authentication, request body, response handling

#### **Request Schema**
- Table or formatted display showing:
  - Parameter name
  - Type (string, number, etc.)
  - Required/Optional
  - Description
  - Example value

#### **Response Schema**
- Shows expected response format
- Example successful response (JSON formatted)
- Common error responses (with error codes)

#### **SDK Installation** (if SDK available)
- Command to install SDK for selected language
- Quick usage example with SDK

---

### TAB 3: Metrics

**Purpose:** Show public usage statistics and performance data.

**Layout Sections (vertical stack):**

#### **Executions Chart**
- **Title:** "Monthly Executions"
- **Chart Type:** Bar chart
- **Data:** Last 12 months
- **Y-axis:** Number of executions
- **X-axis:** Month names
- Show hover tooltips with exact numbers

#### **Response Time Chart**
- **Title:** "Average Response Time"
- **Chart Type:** Line chart
- **Data:** Last 12 weeks (weekly averages)
- **Y-axis:** Milliseconds
- **X-axis:** Week numbers or dates
- Show hover tooltips with exact times
- Optional: Show p50, p95, p99 percentiles as multiple lines

#### **Key Metrics Cards** (3 cards in a row)
- **Card 1:** Total executions this month (big number + trend arrow)
- **Card 2:** Average response time (big number in ms + trend arrow)
- **Card 3:** Uptime percentage (big number + status indicator)

---

## Design System Guidelines

### Colors
- Each category should have a distinct color for badges/accents
- Maintain accessibility (WCAG AA contrast ratios)
- Primary CTA color (for "Try Playground" buttons)
- Success/error states for playground results

### Typography
- Clear hierarchy: Page titles � Section headers � Body text � Labels
- Monospace font for code blocks and API endpoints
- Sans-serif for UI and descriptions

### Components to Design

#### **Function Card** (used in marketplace and category pages)
- Default state
- Hover state
- Active/clicked state
- Mobile responsive version

#### **Category Badge** (appears throughout)
- Small pill/badge design
- 16 color variations (one per category)
- Used in cards, headers, breadcrumbs

#### **Tab Navigation** (function detail page)
- Active/inactive states
- Mobile responsive (stack or scroll?)

#### **Code Block Component**
- Syntax highlighted
- Copy button
- Line numbers (optional)
- Dark/light theme options

#### **Chart Components**
- Bar chart design (executions)
- Line chart design (response time)
- Tooltip styles
- Legend design (if needed)

#### **Input/Output Playground Areas**
- Text area styling
- Button designs (Run, Clear, Copy, Share)
- Loading states
- Error states
- Success states

---

## User Flows

### Flow 1: Discover and Test a Function
1. Land on `/functions` marketplace
2. Browse categories or search
3. Click function card � go to function detail page
4. See playground tab (default)
5. Test function with example data
6. View results
7. Copy code from Integration tab to use in their project

### Flow 2: Category Browsing
1. Land on `/functions` marketplace
2. Click category filter pill (e.g., "JSON")
3. Go to `/functions/json` category page
4. See all JSON functions
5. Click specific function � go to detail page

### Flow 3: Check Performance
1. On function detail page
2. Click "Metrics" tab
3. View execution and performance charts
4. Assess if function meets their speed requirements
5. Return to Integration tab to implement

---

## Responsive Behavior

### Desktop (1200px+)
- 3-4 column grid for function cards
- Side-by-side playground (input left, output right)
- All tabs visible in tab navigation

### Tablet (768px - 1199px)
- 2-3 column grid for function cards
- Stacked playground (input top, output bottom)
- Tabs visible but may scroll horizontally

### Mobile (< 768px)
- 1 column for function cards
- Fully stacked layouts
- Tab navigation scrolls horizontally or shows dropdown
- Simplified charts (mobile-optimized)

---

## Content to Provide (You'll Supply)

For each category:
- Name (e.g., "JSON")
- Description (text)
- HTML content (rich text explanation)

For each function:
- Name (e.g., "json-prettify")
- Category association
- Short description (for cards)
- HTML content (detailed explanation)
- Input schema (for playground)
- Example input data
- Code examples (cURL, JS, Python, etc.)

---

## Special Features / Interactions

### Search with Autocomplete
- As user types, show matching function names
- Highlight matching text
- Show category badge in suggestions
- Click suggestion � go to function detail page

### Playground Permalink Sharing
- After running function, "Share" button generates unique URL
- URL contains input/output state
- Anyone with link can see the result (read-only)

### Copy Buttons
- Copy code examples (one-click)
- Copy API endpoints
- Copy playground results
- Visual feedback (checkmark or "Copied!" message)

### Chart Interactivity
- Hover to see exact values
- Zoom or filter date ranges (optional advanced feature)

---

## Key Messages / Copy Tone

- **For Free Users:** "Test unlimited - no account needed"
- **For Developers:** Clear, technical, precise
- **Performance Focus:** Always highlight speed (e.g., "� 8ms avg")
- **Simplicity:** "One API for 500+ functions"
- **Trust Indicators:** Show uptime %, usage numbers, public metrics

---

## Questions for Designer

1. **Visual Style Preference:** Clean minimal (Stripe-like)? Modern/playful (Vercel-like)? Technical/detailed (AWS-like)?

2. **Category Colors:** Should we provide specific color palette for 16 categories, or do you prefer to create it?

3. **Code Block Theme:** Dark theme? Light theme? Toggle option?

4. **Animations:** Any micro-interactions desired? (card hover, tab switching, chart animations)

5. **Iconography:** Custom icon set? Or use existing library (Heroicons, Lucide, etc.)?

---

## Deliverables Needed

- [ ] High-fidelity mockups for all 3 pages (desktop)
- [ ] Mobile responsive versions
- [ ] Component library (cards, badges, tabs, code blocks, charts)
- [ ] Interactive prototype (optional but helpful)
- [ ] Design system specs (colors, typography, spacing)
- [ ] Icon set (if custom)
- [ ] Playground variations for different function types

---

## Timeline Expectations

- **MVP Focus:** Marketplace, Category Page, Function Detail (3 tabs)
- **Future Phases:** Dashboard, Workers, Agents (not in this brief)

---

## Reference Inspiration (Optional)

Similar platforms for reference (not to copy, just for context):
- Stripe API Docs (clean documentation style)
- Vercel Functions (modern developer UX)
- RapidAPI (function marketplace concept)
- GitHub (for diff visualization in playground)
- Postman (for API testing playground feel)

---

**End of Brief**

