# Orion Brand Theme -- HTML Dashboard

Use this theme when generating interactive HTML email dashboards. The design is
based on the Orion Check-In application: clean, light-mode, system fonts, with
the Orion crimson as the primary accent.

## Quick Reference

Copy this CSS block into every HTML dashboard you generate:

```html
<style>
  /* ── Orion Brand Tokens ── */
  :root {
    /* Primary */
    --orion-red: #D50032;
    --orion-red-light: #FEF2F2;
    --orion-red-shadow: rgba(213, 0, 50, 0.25);

    /* Neutrals */
    --text-primary: #1A1A1A;
    --text-secondary: #374151;
    --text-muted: #6B7280;
    --text-faint: #9CA3AF;
    --border-default: #E5E7EB;
    --border-light: #F3F4F6;
    --bg-page: #F9FAFB;
    --bg-card: #FFFFFF;
    --bg-hover: #F3F4F6;

    /* Priority Tier Colors */
    /* Urgent (Red) */
    --urgent-bg: #FEF2F2;
    --urgent-text: #DC2626;
    --urgent-pill-bg: #FEE2E2;
    --urgent-pill-text: #B91C1C;
    --urgent-dot: #EF4444;
    --urgent-border: #FEE2E2;

    /* Important (Amber) */
    --important-bg: #FFF8E1;
    --important-text: #B45309;
    --important-pill-bg: #FEF3C7;
    --important-pill-text: #92400E;
    --important-dot: #F59E0B;
    --important-border: #FEF3C7;

    /* Delegate (Purple) */
    --delegate-bg: #F3E8FF;
    --delegate-text: #7C3AED;
    --delegate-pill-bg: #EDE9FE;
    --delegate-pill-text: #6D28D9;
    --delegate-dot: #8B5CF6;
    --delegate-border: #EDE9FE;

    /* Defer (Blue) */
    --defer-bg: #EFF6FF;
    --defer-text: #2563EB;
    --defer-pill-bg: #DBEAFE;
    --defer-pill-text: #1D4ED8;
    --defer-dot: #3B82F6;
    --defer-border: #DBEAFE;

    /* FYI / Archive (Gray) */
    --fyi-bg: #F9FAFB;
    --fyi-text: #6B7280;
    --fyi-pill-bg: #F3F4F6;
    --fyi-pill-text: #6B7280;
    --fyi-dot: #9CA3AF;
    --fyi-border: #F3F4F6;

    /* Success (Green) */
    --success-bg: #ECFDF5;
    --success-text: #059669;
    --success-dot: #10B981;

    /* Danger */
    --danger: #EF4444;

    /* Typography */
    --font-sans: ui-sans-serif, system-ui, -apple-system, sans-serif,
      "Apple Color Emoji", "Segoe UI Emoji";
    --font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;

    /* Radius */
    --radius-sm: 6px;
    --radius-md: 8px;
    --radius-lg: 12px;
    --radius-xl: 16px;
    --radius-pill: 999px;

    /* Shadows */
    --shadow-card: 0 1px 3px rgba(0,0,0,0.04);
    --shadow-md: 0 4px 6px -1px rgba(0,0,0,0.1), 0 2px 4px -2px rgba(0,0,0,0.1);
    --shadow-dropdown: 0 4px 16px rgba(0,0,0,0.12), 0 1px 3px rgba(0,0,0,0.06);
    --shadow-primary: 0 2px 8px rgba(213, 0, 50, 0.25);
  }

  /* ── Reset & Base ── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: var(--font-sans);
    background: var(--bg-page);
    color: var(--text-primary);
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
  }

  /* ── Layout Shell ── */
  .dashboard { display: flex; flex-direction: column; min-height: 100vh; }
  .header {
    background: var(--bg-card);
    border-bottom: 1px solid var(--border-default);
    padding: 0 24px;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky; top: 0; z-index: 100;
  }
  .header-brand {
    display: flex; align-items: center; gap: 12px;
    font-size: 17px; font-weight: 700; color: var(--text-primary);
  }
  .header-brand .logo {
    width: 32px; height: 32px;
    background: var(--orion-red);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    color: white; font-weight: 700; font-size: 14px;
  }
  .header-meta {
    font-size: 13px; color: var(--text-muted); font-weight: 500;
  }
  .main-content { flex: 1; padding: 24px; max-width: 1200px; margin: 0 auto; width: 100%; }

  /* ── Stats Row ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 12px;
    margin-bottom: 24px;
  }
  .stat-card {
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: var(--radius-lg);
    padding: 16px 20px;
    display: flex; flex-direction: column; gap: 4px;
    box-shadow: var(--shadow-card);
  }
  .stat-card .stat-label {
    font-size: 11px; font-weight: 600; text-transform: uppercase;
    letter-spacing: 0.05em; color: var(--text-faint);
  }
  .stat-card .stat-value {
    font-size: 28px; font-weight: 700; line-height: 1.2;
  }
  .stat-card .stat-sub {
    font-size: 12px; color: var(--text-muted);
  }

  /* ── Tier Section ── */
  .tier-section { margin-bottom: 20px; }
  .tier-header {
    display: flex; align-items: center; gap: 10px;
    padding: 10px 0; margin-bottom: 8px;
    border-bottom: 1px solid var(--border-light);
  }
  .tier-dot {
    width: 10px; height: 10px; border-radius: 50%; flex-shrink: 0;
  }
  .tier-label {
    font-size: 13px; font-weight: 700; text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  .tier-count {
    font-size: 12px; color: var(--text-muted); font-weight: 500;
    margin-left: auto;
  }

  /* ── Email Row Card ── */
  .email-card {
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: var(--radius-lg);
    padding: 16px 20px;
    margin-bottom: 8px;
    display: grid;
    grid-template-columns: 40px 1fr auto;
    align-items: center;
    gap: 16px;
    transition: border-color 200ms ease, box-shadow 200ms ease;
    cursor: pointer;
  }
  .email-card:hover {
    border-color: var(--border-default);
    box-shadow: var(--shadow-md);
  }
  .email-card.selected {
    border-color: var(--orion-red);
    box-shadow: 0 0 0 1px var(--orion-red);
  }
  .email-num {
    width: 36px; height: 36px;
    background: var(--bg-hover);
    border-radius: var(--radius-md);
    display: flex; align-items: center; justify-content: center;
    font-size: 14px; font-weight: 700; color: var(--text-primary);
  }
  .email-body { min-width: 0; }
  .email-sender {
    font-size: 14px; font-weight: 600; color: var(--text-primary);
    white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .email-subject {
    font-size: 13px; color: var(--text-secondary);
    white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .email-preview {
    font-size: 12px; color: var(--text-muted); margin-top: 2px;
    white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  }
  .email-meta {
    text-align: right; flex-shrink: 0;
  }
  .email-time {
    font-size: 12px; color: var(--text-faint); font-weight: 500;
  }
  .email-action {
    display: inline-block; margin-top: 4px;
    font-size: 11px; font-weight: 600; padding: 3px 8px;
    border-radius: var(--radius-sm); white-space: nowrap;
  }

  /* ── Priority Pills ── */
  .pill-urgent { background: var(--urgent-pill-bg); color: var(--urgent-pill-text); }
  .pill-important { background: var(--important-pill-bg); color: var(--important-pill-text); }
  .pill-delegate { background: var(--delegate-pill-bg); color: var(--delegate-pill-text); }
  .pill-defer { background: var(--defer-pill-bg); color: var(--defer-pill-text); }
  .pill-fyi { background: var(--fyi-pill-bg); color: var(--fyi-pill-text); }

  /* ── Action Items ── */
  .action-items {
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: var(--radius-lg);
    padding: 20px;
    margin-bottom: 24px;
    box-shadow: var(--shadow-card);
  }
  .action-items h3 {
    font-size: 14px; font-weight: 700; margin-bottom: 12px;
    color: var(--text-primary);
  }
  .action-item {
    display: flex; align-items: flex-start; gap: 10px;
    padding: 8px 0;
    border-bottom: 1px solid var(--border-light);
    font-size: 13px; color: var(--text-secondary);
  }
  .action-item:last-child { border-bottom: none; }
  .action-item input[type="checkbox"] {
    accent-color: var(--orion-red);
    margin-top: 2px; flex-shrink: 0;
  }

  /* ── Draft Preview Panel ── */
  .draft-panel {
    background: var(--bg-card);
    border: 1px solid var(--border-default);
    border-left: 3px solid var(--orion-red);
    border-radius: var(--radius-md);
    padding: 16px 20px;
    margin-top: 8px;
  }
  .draft-panel .draft-header {
    font-size: 12px; font-weight: 600; color: var(--orion-red);
    text-transform: uppercase; letter-spacing: 0.05em;
    margin-bottom: 8px;
  }
  .draft-panel .draft-body {
    font-size: 14px; color: var(--text-secondary); line-height: 1.6;
  }

  /* ── Primary Button ── */
  .btn-primary {
    background: var(--orion-red);
    color: #FFFFFF;
    border: none;
    border-radius: var(--radius-pill);
    padding: 10px 32px;
    font-size: 14px; font-weight: 600;
    cursor: pointer;
    box-shadow: var(--shadow-primary);
    transition: all 200ms ease;
  }
  .btn-primary:hover { opacity: 0.9; }
  .btn-primary:disabled {
    background: #E5E7EB; color: #9CA3AF;
    box-shadow: none; cursor: default;
  }

  /* ── Secondary Button ── */
  .btn-secondary {
    background: none;
    border: 1px solid var(--border-default);
    border-radius: var(--radius-md);
    padding: 8px 16px;
    font-size: 13px; font-weight: 500;
    color: var(--text-secondary);
    cursor: pointer;
    transition: background 150ms ease;
  }
  .btn-secondary:hover { background: var(--bg-hover); }

  /* ── Filter Bar ── */
  .filter-bar {
    background: var(--bg-card);
    border-bottom: 1px solid var(--border-default);
    padding: 12px 24px;
    display: flex; align-items: center; gap: 8px;
    flex-wrap: wrap;
  }
  .filter-chip {
    padding: 6px 14px;
    font-size: 13px; font-weight: 500;
    border: 1px solid var(--border-default);
    border-radius: var(--radius-md);
    background: var(--bg-card);
    color: var(--text-secondary);
    cursor: pointer;
    transition: all 150ms ease;
  }
  .filter-chip:hover { background: var(--bg-hover); }
  .filter-chip.active {
    background: var(--orion-red);
    color: white;
    border-color: var(--orion-red);
  }

  /* ── Responsive ── */
  @media (max-width: 768px) {
    .header { padding: 0 12px; height: 56px; }
    .main-content { padding: 12px; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
    .email-card {
      grid-template-columns: 32px 1fr;
      gap: 10px; padding: 12px 14px;
    }
    .email-meta { display: none; }
    .email-num { width: 28px; height: 28px; font-size: 12px; }
  }

  /* ── Animations ── */
  @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes slideDown { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }
  .fade-in { animation: fadeIn 300ms ease forwards; }
  .tier-section { animation: fadeIn 400ms ease forwards; }
  .email-card { animation: fadeIn 300ms ease forwards; }
</style>
```

