```markdown
# Detailed UI Enhancement Plan

This plan outlines the step-by-step changes to beautify the Dashboard UI in a modern, clean, and stylish way. We will update the main dashboard page, refine layout details, and ensure the USMap component’s visual details complement the new design. All modifications follow best practices regarding error handling, responsiveness, and modern design guidelines.

---

## File: src/app/page.tsx

1. **Remove Icon Library Dependencies**  
   - Delete the import of lucide-react icons:
     ```js
     // Remove this import
     // import { RefreshCw, Download, ChevronRight, Calendar, Filter } from "lucide-react";
     ```
   - Remove all usages of these icons from button components and replace them with text-based or simple Unicode symbols if necessary. For example, in header buttons, remove `<RefreshCw ... />` and `<Download ... />`.

2. **Update Button and Card Styles**  
   - Enhance buttons by adding additional Tailwind classes for shadows, rounded corners, and refined hover effects. For instance, update:
     ```jsx
     <Button className="bg-blue-600 hover:bg-blue-700 text-white shadow-md rounded-lg transition-all">
       Refresh
     </Button>
     ```
   - In areas where `<ChevronRight />` was used (in cards), replace with a simple text arrow:
     ```jsx
     <span className="text-gray-400 text-xl">→</span>
     ```
   - Adjust all Cards to include classes such as `shadow-md rounded-xl` and update inner spacing to ensure a modern clean layout.

3. **Typography and Spacing Improvements**  
   - Increase font sizes and weight where necessary (e.g., for headings and labels) using Tailwind classes like `text-lg`, `font-semibold`, and `mb-2` for consistent spacing.
   - Ensure that all call-to-action text is clear and well-aligned with the overall design.

4. **Filter & Date Range Section**  
   - In the filter section at the bottom, remove the `<Calendar>` and `<Filter>` icons. Replace the calendar icon with a text label ("Date Range") and the filter icon with the plain word ("Filters").
   - Update the select component styling with additional padding and a refined border style for a modern look.

---

## File: src/app/layout.tsx

1. **Global Layout Consistency**  
   - No major changes are required here; however, verify that the imported global CSS (`globals.css`) supports the updated shadow, spacing, and typography styles.
   - Ensure that the font (Inter) is consistently applied across all pages.

---

## File: src/components/USMap.tsx

1. **Modernize Legend and Tooltip Styling**  
   - Confirm that the tooltip and legend boxes have updated styling (e.g., `rounded-lg`, `shadow-lg`, and refined padding) to match the overall modern dashboard UI.
   - Ensure error message styling remains consistent with the new card style (using `bg-red-50 border-red-200 rounded-lg` with updated spacing).

2. **Error Handling and Hover States**  
   - Validate that all error handling (when map data fails to load) is properly visible and styled to be informative while matching the visual hierarchy.

---

## Additional Considerations

- **Global CSS Updates:**  
  - Optionally, review and enhance `src/app/globals.css` to include additional transition effects and refined color variables if needed.
- **Responsiveness:**  
  - Test the new UI across different screen sizes ensuring that spacing, card layouts, and typography remain consistent.
- **Alternative Icon Representations:**  
  - Use Unicode arrows (e.g., “→”) in place of removed icons, ensuring no external library icons are present.
- **Error Handling:**  
  - Maintain robust error alerts in all components, especially within USMap, with clear messaging and appropriate fallbacks.
- **Testing:**  
  - After modifications, run the application locally and verify via browser and relevant curl commands (if any API endpoints were indirectly affected).

---

## Summary

- Removed lucide-react icon dependencies from src/app/page.tsx and replaced all icon instances with text-based alternatives.  
- Enhanced button and card components with modern Tailwind classes (shadows, rounded corners, transitions).  
- Updated typography and spacing for clarity and modern aesthetics.  
- Refined the filter section to discard external icons and use clear text labels and styling.  
- Verified that USMap tooltip and legend styling now match the modern UI look while preserving error handling best practices.
