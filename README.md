# 📝 Todo App

A minimalist **Vue 3** + **TypeScript** Todo application styled with **Pico CSS**. This app lets users manage tasks with a clean interface, including adding, completing, filtering, and deleting tasks.

## ✨ Features

- ➕ Add new tasks  
- ✅ Mark tasks as completed/incomplete  
- 🔍 Filter tasks by status (All / Done / Todo)  
- ❌ Remove tasks  
- 📊 Real-time completion tracker  

## 🛠️ Tech Stack

| Tool          | Purpose                        |
|---------------|--------------------------------|
| [Vue 3](https://vuejs.org/) | JavaScript framework         |
| [TypeScript](https://www.typescriptlang.org/) | Static typing             |
| [Pico CSS](https://picocss.com/) | Minimalist styling         |
| [Vite](https://vitejs.dev/) | Build tool + dev server     |
| [pnpm](https://pnpm.io/)   | Fast, efficient package manager |

## 📁 Project Structure

```
todo-app/
├── src/
│   ├── assets/                
│   ├── components/            
│   │   ├── FilterButton.vue
│   │   ├── TaskForm.vue
│   │   └── TaskList.vue
│   ├── App.vue               
│   ├── main.ts                
│   ├── style.css
│   ├── types.ts
│   └── vite-env.d.ts
├── index.html
├── package.json
├── pnpm-lock.yaml
├── vite.config.ts
├── tsconfig*.json
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v16+)
- [pnpm](https://pnpm.io/)

### Installation

```bash
# Clone the repository
git clone https://github.com/locturui/todo-app.git
cd todo-app

# Install dependencies
pnpm install

# Run in development mode
pnpm dev
```

Then open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for Production

```bash
pnpm build
```

## 🧪 Scripts

| Script        | Description                      |
|---------------|----------------------------------|
| `pnpm dev`    | Starts the development server    |
| `pnpm build`  | Builds the app for production    |
| `pnpm preview`| Serves the built app locally     |

## ✅ TODO

- [ ] Add localStorage persistence  
- [ ] Drag-and-drop task reordering  
- [ ] Deploy to Vercel/Netlify  

## 📄 License

[MIT](LICENSE)