## Dashboard HTML Structure

Use this skeleton when generating the interactive dashboard:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Inbox Triage -- [Date]</title>
  <!-- Paste the full <style> block from above -->
</head>
<body>
<div class="dashboard">

  <!-- Header -->
  <div class="header">
    <div class="header-brand">
      <div class="logo">O</div>
      <span>Orion Inbox</span>
    </div>
    <div class="header-meta">[Date] &middot; [N] emails</div>
  </div>

  <!-- Filter Bar -->
  <div class="filter-bar">
    <button class="filter-chip active" onclick="filterTier('all')">All</button>
    <button class="filter-chip" onclick="filterTier('urgent')">Urgent</button>
    <button class="filter-chip" onclick="filterTier('important')">Important</button>
    <button class="filter-chip" onclick="filterTier('delegate')">Delegate</button>
    <button class="filter-chip" onclick="filterTier('defer')">Defer</button>
    <button class="filter-chip" onclick="filterTier('fyi')">FYI</button>
  </div>

  <div class="main-content">

    <!-- Stats Row -->
    <div class="stats-row">
      <!-- One stat-card per tier, plus a total card -->
    </div>

    <!-- Action Items (extracted from emails) -->
    <div class="action-items">
      <h3>Action Items</h3>
      <!-- Checkboxes for each extracted action -->
    </div>

    <!-- Tier Sections -->
    <!-- One .tier-section per priority tier with .email-card rows -->

  </div>
