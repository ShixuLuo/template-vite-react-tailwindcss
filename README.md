# Template for Vite + React + Tailwind CSS + Vitest + React Router + React Cosmos

## tl;dr

```bash
npx degit shixuluo/template-vite-react-tailwindcss
```

## Step by step

### Vite

```bash
yarn create vite .
```

Choose `react` from cli.

### Tailwind CSS

```bash
yarn add tailwindcss @tailwindcss/vite
```

Modify `vite.config.ts`:

```typescript
// vite.config.ts

+ import tailwindcss from '@tailwindcss/vite';

export default defineConfig({
  plugins: [
+    tailwindcss(),
  ],
})
```

Also remember to import tailwindcss in one of your CSS file.

### Vitest

```bash
yarn add -D vitest
```

Modify `package.json`
```JSON
"scripts": {
   "test": "vitest"
}
```

```bash
yarn add -D jsdom
```

Modify `vite.config.ts`
```typescript
export default defineConfig({
  test: {
    environment: 'jsdom',
  },
  ...
})
```

```bash
yarn add -D @testing-library/react @testing-library/jest-dom @testing-library/user-event
```

Create `tests/setup.ts`
```typescript
import { expect, afterEach } from 'vitest';
import { cleanup } from '@testing-library/react';
import * as matchers from "@testing-library/jest-dom/matchers";

expect.extend(matchers);

afterEach(() => {
  cleanup();
});
```

Modify `vite.config.ts`
```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
+   globals: true,
    environment: 'jsdom',
+   setupFiles: './tests/setup.ts',
  },
});
```

### React Router

```bash
yarn add react-router
```

### React Cosmos

```bash
yarn add --dev react-cosmos react-cosmos-plugin-vite
```

Create `cosmos.config.json`.
```JSON
{
    "plugins": ["react-cosmos-plugin-vite"]
}
```

Modify 'package.json'.
```JSON
"script": {
    "cosmos": "cosmos",
    "cosmos-export": "cosmos-export"
}
```
