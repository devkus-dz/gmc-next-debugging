# React Debugging Checkpoint

## Overview

This project was debugged using **React Developer Tools** to inspect the component tree, verify state and props, and identify incorrect behaviors. The following issues were found and resolved.

![eslint warnings](/eslint-warnings.JPG)

### Debugging Steps :

- Installed React Developer Tools extension and inspect component hierarchy.

- Checked props passing and state values.

- Identify incorrect prop naming in different components.

- Verify functionality after bug fixes.

## Bug Fixed

### 1. `PassingProps.js`

**Issue:**

- Unused useEffect hook import
- PurchaseSummary component has an incorrect Prop names.

**Fix:**
1- Removed the unused import useEffect hook.
2- Ensured that the prop names in the parent matches the one used in the child component `<PurchaseSummary>`.

**Before:**

```jsx
<PurchaseSummary level={purchaseLevel} liked={likeStatus} />
```

**After:**

```jsx
<PurchaseSummary
  purchaseLevel={purchaseLevel}
  purchaseLikability={likeStatus}
/>
```

### 2. `HookSideEffects.js`

**Issue:**

- useCallback was missing a dependency array, causing repeated and unnecessary re-renders.

**Fix:**

- Added the dependency array to ensure the side effect runs only when necessary.

**Before:**

```jsx
const track = useCallback((analyticsEvent) => {
  setEventBatch((batch) => [...batch, analyticsEvent]);
});
```

**After:**

```jsx
const track = useCallback((analyticsEvent) => {
  setEventBatch((batch) => [...batch, analyticsEvent]);
}, []);
```
