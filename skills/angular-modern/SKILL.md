---
name: angular-modern
description: Modern Angular 18/19+ standards for high-speed agentic development. Enforces Single-File Standalone Components (SFC), Angular Signals, non-interactive CLI hygiene (NG_CLI_ANALYTICS=false), HMR dev server retention, and zero-slop UI tokens.
---

# Angular Modern (18/19+) Standards

Standard Operating Procedure for developing Angular applications with autonomous AI agents. Designed for token efficiency, fast HMR feedback, and modern single-file architecture.

---

## 1. CLI Non-Interactive Hygiene (No Hangs)

Angular CLI prompts for anonymous analytics by default, which hangs autonomous agents running in non-interactive shells.

- **Mandatory Environment Variable**:
  Always set analytics to false before running CLI commands:
  ```powershell
  $env:NG_CLI_ANALYTICS="false"
  ```
- **New Project Scaffolding**:
  Always include `--defaults` and disable SSR/git during initial generation:
  ```powershell
  npx -y @angular/cli@19 new <app-name> --routing --style=css --ssr=false --skip-git --defaults
  ```

---

## 2. Single-File Standalone Components (SFC) for Spikes

Traditional Angular splits every component into 4 separate files (`.ts`, `.html`, `.css`, `.spec.ts`). For AI agents, this quadruples file-reading roundtrips and token burn.

### The Lean Single-File Pattern:
Combine template and styles directly into the TypeScript file using inline definitions:

```typescript
import { Component, signal, input, output } from '@angular/core';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-metric-card',
  standalone: true,
  imports: [CommonModule],
  template: `
    <div class="metric-card">
      <div class="header">
        <span class="label">{{ label() }}</span>
        <button class="action-btn" (click)="onRefresh.emit()">Refresh</button>
      </div>
      <div class="value">{{ value() }}</div>
    </div>
  `,
  styles: [`
    .metric-card {
      background: var(--bg-surface, #1e293b);
      border: 1px solid var(--border-subtle, #334155);
      border-radius: 0.75rem;
      padding: 1.25rem;
    }
    .header { display: flex; justify-content: space-between; align-items: center; }
    .label { font-size: 0.875rem; color: #94a3b8; }
    .value { font-size: 1.75rem; font-weight: 700; color: #f8fafc; margin-top: 0.5rem; }
    .action-btn { background: #3b82f6; color: white; border: none; padding: 0.25rem 0.75rem; border-radius: 0.375rem; cursor: pointer; }
  `]
})
export class MetricCardComponent {
  label = input.required<string>();
  value = input.required<string | number>();
  onRefresh = output<void>();
}
```

### Benefits:
- Agent edits template, logic, and style in a **single atomic `replace_file_content`** call.
- Eliminates context confusion across multiple open tabs.

---

## 3. Modern State: Angular Signals over RxJS Boilerplate

Replace verbose `BehaviorSubject`, `combineLatest`, and manual `unsubscribe()` with native Angular Signals:

```typescript
import { Component, signal, computed, inject } from '@angular/core';
import { HttpClient } from '@angular/common/http';

export class DashboardComponent {
  private http = inject(HttpClient);
  
  // State Signals
  items = signal<Item[]>([]);
  searchQuery = signal<string>('');
  
  // Derived State (Auto-computes with 0 subscription leaks)
  filteredItems = computed(() => {
    const q = this.searchQuery().toLowerCase();
    return this.items().filter(i => i.title.toLowerCase().includes(q));
  });

  // Action
  loadItems() {
    this.http.get<Item[]>('/api/items').subscribe(data => this.items.set(data));
  }
}
```

---

## 4. Dev Server & HMR Retention (Strict Ban on Build Loops)

**NEVER** abandon `ng serve` to run `npm run build` + custom node static servers during UI development loops! Rebuilding the entire application on every CSS edit wastes 10–20 seconds and hundreds of tokens per turn.

- **Start Dev Server in Background**:
  ```powershell
  $env:NG_CLI_ANALYTICS="false"; npx ng serve --port 4200 --host 0.0.0.0
  ```
- **HMR Behavior**:
  With `ng serve`, file edits are pushed to the browser in <200ms without restarting the process.
- **Pre-Flight Port Cleanup**:
  ```powershell
  Get-NetTCPConnection -LocalPort 4200 -ErrorAction SilentlyContinue | ForEach-Object { Stop-Process -Id $_.OwningProcess -Force }
  ```

---

---

## 5. Zero-Leak Frontend Security & API Proxying
- **Strict Ban on Client Secrets**: Never store API keys, tokens, or private credentials inside Angular client-side code (`environment.ts`, services, components).
- **Backend Proxy Mandate**: All requests requiring external AI credentials (e.g. Gemini, OpenAI, GitHub tokens) must route through local backend endpoints (`/api/...`). The client only communicates with the trusted backend.

## 6. Summary Checklist for AI Agents
1. Did you set `$env:NG_CLI_ANALYTICS="false"` before calling CLI?
2. Did you use Single-File Standalone Components (`template: ...`) for fast iteration?
3. Did you use `signal()` and `computed()` instead of heavy RxJS subjects?
4. Did you keep `ng serve` running with HMR instead of triggering full production builds?
