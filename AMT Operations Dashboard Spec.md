# AMT Operations Dashboard — Frontend Specification

> This document is a complete, authoritative specification for recreating the AMT Unified Trading Operations Dashboard. Build exactly what is described here. Do not add features, change colours, or modify structure unless explicitly instructed.

-----

## 1. Technology Stack

|Layer    |Choice                          |
|---------|--------------------------------|
|Framework|React 18 + TypeScript           |
|Styling  |Tailwind CSS v4                 |
|Icons    |`lucide-react`                  |
|Charts   |`recharts` (Prometheus tab only)|
|Build    |Vite                            |

-----

## 2. Colour Palette

All colours are used as inline `style` props, not Tailwind colour classes, so they are easy to audit and change.

### Goldman Sachs Brand Palette

|Token          |Hex      |Usage                                                                         |
|---------------|---------|------------------------------------------------------------------------------|
|`gs-navy`      |`#0B2D59`|Primary text, headings, borders, active tab underline, detail panel top border|
|`gs-navy-dark` |`#071D3A`|Header bar background                                                         |
|`gs-steel`     |`#6B8DB5`|Secondary labels, icon tints, button text, muted UI                           |
|`gs-light-blue`|`#A8C4DC`|Sidebar labels, active sidebar highlights                                     |
|`gs-charcoal`  |`#1E1E2A`|Default body text                                                             |
|`gs-surface`   |`#F4F6F9`|Page background, detail panel header background                               |

### Status Colours (signal only — never used for branding)

|State   |Background|Text / Badge bg|Badge text|
|--------|----------|---------------|----------|
|Healthy |—         |`#DCFCE7`      |`#15803D` |
|Warning |—         |`#FEF3C7`      |`#92400E` |
|Critical|—         |`#FEE2E2`      |`#991B1B` |
|Unknown |—         |`#F3F4F6`      |`#374151` |

Status bar colours (left border of status badge): `#16A34A` (healthy), `#D97706` (warning), `#DC2626` (critical), `#6B7280` (unknown).

### Sidebar palette (dark navy background)

The sidebar background is `#0B2D59`. All sidebar text, borders, and button states use opacity variants of `#A8C4DC` and `#6B8DB5` on this dark ground.

-----

## 3. Global CSS Rules

```css
/* Hide all scrollbars globally — users scroll, bars don't show */
* { scrollbar-width: none; }
*::-webkit-scrollbar { display: none; }

/* Page background */
body { background: #F4F6F9; color: #1E1E2A; }
```

-----

## 4. Layout Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│  Header (h=52px, full width, position: sticky top)                      │
├──────────────────┬──────────────────────────────────────────────────────┤
│  Sidebar         │  Main scroll area                                    │
│  w=240px         │  - Page title row                                    │
│  dark            │  - System Block Grid (3-col)                         │
│  navy            │  - Detail Panel (appears below grid)                 │
└──────────────────┴──────────────────────────────────────────────────────┘
```

- Root: `h-screen flex flex-col`
- Body row: `flex-1 flex overflow-hidden`
- Main: `flex-1 overflow-y-auto`
- Max content width: `max-w-7xl mx-auto p-6`

-----

## 5. Header Component

**File:** `src/app/components/Header.tsx`

**Height:** 52px. Background: `#071D3A`. Bottom border: `rgba(168,196,220,0.15)`.

**Left side:**

- “GOLDMAN SACHS” in `text-sm font-bold tracking-wide` colour `#A8C4DC`, letter-spacing `0.08em`
- Below it: “AMT Unified Trading · Operations Dashboard” in `text-xs` colour `#6B8DB5`
- No environment badge in the header — environment is shown on the main page only

**Right side (flex row, gap-3):**

- “Updated HH:MM:SS AM/PM” in `text-xs` colour `#6B8DB5`
- Custom toggle switch (28×16px pill) controlling auto-refresh:
  - Track background: `#0B2D59` when ON, `rgba(107,141,181,0.3)` when OFF
  - Track border: `1px solid rgba(168,196,220,0.3)`
  - Thumb (12×12px circle): `#A8C4DC` when ON, `#6B8DB5` when OFF
  - Thumb left offset: `14px` when ON, `2px` when OFF
  - Label “Auto” in `text-xs` colour `#94A3B8`
- Refresh icon button (`RefreshCw` size-3.5), colour `#6B8DB5`, `p-1.5 rounded`

