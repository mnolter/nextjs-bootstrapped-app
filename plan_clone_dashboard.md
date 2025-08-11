# Plan to Clone Dashboard Application from Screenshots

## Objective
Replicate the dashboard UI shown in the screenshots using the existing Next.js 15+ TypeScript project with shadcn/ui components, Radix UI, and Tailwind CSS.

## Steps

1. Create a new page in `src/app/dashboard/page.tsx` to serve as the dashboard entry point.
2. Build reusable UI components for:
   - Policies per carrier table
   - Applicants per carrier table
   - Policies per US state map chart
   - Policies per status pie chart
   - Agents leaderboard table
   - Policies submitted each month line chart
   - Policies by product type pie chart
3. Use existing shadcn/ui components for layout, cards, tables, buttons, and filters.
4. Use Recharts or similar charting library (already in dependencies) for charts.
5. Implement Tailwind CSS styling to match the screenshots (light theme, spacing, typography).
6. Add buttons for "Refresh" and "Save as PDF" with placeholder handlers.
7. Ensure mobile responsiveness and accessibility.
8. Prepare the codebase for easy future modifications and feature additions.

## Deliverables
- Fully functional dashboard page replicating the screenshots.
- Modular components for each dashboard section.
- Clean, maintainable TypeScript and React code.
- Tailwind CSS styling consistent with the existing project.
