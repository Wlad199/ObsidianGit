
#gulp
[Gulp](https://gulpjs.com/docs/en/getting-started/quick-start) | [npm](https://www.npmjs.com/)

## Настройка 
1. Установить Node.js (node -v)
2. Установить npm: npm init (npm -v)
3. Установить Gulp: npm i gulp-cli -g
4. npm i gulp -D    (-D === --save-dev). -D это установка для режима разработчика
5. Создать gulpfile.js (В этом файле будут задачи для галпа)
6. Создать структуру папок
7. В gulpfile.js пишем:  const { src, dest } = require('gulp');
8. Устанавливаем 2 плагина для scss: npm i gulp-sass sass -D
9. В gulpfile.js подключаем плагины:  const scss = require('gulp-sass')(require('sass'));
10. Создаем функцию для стилей:
function styles() {
	return src('src/scss/style.scss')  // Файл, который нужно взять
	.pipe(scss())											// Обращаемся к константе из пункта 9
	.pipe(dest('src/css'))						// Куда сохранить готовый файл
}
11. Экспортировать функцию: exports.styles = styles;

#### Кратко
1. Установка чарез npm
2. В gulpfile.js подключаем плагин путем создания константы
3. Создаем функцию. Например:
	function scripts() {
	return src('src/js/main.js')
		.pipe(concat('main.min.js'))
		.pipe(uglify())
		.pipe(dest('src/js')
	})
4. Экспортируем функцию


## Плагины:
Слежение за файлами watch идет в комплекте с Gulp

| `npm i gulp-sass sass -D`      | scss                                                                  |
| ------------------------------ | --------------------------------------------------------------------- |
| `npm i gulp-concat -D`         | Переименование файлов                                                 |
| `npm i gulp-uglify-es -D`      | Для js файлов                                                         |
| `npm i browser-sync -D`        | Обновление страницы                                                   |
| `npm i gulp-autoprefixer -D`   | Преффиксы                                                             |
| `npm i gulp-clean -D`          | Удаление файлов                                                       |
| `npm i gulp-avif -D`           | Картинки Avif                                                         |
| `npm i gulp-webp -D`           | Картинки Webp                                                         |
| `npm i gulp-imagemin@7.1.0 -D` | Картинки сжатие                                                       |
| `npm i gulp-cashed -D`         | Кэш                                                                   |
| `npm i gulp-newer -D`          | Кэш альтернатива - newer (чтобы не комполировать картинки каждый раз) |
| `npm i gulp-svg-sprite -D`     | Спрайты                                                               |
| `npm i gulp-ttf2woff2 -D`      | Шрифты                                                                |
| `npm i gulp-fonter -D`         | Конвертация в woff2                                                   |
| `npm i gulp-include -D`        | Сборка HTML частей		                                                  |