**Props:**

```ts
interface HeaderProps {
  lastUpdated: string;
  autoRefresh: boolean;
  onRefresh: () => void;
  onToggleAutoRefresh: () => void;
}
```

-----

## 6. Sidebar Component

**File:** `src/app/components/Sidebar.tsx`

**Width:** 240px (`w-60`). Background: `#0B2D59`. Right border: default. `flex flex-col overflow-y-auto`.

### 6.1 Section ordering (top to bottom)

1. Environment Toggle
1. Divider
1. Quick Filters
1. Divider
1. System Blocks list

### 6.2 Environment Toggle

Section label: “ENVIRONMENT” — `text-xs uppercase tracking-widest` colour `#A8C4DC`. `px-4 pt-5 pb-4`.

Toggle pill: two buttons side by side in a `flex rounded-md overflow-hidden border` (border colour `rgba(168,196,220,0.25)`).

|State   |Background   |Text                   |
|--------|-------------|-----------------------|
|Active  |`#6B8DB5`    |`#fff`                 |
|Inactive|`transparent`|`rgba(168,196,220,0.5)`|

Both options: `PROD` and `UAT`. Style is identical for both — no red/green, no status colour. The active option just gets the steel-blue fill.

### 6.3 Quick Filters

Section label: “QUICK FILTERS” — same style as section labels above. `px-4 mb-4`.

Four filter buttons stacked vertically with `space-y-1`. Each is a `w-full flex items-start gap-2.5 px-3 py-2 rounded-md text-left` button.

|State   |Background              |Border                            |Text     |
|--------|------------------------|----------------------------------|---------|
|Active  |`rgba(107,141,181,0.35)`|`1px solid rgba(168,196,220,0.45)`|`#fff`   |
|Inactive|`rgba(255,255,255,0.05)`|`1px solid rgba(168,196,220,0.15)`|`#94A3B8`|

Each filter has an icon (left, `mt-px flex-shrink-0`, colour `#A8C4DC` active / `#6B8DB5` inactive) and two text lines:

- Label: `text-xs font-medium leading-tight`
- Description: `fontSize: 10px leading-tight mt-0.5` colour `#6B8DB5`

|Filter id   |Label              |Icon           |Description                    |
|------------|-------------------|---------------|-------------------------------|
|`critical`  |Critical Only      |`AlertCircle`  |Systems in critical state      |
|`degraded`  |Degraded           |`AlertTriangle`|Warning or critical            |
|`sevs`      |Active SEVs        |`Activity`     |Systems with open incidents    |
|`trade-path`|Trade Critical Path|`Zap`          |Engine · FIX · Middletier · DRA|

Filter logic applied to the system block grid:

- `critical` → show only blocks with `status === 'critical'`
- `degraded` → show blocks with `status === 'warning' || status === 'critical'`
- `sevs` → show blocks with `sevs > 0`
- `trade-path` → show only IDs: `['trade-engine', 'fix-engine', 'middletier', 'dra']`
- `null` (default) → show all

Clicking the active filter again clears it (sets to null). Filters are mutually exclusive.

### 6.4 System Blocks List

Section label: “SYSTEM BLOCKS”. `px-4 mb-2`.

**“View All” entry** — first item, default selected state (`selectedBlockId === null`). No icon, no dot — just `<span className="flex-1 text-xs font-medium">View All</span>`. A hairline divider (`height: 1`, background: `rgba(168,196,220,0.1)`) separates View All from the block list.

**Block entries** — one button per system block. No status dots. No search input.

```
[ Block Name             1 SEV ]
```

Each button: `w-full flex items-center gap-2.5 px-3 py-2 rounded-md mb-0.5 text-left`

|State   |Background             |Text     |
|--------|-----------------------|---------|
|Selected|`rgba(168,196,220,0.2)`|`#fff`   |
|Default |`transparent`          |`#CBD5E1`|

SEV badge (only shown when `sevCount > 0`): `background: #DC2626, color: #fff, fontSize: 10px, px-1.5 py-0.5 rounded`.

**Props:**

```ts
export type QuickFilter = 'critical' | 'sevs' | 'degraded' | 'trade-path' | null;

interface SidebarProps {
  systemBlocks: { id: string; name: string; status: string; sevCount?: number; jobCount?: number }[];
  selectedBlockId: string | null;
  onSelectBlock: (id: string | null) => void;
  environment: 'PROD' | 'UAT';
  onEnvironmentChange: (env: 'PROD' | 'UAT') => void;
  activeFilter: QuickFilter;
  onFilterChange: (filter: QuickFilter) => void;
}
```

