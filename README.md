# npm run dev vs npm run build - 06/11/25

> A comprehensive guide to understanding the difference between development and production builds

---

## 🎯 Quick Answer

- **`npm run dev`** → Development mode (while coding)
- **`npm run build`** → Production build (before deployment)

---

## 🛠️ npm run dev (Development Mode)

### What it does:
- Starts a **local development server**
- Enables **hot reload** (changes appear instantly without refresh)
- Includes **source maps** for easier debugging
- Shows **detailed error messages**
- **NOT optimized** for performance
- Code is **NOT minified**

### When to use:
- ✅ While actively coding
- ✅ Testing features locally
- ✅ Debugging issues
- ✅ Day-to-day development

### What happens:
```bash
npm run dev
# or
npm start  # (in some projects)

→ Starts server at http://localhost:3000
→ Watches for file changes
→ Auto-reloads browser when you save
→ Fast rebuild times
```

### Characteristics:
- **Fast startup** ⚡
- **Large file sizes** (unoptimized)
- **Readable code** (for debugging)
- **Helpful warnings** and errors
- **Development-only features** enabled

---

## 🚀 npm run build (Production Build)

### What it does:
- Creates **optimized production files**
- **Minifies** code (removes whitespace, shortens variable names)
- **Compresses** assets
- **Tree-shakes** unused code (removes dead code)
- **Optimizes images**
- Creates static files ready for deployment
- **NO hot reload** (it's not a server)

### When to use:
- ✅ Before deploying to production
- ✅ Testing production performance locally
- ✅ Checking final bundle size
- ✅ Before pushing to hosting (Vercel, Netlify, etc.)

### What happens:
```bash
npm run build

→ Creates optimized files in /build or /dist or /.next folder
→ Minifies JavaScript, CSS, HTML
→ Optimizes images
→ Generates production-ready bundle
→ Takes longer than dev (30s - 2min depending on project size)
```

### Output:
```
/build  (Create React App)
/dist   (Vite)
/.next  (Next.js)
/out    (Next.js static export)
```

### Characteristics:
- **Slower build time** 🐢 (but only done once)
- **Small file sizes** (optimized for web)
- **Unreadable code** (minified)
- **Best performance**
- **Production-only features** (like SSR in Next.js)

---

## 📊 Side-by-Side Comparison

| Feature | `npm run dev` | `npm run build` |
|---------|--------------|-----------------|
| **Purpose** | Local development | Production deployment |
| **Speed** | Fast startup | Slow build, fast runtime |
| **File Size** | Large (~2-5MB+) | Small (~200KB-1MB) |
| **Code** | Readable | Minified |
| **Hot Reload** | ✅ Yes | ❌ No |
| **Optimization** | ❌ None | ✅ Full |
| **Error Messages** | Detailed | Minimal |
| **Source Maps** | ✅ Yes | Optional |

---

## 🔄 Typical Workflow

```bash
# 1. Start development
npm run dev
# Code, code, code... save files, see changes instantly

# 2. When feature is complete
git add .
git commit -m "feat(component): add new feature"

# 3. Before deploying (or to test production build)
npm run build

# 4. (Optional) Test production build locally
npm start  # In Next.js, or use a static server
# or
npx serve -s build  # For Create React App

# 5. Deploy to production
git push origin main  # If using Vercel/Netlify auto-deploy
# or upload the /build folder manually
```

---

## 🎨 Framework-Specific Commands

### Create React App:
```bash
npm start          # Development mode (port 3000)
npm run build      # Production build → /build folder
npx serve -s build # Serve production build locally
```

### Next.js:
```bash
npm run dev        # Development mode (port 3000)
npm run build      # Production build → /.next folder
npm start          # Serve production build (after npm run build)
```

### Vite:
```bash
npm run dev        # Development mode (port 5173)
npm run build      # Production build → /dist folder
npm run preview    # Preview production build locally
```

---

## ⚡ Key Differences in Next.js

Next.js is special because `npm run build` does more:

```bash
# Development
npm run dev
→ Fast refresh
→ Detailed errors
→ Server-side rendering on-demand

# Production
npm run build
→ Pre-renders pages (SSG)
→ Optimizes images
→ Creates optimized bundles
→ Generates static assets

npm start  # After build
→ Serves the optimized build
→ Faster than dev mode
→ What users actually experience
```

---

## 🚨 Common Mistakes

### ❌ Don't:
```bash
# Deploying dev mode to production
npm run dev  # and leaving it running on server

# Never running build before deployment
git push  # without testing npm run build first
```

### ✅ Do:
```bash
# Always test build locally
npm run build
npm start  # or preview command

# Then deploy
git push origin main
```

---

## 💡 Pro Tips

### 1. Run `npm run build` regularly during development to:
   - Catch production-only errors early
   - Check bundle sizes
   - Ensure everything compiles

### 2. Check build output:
   ```bash
   npm run build
   
   # Look for warnings like:
   # "Bundle size exceeded 500KB"
   # "Unused dependencies detected"
   ```

### 3. Environment variables:
   - Dev: Uses `.env.development` or `.env.local`
   - Build: Uses `.env.production`

### 4. Testing production locally:
   ```bash
   npm run build
   npm start  # Next.js
   # or
   npx serve -s build  # React/Vite
   ```

---

## 🎯 Quick Decision Guide

### Use `npm run dev` when:
- 👨‍💻 You're coding
- 🐛 Debugging issues
- ⚡ Need instant feedback
- 🔥 Want hot reload

### Use `npm run build` when:
- 🚀 Ready to deploy
- 📦 Checking bundle size
- 🧪 Testing production behavior
- ✅ Before committing major changes

---

## 📚 TL;DR

**`dev`** = fast coding experience with hot reload

**`build`** = optimized files for production users

You'll use `dev` 99% of the time while coding, and `build` before every deployment! 🚀

---

## 🤝 Contributing

Found something unclear or have suggestions? Feel free to open an issue or PR!

---

<div align="center">

**Happy Coding! 💻**

</div>