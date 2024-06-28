# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Basic Setup - Creating a React and Vite project

### Creating project file

npm create vite@latest
Give a file_name
Select React framework and JavaScript variant

### Installing dependencies

```
cd file_name
file_name > npm install
file_name > npm install -D tailwindcss postcss autoprefixer
file_name > npx tailwindcss init -p
```

### Adding tailwind configuration

Go into tailwind config file and add content:
content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"]

### Add Tailwind Components inside index.css file

@tailwind base;
@tailwind components;
@tailwind utilities;

### Now you are ready to build using React + Vite + Tailwind !
