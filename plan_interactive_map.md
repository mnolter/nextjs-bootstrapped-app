# Detailed Implementation Plan for Interactive US Map

## 1. Overview
We will replace the current static "Policies per US state" representation with an interactive US map. This interactive map will use a free, open-source library to render US state boundaries, support hover and click interactions, and display placeholder data for policies. The design will follow a modern blue/white theme with smooth transitions and clear typography.

## 2. Dependency Installation
- **Library:** We will use [react-simple-maps](https://www.react-simple-maps.io) for rendering the map.
- **Installation Command:**  
  Run the following command in your project root:
  ```bash
  npm install react-simple-maps
  ```
- Verify that the dependency is added to your package.json.

## 3. New Component: USMap
Create a new file: `src/components/USMap.tsx` with the following changes and features:

### File: src/components/USMap.tsx
- **Imports:**
  - Import React hooks (`useState`, `useEffect`).
  - Import `ComposableMap`, `Geographies`, and `Geography` from `react-simple-maps`.
- **Geography Data:**
  - Use the TopoJSON data URL:  
    ```typescript
    const geoUrl = "https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json";
    ```
- **Component State & Handlers:**
  - Create state variables to store the currently hovered state (`hoveredState`) and any error state.
  - Implement `onMouseEnter` to update `hoveredState` with the state's name.
  - Add an `onMouseLeave` to clear the hovered state.
  - Use an `onClick` handler that (for now) logs or displays the selected state (in a future iteration this could trigger a modal or side panel).
- **Styling & Transitions:**
  - Use Tailwind CSS classes to provide smooth transitions (e.g., `transition-colors`), hover effects (e.g., `hover:fill-blue-100`), and a modern blue/white theme.
- **Error Handling:**
  - Wrap fetch of TopoJSON data in error handling logic; if loading fails, show a user-friendly error message within the map area.
- **Accessibility:**
  - Add `aria-label` for each interactive state.

#### Example Skeleton Code:
```typescript
import React, { useState } from "react";
import {
  ComposableMap,
  Geographies,
  Geography,
} from "react-simple-maps";

const geoUrl = "https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json";

const USMap: React.FC = () => {
  const [hoveredState, setHoveredState] = useState<string | null>(null);
  const [error, setError] = useState<string | null>(null);

  return (
    <div className="relative">
      {error && (
        <div className="p-4 bg-red-100 text-red-600 text-center rounded">
          Failed to load map data.
        </div>
      )}
      <ComposableMap
        projection="geoAlbersUsa"
        data-testid="us-map"
        className="w-full h-full"
      >
        <Geographies
          geography={geoUrl}
          onError={(err) => {
            console.error("Error loading map", err);
            setError("Error loading map data.");
          }}
        >
          {({ geographies }) =>
            geographies.map((geo) => {
              const stateName = geo.properties.name;
              return (
                <Geography
                  key={geo.rsmKey}
                  geography={geo}
                  onMouseEnter={() => setHoveredState(stateName)}
                  onMouseLeave={() => setHoveredState(null)}
                  onClick={() => alert(`Selected state: ${stateName}`)}
                  style={{
                    default: {
                      fill: "#eff6ff",
                      outline: "none",
                      transition: "fill 0.3s ease",
                    },
                    hover: {
                      fill: "#3b82f6",
                      outline: "none",
                    },
                    pressed: {
                      fill: "#2563eb",
                      outline: "none",
                    },
                  }}
                  aria-label={`US state ${stateName}`}
                />
              );
            })
          }
        </Geographies>
      </ComposableMap>
      {hoveredState && (
        <div className="absolute bottom-2 left-2 bg-white p-2 rounded shadow text-sm text-blue-600">
          {hoveredState}
        </div>
      )}
    </div>
  );
};

export default USMap;
```

## 4. Updating the Dashboard (src/app/page.tsx)
- **Import and Integrate USMap Component:**
  - In the "Policies per US state" card, remove the current static placeholder and import the new `USMap` component.
  - Replace the old static map `<div className="h-64 bg-gray-50 ...">...</div>` with `<USMap />`.
- **Code Changes:**
  - At the top of the file, add:
    ```typescript
    import USMap from "@/components/USMap";
    ```
  - In the corresponding card section, update the JSX:
    ```tsx
    <Card className="bg-white">
      <CardHeader>
        <CardTitle className="text-lg">Policies per US state (Top 10)</CardTitle>
        <CardDescription>Where your clients are located</CardDescription>
      </CardHeader>
      <CardContent>
        <div className="h-64">
          <USMap />
        </div>
      </CardContent>
    </Card>
    ```

## 5. UI/UX Considerations
- Ensure the map is fully responsive and scales cleanly on different screen sizes.
- Use modern UI techniques with blue and white tones and subtle transitions.
- Provide clear visual feedback on hover (color transition effects) and focus states for accessibility.
- The tooltip displaying the hovered state should be concise and unobtrusive.

## 6. Error Handling and Best Practices
- Use try/catch or inline error callbacks (as shown in the `onError` prop of Geographies) to handle and report any loading issues.
- Include accessibility features using `aria-label` attributes.
- Use Tailwind utility classes for consistency in colors and spacing.
- Comment critical code blocks to explain functionality and possible extension points (e.g., future integration with Supabase data).

## 7. Testing and Verification
- Run the application using `npm run dev` (or equivalent) and verify the interactive map renders correctly.
- Use browser-based testing: Hover over states to confirm the tooltip appears, click a state to confirm the alert (or debug output).
- Check the network tab in the browser for successful fetching of the TopoJSON file.
- Validate that error messages are displayed gracefully if the TopoJSON data fails to load.

## 8. Future Enhancements
- Integrate dynamic policy data from Supabase when available.
- Replace the alert on state click with a modal or side panel displaying detailed policy statistics.
- Refine the UI animations and transitions further based on user feedback.

---

**Summary:**
• Added dependency "react-simple-maps" to render a dynamic interactive US map.  
• Created a new component, `USMap.tsx`, which loads US states from TopoJSON and shows hover and click effects.  
• Updated `src/app/page.tsx` to replace the static map placeholder with the interactive component.  
• Implemented error handling with user-friendly messages and accessibility via ARIA labels.  
• Ensured modern blue/white UI styling and smooth transitions using Tailwind CSS.  
• Future enhancement plans include integration with live policy data from Supabase and detailed state modals.
