# App with components

```
app/
├── main-dashboard/page.tsx
├── cs-dashboard/page.tsx           // <UnifiedDashboard {...csConfig} />
├── int-dashboard/page.tsx          // <UnifiedDashboard {...intConfig} />
├── pr-dashboard/page.tsx           // <UnifiedDashboard {...prConfig} />
├── ss-dashboard/page.tsx           // <UnifiedDashboard {...ssConfig} />
├── lottery/[application-period-id]/[lottery-id]/page.tsx       // Detail view (if needed)
└── shareholder/[id]/page.tsx       // Detail view (if needed)

components/ui/
├── unified-dashboard.tsx           // The main component
├── data-table.tsx                  // Generic table
├── data-filter.tsx                 // Generic filters
├── action-button.tsx               // Generic actions
├── download-data-btn.tsx           // Generic download
├── upload-data-btn.tsx             // Generic upload
├── form-sheet.tsx                  // Generic modals
├── loading-table.tsx               // Generic loading
└── error-boundary.tsx              // Generic Error Boundary
```

## [Unified Dash](./unified_architecture_rationale.md)
