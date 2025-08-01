## Main Dashboard Page

```
app/dashboard-main/page.tsx
├── components/dash-summary.tsx
├── components/dash-quick-actions.tsx
└── components/dash-downloads.tsx
```

## Shareholder Support Page

```
app/shareholder-support/page.tsx
├── components/shareholder-search.tsx
└── components/shareholder-table.tsx
    ├── components/view-shareholder-btn.tsx
    └── ...
```

**Sub pages**

```
app/shareholder/[id]/page.tsx
├── components/shareholder-wrapper.tsx
    ├── components/shareholder-data.tsx
    ├── components/edit-shareholder-btn.tsx
    ├── components/edit-shareholder-sheet.tsx
        ├── components/edit-shareholder-form.tsx
            └── components/submit-shareholder-changes-btn.tsx
    ├── components/view-shareholder-issue-log-btn.tsx
    └── components/issue-log-sheet.tsx
        ├── components/issue-log-wrapper.tsx
            └── components/issue-log-card.tsx
        └── components/issue-log-form.tsx
└── components/shareholder-application-wrapper.tsx
    ├── components/application-data.tsx
    ├── components/edit-application-btn.tsx
    └── components/proxy-application-btn.tsx
```

## Data Management (Benefits and Lottery Pages Combined)

```
app/data-management/page.tsx
├── components/benefit-data-search.tsx
    ├── components/data-dropdown.tsx
    ├── components/data-checkbox.tsx
    ├── components/data-add-btn.tsx
    └── components/data-clear-btn.tsx
└── components/data-table.tsx
└── components/download-data-results.tsx
```
