<h1>Vite HTML</h1>

- npm install

- npm run dev

- npm run build

- npm run preview

<blockquote>Important rule! Do not delete the <code>second.html</code> file until the new next file of the multi-page site is created.</blockquote>

 - если нужно отключить минификацию, вставляем строку <code>minify: false</code> в vite.config.js. Тогда не будут минифицироваться изображения и style.css, script.js
  ```
  build: {
    rollupOptions: {
      input: sync('src/**/*.html'.replace(/\\/g, '/')),
      output: {
        assetFileNames: (assetInfo) => {
          let extType = assetInfo.name
          if (/css/.test(extType)) { extType = 'assets/css' }
          return assetInfo.originalFileName ?? `${extType}/[name][extname]`
        },
        chunkFileNames: 'assets/js/[name].js',
        entryFileNames: 'assets/js/[name].js',
      },
    },
    assetsInlineLimit: 0,
    emptyOutDir: true,
    outDir: '../dist',
    minify: false, // Отключаем минификацию всех файлов (добавить строку в конфиг, если нужно)
  },
  root: 'src',
  base: '',
  ```