-----

## 7. Main Content Area

### 7.1 Page Title Row

```
Control Center   [PROD]
Live operating snapshot across AMT trading systems
```

- “Control Center”: `text-2xl font-semibold` colour `#0B2D59`
- Environment badge (inline, next to heading): `px-3 py-0.5 rounded text-xs font-bold tracking-widest uppercase`, background `#0B2D59`, text `#A8C4DC`, letterSpacing `0.12em`. Reflects the current environment state.
- Subtitle: `text-sm` colour `#6B7280`
- When a filter is active, show inline pill: `background: #D1DEEE, color: #0B2D59, text-xs font-medium px-2 py-0.5 rounded` → “Filter active — N of 11 blocks shown”

### 7.2 System Block Grid

`grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4`

Section heading: “System Blocks” `text-lg font-semibold` colour `#0B2D59`. Right-aligned count: “N of 11 blocks” in `text-sm` colour `#6B7280`.

-----

## 8. SystemBlockCard Component

**File:** `src/app/components/SystemBlockCard.tsx`

**Shape:** White card, `rounded-lg`, uniform border (no coloured left bar).

|State   |Border                           |Box Shadow                                                       |
|--------|---------------------------------|-----------------------------------------------------------------|
|Default |`1px solid rgba(11,45,89,0.1)`   |`0 1px 3px rgba(11,45,89,0.06)`                                  |
|Selected|`1px solid rgba(107,141,181,0.5)`|`0 0 0 2px rgba(107,141,181,0.25), 0 4px 12px rgba(11,45,89,0.1)`|

**Card internals (p-4):**

**Top row:**

- Block name: `text-sm font-semibold` colour `#0B2D59`
- Description: `text-xs mt-0.5 leading-relaxed` colour `#6B7280`
- Status badge (top-right, flex-shrink-0): `px-2 py-0.5 rounded text-xs font-semibold` — colours from status table in section 2

**Stats grid** (`grid grid-cols-2 gap-y-1.5 gap-x-4 mt-3`): four items — Jobs, Hosts, Open SEVs, Panels. Each: label in `#9CA3AF`, value in `#1E1E2A font-semibold tabular-nums`.

**Footer row** (separated by `1px solid rgba(11,45,89,0.07)`, `pt-3 mt-2`):

- Left: “{N} running” — the number in `#16A34A`. If `warningMetrics > 0`, append ` · {N} warnings` in `#D97706`.
- Right: **Explore button** — `px-3 py-1.5 rounded-md text-xs font-semibold flex items-center gap-1`. Background `#0B2D59`, text `#A8C4DC`, border `1px solid rgba(168,196,220,0.25)`. On hover: background `#6B8DB5`, text `#fff`. Uses `onMouseEnter`/`onMouseLeave` for hover state. Click calls `onExplore()` (stops propagation).

**Behaviour:**

- Clicking the card body calls `onClick()` — selects the block (opens detail panel) but does NOT scroll.
- Clicking the Explore button calls `onExplore()` — selects AND smooth-scrolls to the detail panel.

**Props:**

```ts
interface SystemBlockCardProps {
  block: SystemBlockData;
  isSelected: boolean;
  onClick: () => void;
  onExplore: () => void;
}
```

-----

## 9. Mock Data — 11 System Blocks

**File:** `src/app/data/mockData.ts`

```ts
export interface SystemBlockData {
  id: string;
  name: string;
  description: string;
  status: 'healthy' | 'warning' | 'critical' | 'unknown';
  jobs: number;
  hosts: number;
  sevs: number;
  panels: number;
  runningJobs: number;
  warningMetrics?: number;
}
```

