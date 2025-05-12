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
