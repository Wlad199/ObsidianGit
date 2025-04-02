### Деплой проекта на Гит
#git #vue/deploy #git/vue
- Инициализировать, закоммитить и запушить в ветку Main:
```bash
	git init
	git commit -m "first commit"
	git branch -M main
	git remote add origin https://github.com/Wlad199/testVue.git
	git push -u origin main
```
- Перейти в ветку gh-pages: 
```bash
	git checkout -b gh-pages
```
- Открыть файл vite.config.js и добавить в defineConfig название проекта из гит:
	`base: '/testVue/'`
- Забилдить:  
```bash
	npm run build
```
- Добавить папку дист:  
```bash
	git add dist -f
	git commit -m dist
	git subtree push --prefix dist origin gh-pages
```
- Зайти в проект на гитхаб, вкладка actions и дождаться деплоя

### Errors:
error: remote origin already exists.
для проверки:
```bash
git remote -v
```

для переназначения:
```bash
git remote set-url origin <NEW_GIT_URL_HERE>
```


