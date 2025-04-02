{
	"path-autocomplete.pathMappings": {
		"@img": "${folder}/src/img", // alias for /test
		"@scss": "${folder}/src/scss", // the absolute root folder is now /src,
		"@js": "${folder}/src/js" // the relative root folder is now /src
	},
	"editor.tabSize": 2,
	"editor.comments.insertSpace": false,
	"editor.detectIndentation": false,
	"editor.mouseWheelZoom": true,
	"editor.guides.bracketPairs": "active",
	"files.associations": {
		"*.kit": "html"
	},
	"workbench.startupEditor": "none",
	//"editor.hover.enabled": false,//!убрать всплывающие подсказки
	//"editor.quickSuggestionsDelay": 3000,
	//"editor.quickSuggestions": { // !Настройка подсказок
	//	"other": "on",
	//	"comments": "off",
	//	"strings": "off",
	//},
	"liveSassCompile.settings.generateMap": false,
	"liveSassCompile.settings.formats": [
		{
			"format": "expanded",
			"autoprefix": "last 5 version",
			"extensionName": ".min.css",
			"savePath": "css/"
		}
	],
	"explorer.confirmDelete": false,
	"[html]": {
		"editor.suggest.insertMode": "replace",
		"editor.defaultFormatter": "vscode.html-language-features"
	},
	"liveServer.settings.wait": 1,
	"liveServer.settings.showOnStatusbar": false,
	"liveServer.settings.CustomBrowser": "chrome",
	"liveSassCompile.settings.showOutputWindowOn": "Error",
	"security.workspace.trust.untrustedFiles": "open",
	"liveServer.settings.donotShowInfoMsg": true,
	"git.confirmSync": false,
	"terminal.integrated.defaultProfile.windows": "Git Bash",
	"google-translate.secondLanguage": "en",
	"css.lint.emptyRules": "ignore",
	"scss.lint.emptyRules": "ignore",
	"bemHelper.modifierSeparator": "_",
	"editor.snippetSuggestions": "top",
	"emmet.showSuggestionsAsSnippets": true,
	"update.enableWindowsBackgroundUpdates": false,
	"update.mode": "default",
	"editor.fontSize": 19,
	"editor.colorDecorators": false,
	"workbench.preferredHighContrastColorTheme": "Red",
	"workbench.preferredDarkColorTheme": "Default High Contrast",
	"workbench.preferredHighContrastLightColorTheme": "Solarized Dark",
	"workbench.preferredLightColorTheme": "Default High Contrast Light",
	"workbench.colorCustomizations": {},
	"git.suggestSmartCommit": false,
	"editor.parameterHints": false,
	"editor.insertSpaces": false,
	"ecsstractor_port.empty_line_before_nested_selector": false,
	"terminal.integrated.profiles.windows": {
		"PowerShell": {
			"source": "PowerShell",
			"icon": "terminal-powershell"
		},
		"Command Prompt": {
			"path": [
				"${env:windir}\\Sysnative\\cmd.exe",
				"${env:windir}\\System32\\cmd.exe"
			],
			"args": [],
			"icon": "terminal-cmd"
		},
		"Git Bash": {
			"source": "Git Bash"
		},
		"Windows PowerShell": {
			"path": "C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe"
		}
	},
	"scm.inputFontSize": 0,
	"markdown.preview.fontSize": 10,
	"terminal.integrated.cursorStyle": "line",
	"terminal.integrated.cursorBlinking": true,
	"terminal.integrated.customGlyphs": false,
	"terminal.explorerKind": "both",
	"terminal.integrated.enableBell": true,
	"emmet.triggerExpansionOnTab": true,
	"liveSassCompile.settings.forceBaseDirectory": "",
	"prettier.useTabs": true,
	"[javascriptreact]": {
		"editor.defaultFormatter": "vscode.typescript-language-features"
		//"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"prettier.enable": false,
	"prettier.semi": false,
	"prettier.singleQuote": true,
	"prettier.singleAttributePerLine": true,
	"[json][jsonc]": {
		"editor.defaultFormatter": "vscode.json-language-features"
	},
	"workbench.settings.applyToAllProfiles": [
		"editor.defaultFormatter"
	],
	"code-runner.saveFileBeforeRun": true,
	"editor.parameterHints.enabled": false,
	"editor.parameterHints.cycle": false,
	"javascript.inlayHints.parameterTypes.enabled": true,
	"editor.inlayHints.enabled": "offUnlessPressed",
	"explorer.confirmDragAndDrop": false,
	"workbench.iconTheme": "vscode-icons",
	"terminal.integrated.fontSize": 16,
	"google-translate.firstLanguage": "ru",
	"typescript.surveys.enabled": false,
	"javascript.inlayHints.variableTypes.suppressWhenTypeMatchesName": false,
	"window.commandCenter": false,
	"workbench.activityBar.location": "top",
	"ecsstractor_port.attributes": "className",
	"workbench.editor.tabSizingFixedMaxWidth": 120,
	"workbench.editor.wrapTabs": true,
	"editor.indentSize": "tabSize",
	"workbench.editor.tabSizing": "shrink",
	"[scss]": {
		//"editor.defaultFormatter": "sibiraj-s.vscode-scss-formatter"
		"editor.defaultFormatter": "vscode.css-language-features"
	},
	"editor.formatOnPaste": true,
	//"editor.defaultFormatter": "vscode.typescript-language-features",
	"workbench.colorTheme": "Oceanic Next", // Открывает новые вкладки без замены
	"better-comments.tags": [
		{
			"tag": "!",
			"color": "#FF2D00",
			"strikethrough": false,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		},
		{
			"tag": "?",
			"color": "#3498DB",
			"strikethrough": false,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		},
		{
			"tag": "//",
			"color": "#474747",
			"strikethrough": true,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		},
		{
			"tag": "todo",
			"color": "#FF8C00",
			"strikethrough": false,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		},
		{
			"tag": "*",
			"color": "#98C379",
			"strikethrough": false,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		},
		{
			"tag": "##",
			"color": "#00689F",
			"strikethrough": false,
			"underline": false,
			"backgroundColor": "transparent",
			"bold": false,
			"italic": false
		}
	],
	"editor.minimap.enabled": false,
	"diffEditor.renderSideBySide": false,
	"files.saveConflictResolution": "overwriteFileOnDisk",
	"git.openRepositoryInParentFolders": "never",
	"html.format.wrapAttributes": "preserve", // wrap html attributes
	"[vue]": {
		"editor.defaultFormatter": "Vue.volar",
		//"editor.defaultFormatter": "octref.vetur"
		//"editor.defaultFormatter": "Vue.volar"
		//"editor.defaultFormatter": "vscode.typescript-language-features"
	},
	"editor.defaultFormatter": "vscode.typescript-language-features",
	"editor.formatOnSave": true,
	"terminal.integrated.tabs.showActiveTerminal": "singleTerminal",
	"terminal.integrated.tabs.location": "left",
	"workbench.editor.highlightModifiedTabs": true,
	"workbench.editor.enablePreview": false,
	"vetur.experimental.templateInterpolationService": true
}