|id              |name          |status  |jobs|hosts|sevs|panels|runningJobs|warningMetrics|
|----------------|--------------|--------|----|-----|----|------|-----------|--------------|
|`ui-facing`     |UI Facing     |warning |39  |39   |1   |6     |37         |2             |
|`dra`           |DRA           |healthy |24  |24   |0   |5     |24         |0             |
|`clientside`    |Clientside    |healthy |154 |154  |0   |4     |154        |0             |
|`upstream`      |Upstream      |healthy |2   |2    |0   |6     |2          |0             |
|`notification`  |Notification  |healthy |5   |5    |0   |5     |5          |0             |
|`middletier`    |Middletier    |warning |1   |1    |1   |0     |6          |1             |
|`trade-engine`  |Trade Engine  |critical|2   |2    |0   |6     |2          |3             |
|`fix-engine`    |FIX Engine    |healthy |60  |60   |0   |5     |60         |0             |
|`reconciliation`|Reconciliation|warning |32  |32   |0   |5     |32         |1             |
|`reference-data`|Reference Data|healthy |30  |30   |0   |5     |30         |0             |
|`reg-compliance`|Reg Compliance|healthy |40  |40   |0   |5     |40         |0             |

Descriptions (in order): “DRA streaming, WebSocket feeds & real-time data relay” / “Dynamic resource allocation & server orchestration” / “UI static site, CDN health, browser error tracking” / “Upstream feed ingestion, order receipt & validation” / “Email, Symphony & push alert delivery” / “Orchestration, business logic & Concert API gateway” / “Order validation, execution & allocation pipeline” / “FIX protocol sessions, message routing & drop-copy” / “Trade reconciliation, position matching & break resolution” / “Security master, counterparty & static data management” / “Regulatory reporting, compliance checks & audit trails”

-----

## 10. App State (App.tsx)

```ts
const [selectedBlockId, setSelectedBlockId] = useState<string | null>(null); // default null = "View All"
const [environment, setEnvironment] = useState<'PROD' | 'UAT'>('PROD');
const [activeFilter, setActiveFilter] = useState<QuickFilter>(null);
const [autoRefresh, setAutoRefresh] = useState(true);
const [lastUpdated, setLastUpdated] = useState(new Date());
const detailPanelRef = useRef<HTMLDivElement>(null);
```

**Auto-refresh:** `setInterval` every 30 seconds updates `lastUpdated` when `autoRefresh` is true.

**handleExplore(id):** Sets `selectedBlockId(id)`, then after 80ms calls `detailPanelRef.current?.scrollIntoView({ behavior: 'smooth', block: 'start' })`.

**handleSidebarSelect(id | null):** Sets `selectedBlockId(id)`. If id is not null, same scroll behaviour as handleExplore.

The `<div ref={detailPanelRef}>` wraps the `DetailPanel` at the bottom of the main content area.

-----

## 11. Detail Panel Component

**File:** `src/app/components/DetailPanel.tsx`

Appears below the system block grid when a block is selected. Wrapped in a `ref` div for scroll targeting.

**Container:** `rounded-lg mt-6`, background `#fff`, border `1px solid rgba(11,45,89,0.12)`, **top border `3px solid #0B2D59`**, box-shadow `0 4px 16px rgba(11,45,89,0.1)`.

### 11.1 Panel Header

Background `#F4F6F9`, border-bottom `1px solid rgba(11,45,89,0.08)`. Padding `p-4`.

Top row:

- Breadcrumb: “All Systems / {block.name}” `text-xs` colour `#9CA3AF`
- Block name: `text-lg font-semibold` colour `#0B2D59`
- Description: `text-sm` colour `#6B7280`
- Close button (top-right): `X` Icon, `p-2 rounded-md`, colour `#6B8DB5`

Bottom row:

- Status badge (variant from status)
- Jobs / Hosts / SEVs / Dashboards inline stats: label `#9CA3AF`, value `#0B2D59 font-semibold`
- Right side: “Refresh” button + “Open in Grafana” button — both `px-3 py-1.5 text-xs rounded-md flex items-center gap-1`, border `1px solid rgba(11,45,89,0.2)`, text `#6B8DB5`

### 11.2 Tabs

Five tabs (no Overview — it was removed):

|id          |Label           |Count badge source|
|------------|----------------|------------------|
|`procmon`   |Procmon & Nimbus|`block.jobs`      |
|`prometheus`|Prometheus      |hardcoded `18`    |
|`grafana`   |Grafana         |hardcoded `1`     |
|`bql`       |BQL Logs        |hardcoded `6`     |
|`sevs`      |Open SEVs       |`block.sevs`      |

**Default active tab:** `procmon`

Tab button styles:

- Active: `color: #0B2D59, borderBottom: 2px solid #0B2D59`
- Inactive: `color: #9CA3AF`
- Count badge: `background: #E8EDF4, color: #0B2D59, px-1.5 py-0.5 text-xs rounded-full ml-1.5`