</div>

<script>
  // ── Interactive Filtering ──
  function filterTier(tier) {
    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
    event.target.classList.add('active');
    document.querySelectorAll('.tier-section').forEach(s => {
      s.style.display = (tier === 'all' || s.dataset.tier === tier) ? '' : 'none';
    });
  }

  // ── Card Selection (for batch actions) ──
  document.querySelectorAll('.email-card').forEach(card => {
    card.addEventListener('click', () => card.classList.toggle('selected'));
  });

  // ── Staggered fade-in ──
  document.querySelectorAll('.email-card').forEach((card, i) => {
    card.style.animationDelay = (i * 50) + 'ms';
  });
</script>
</body>
</html>
```

## Mapping Priority Tiers to Orion Colors

| Tier | Dot Color | Pill Class | Stat Accent |
|------|-----------|------------|-------------|
| URGENT | `var(--urgent-dot)` #EF4444 | `.pill-urgent` | `color: var(--urgent-text)` |
| IMPORTANT | `var(--important-dot)` #F59E0B | `.pill-important` | `color: var(--important-text)` |
| DELEGATE | `var(--delegate-dot)` #8B5CF6 | `.pill-delegate` | `color: var(--delegate-text)` |
| DEFER | `var(--defer-dot)` #3B82F6 | `.pill-defer` | `color: var(--defer-text)` |
| FYI | `var(--fyi-dot)` #9CA3AF | `.pill-fyi` | `color: var(--fyi-text)` |
