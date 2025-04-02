### Деплой проекта на Гит
#git #vue/deploy
- Инициализировать, закоммитить и запушить в ветку Main:
	`git init`
	`git commit -m "first commit"`
	`git branch -M main`
	`git remote add origin https://github.com/Wlad199/testVue.git`
	`git push -u origin main`
- Перейти в ветку gh-pages: 
	`git checkout -b gh-pages`
- Открыть файл vite.config.js и добавить в defineConfig название проекта из гит:
	`base: '/testVue/'`
- Забилдить:  
	`npm run build`
- Добавить папку дист:  
	`git add dist -f`   
	`git commit -m dist`   
	`git subtree push --prefix dist origin gh-pages` 
- Зайти в проект на гитхаб, вкладка actions и дождаться деплоя