BQL Logs and Open SEVs tabs render a plain centred placeholder message. All others render their respective tab component.

-----

## 12. Procmon & Nimbus Tab

**File:** `src/app/components/tabs/ProcmonTab.tsx`

**Layout:** Two-column grid (`grid grid-cols-2 gap-6`).

### Left panel — Job groups list

Search input (full width, with `Search` icon, placeholder “Search job, process, FQDN, host, Nimbus real-server…”).

Status filter pills: All / Running / Pending / Failed — `px-3 py-1.5 text-xs border border-gray-300 rounded-md hover:bg-gray-50`.

Expandable job groups (accordion). Each group:

- Header button: `w-full flex items-center justify-between p-3 bg-gray-50 hover:bg-gray-100`
- Left: `ChevronDown`/`ChevronRight` icon + group name `font-semibold text-sm` + instance count badge
- Right: RUNNING badge
- Expanded rows: each `JobInstance` in a `divide-y` list — click selects it for the right panel

**Mock data (for `ui-facing` block only — other blocks show empty):**

Group “Allocation” (3 instances): ALLOCATION DRA — allocationPool PID0/1/2, status running, nimbusStatus up, fqdn `d203446-htt-appserver-prod-ny-a004.dc.gs.com`, PID `19876` on PID0 only.

Group “Placement” (3 instances): PLACEMENT DRA — placementPool PID0/1/2, all running.

Group “Execution” (2 instances): EXECUTION DRA Server Prod — execution-dra-pool PID0/1, all running.

Group “Static UI” (3 instances): amt_trading_ui_deploy_static_site — prodOld0/prodOld1 (pending, nimbusStatus unknown), prod_PID1 (running, up).

### Right panel — Instance detail

When no job selected: dashed border placeholder “No job selected / Select a job from the list to view details”.

When a job is selected: `bg-gray-50 rounded-lg border border-gray-200 p-4` with two-column label/value grid:

- Status (badge), FQDN (font-mono text-xs break-all), PID (if present, font-mono), Pool Name, Username (`p2iamtrdprod`), Rundate (`20260601`), Memory (`-Xmx20G -Xms20G`), Slots (`20`)

Footer buttons: “View Logs via Procmon” (full-width, `bg-blue-600 text-white`) + “Open host in Grafana” (full-width, border).

-----

## 13. Prometheus Tab

**File:** `src/app/components/tabs/PrometheusTab.tsx`

**Health banner:** `bg-green-50 border border-green-200 rounded-lg p-4 mb-4` — “All systems healthy”, “18 jobs evaluated · Last evaluation: just now”, “4 UP · 2 warnings · 99.6% avg availability”.

**Controls row:** Table / Hosts / All Jobs toggle buttons + “Warnings only” checkbox.

**Metrics table** (dense, `text-xs`, dark header `bg-gray-800 text-white`):

Columns: JOB · STATUS · HEAP % · OLD GEN % · GC PROMO RATIO · PROC CPU · SYS CPU · P95 · P99 · THREADS · BLOCKED · GC PAUSE · GC FREQ · AVAILABILITY

P99 values > 10 seconds are highlighted `text-red-600 font-semibold`.

Mock rows (5 rows):

|Job                |Status     |Heap |OldGen|GcPromo|ProcCpu|SysCpu|P95    |P99   |Threads|Blocked|GcPause|GcFreq|Avail|
|-------------------|-----------|-----|------|-------|-------|------|-------|------|-------|-------|-------|------|-----|
|allocationPool PID0|UP         |47.9%|33.5% |0.0%   |0.4%   |11.2% |67.9ms |17.58s|313    |0      |17.0ms |0.00/s|99.5%|
|allocationPool PID1|UP         |83.8%|36.5% |0.6%   |0.5%   |6.6%  |123.6ms|44.79s|321    |0      |58.4ms |0.00/s|99.6%|
|placementPool PID0 |UP         |67.4%|38.1% |0.5%   |0.8%   |3.5%  |107.1ms|16.32s|321    |0      |35.0ms |0.00/s|99.8%|
|LionViewDRA        |UP         |39.5%|29.2% |0.2%   |1.5%   |5.2%  |51.4ms |16.6ms|333    |0      |93.9ms |0.00/s|99.9%|
|BasketViewModel    |SCRAPE ONLY|—    |—     |—      |—      |—     |0µs    |0µs   |—      |—      |—      |—     |—    |

