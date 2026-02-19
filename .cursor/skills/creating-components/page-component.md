# Page Component

Page components live in `src/app/` and render a main component from `src/components/[page-name]/`.

**With i18n:** `src/app/[locale]/[route-name]/page.tsx`
**Without i18n:** `src/app/[route-name]/page.tsx`

The page file exports `[RouteNamePage]` as a named export. Keep logic out of page files; load data and delegate rendering to `src/components/[page-name]/[PageName].tsx`.

## Example

```
src/app/[locale]/about-us/page.tsx   →  exports AboutUsPage
src/components/about-us/AboutUs.tsx  →  main page component
```

```tsx
// src/app/[locale]/about-us/page.tsx
export const AboutUsPage: React.FC = () => (
  <AboutUs />
);
```