-----

## 14. Grafana Tab

**File:** `src/app/components/tabs/GrafanaTab.tsx`

**Layout:** Two-column grid (`grid grid-cols-2 gap-6`).

**Default state:** First host is auto-selected on mount (`useState<Host | null>(mockHosts[0])`).

### Left panel — Host selector

Title: “Monitoring — Hosts” `font-semibold text-sm mb-3`.

Search input with `Search` icon.

Filter pills: “All (5)” (active, `bg-blue-600 text-white`), “Procmon (5)”, “Prometheus (0)”, “▲ Down (0)” — `px-3 py-1.5 text-xs rounded-full`.

Host list container: `bg-gray-900 rounded-lg p-4`. Each row: `p-2 rounded cursor-pointer`. Selected: `bg-blue-600 text-white`. Default: `text-gray-300 hover:bg-gray-800`.

Each row shows: green dot (`bg-green-500`) + hostname `text-sm font-medium` + FQDN `text-xs opacity-75 font-mono` + source badge (“Procmon” in success variant).

Mock hosts (5):

1. `d203446-amtrd-prod-ny-a010` / `d203446-amtrd-prod-ny-a010.dc.gs.com` / Procmon / running
1. `d203446-htt-appserver-prod-ny-a001` / `.dc.gs.com` / Procmon / running
1. `d203446-htt-appserver-prod-ny-a002` / `.dc.gs.com` / Procmon / running
1. `d203446-htt-appserver-prod-ny-a003` / `.dc.gs.com` / Procmon / running
1. `d203446-htt-appserver-prod-ny-a004` / `.dc.gs.com` / Procmon / running

### Right panel — Grafana preview

**Dark header bar** (`bg-gray-900 text-white rounded-t-lg p-4`): hostname + FQDN + “Open in Grafana” button (`bg-green-600`).

**Content area** (`border border-t-0 rounded-b-lg p-4 bg-white`):

- “Hosts/Device Overview” heading + time-range selector dropdown (Last 1 hour / 6h / 24h) + refresh icon + “5s” label.
- CPU panel: `border rounded-lg p-3`, `h-32 bg-gray-50` placeholder with `BarChart3` icon + “CPU metrics visualization”
- RAM panel: same structure + “65.2 GiB total” subtitle

-----

## 15. Interaction Behaviours

|Action                         |Result                                                                |
|-------------------------------|----------------------------------------------------------------------|
|Click card body                |`selectedBlockId` updated → detail panel opens below grid. No scroll. |
|Click Explore button           |`selectedBlockId` updated → smooth scroll to detail panel (80ms delay)|
|Click sidebar block            |`selectedBlockId` updated → smooth scroll to detail panel             |
|Click “View All”               |`selectedBlockId = null` → detail panel hidden                        |
|Click close (×) in detail panel|`selectedBlockId = null` → detail panel hidden                        |
|Click quick filter (inactive)  |`activeFilter` set → grid filters to matching blocks only             |
|Click quick filter (active)    |`activeFilter = null` → all blocks shown                              |
|Toggle environment             |`environment` flips PROD ↔ UAT → badge in page title updates          |
|Toggle auto-refresh            |Stops/starts 30s interval                                             |
|Click refresh icon             |`lastUpdated` set to `new Date()`                                     |

-----

## 16. File Structure

```
src/
  app/
    App.tsx                ← root, all state lives here
    components/
      Header.tsx
      Sidebar.tsx
      SystemBlockCard.tsx
      DetailPanel.tsx
      tabs/
        ProcmonTab.tsx
        PrometheusTab.tsx
        GrafanaTab.tsx
    data/
      mockData.ts
    styles/
      theme.css            ← CSS tokens + scrollbar suppression
      fonts.css            ← font imports only
```

-----

## 17. What is NOT in this dashboard

The following were deliberately removed. Do not re-add them:

- KPI summary cards (Total Jobs / Open SEVs / Live Dashboards) — removed from main page
- “Overview” tab in the detail panel — removed; Procmon & Nimbus is the first tab
- Status dots in the sidebar system blocks list — removed
- Coloured left-border bars on system block cards — removed
- Search/filter box in the sidebar system blocks section — removed
- Checkboxes next to sidebar system blocks — removed
- “Critical / warnings / healthy” count row in the header — removed
- Red/green colour coding for PROD/UAT toggle — removed