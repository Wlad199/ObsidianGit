```css
/*color: #7ee787;*/
/*color: #ff79c6;*/
/*color: #71aaff;*/
/*color: #bda96c;*/
/*color: #ff757f;*/
/*color: #f9f200 */
/*color: #f90000*/
/*color: #e0de5c*/
/*color: #c1d443*/
/*color: #f79320*/
/*color: #f05c26*/
/*color: #9dc7e1*/

/* Title */
.inline-title{
	font-size: 40px !important;
	color: #f90000 !important;
}
h1{
	color: #ff79c6!important;
	font-size: 35px!important;
}
h2{
	color: #7ee787!important;
	font-size: 30px!important;
}
h3{
	color: #71aaff!important;
	font-size: 25px!important;
}
h4{
	color: #bda96c!important;
	font-size: 25px!important;
}


/* List */
li{
	font-size: 18px !important;
	color: #e8eeb7!important;
	margin-bottom: 5px;
	line-height: 130%;
	position: relative;
	&:before{
		content: '';
		position: absolute;
		top: 0;
		left: -26px;
		width: 23px;
		height: 23px;
		background-color: #282f3e;
		z-index: 1;
	}
	&:after{
		content: '';
		position: absolute;
		top: 8px;
		left: -20px;
		width: 10px;
		height: 10px;
		border-radius: 50%;
		background-color: #e8eeb7;
		z-index: 1;
	}
}


hr{
	margin: 10px 80px;
	border-bottom: 1px solid #959200!important;
}
.tree-item-inner{
font-size: 13px !important;
}
.tree-item-self {
	padding-top: 1px !important;
	padding-bottom: 1px !important;
}


/* Link */
a{
	color: #d5007a !important;
	transition: all 0.2s ease 0s;
}
a:hover{
	color: #aa0062 !important;
}


/* sidebar */
.markdown-preview-view {
	padding: 10px 20px !important;
}


/* calendar */
#calendar-container > div > div{
	margin-top: 7px;
}
#calendar-container > div > div > div.reset-button.svelte-1vwr9dd{
	margin: 0;
	margin-top: 7px;
	font-size: 10px;
	line-height: 0;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-sidedock.mod-right-split > div:nth-child(4) > div.workspace-tab-container > div > div > div.view-content{
	padding-top: 0;
	padding-bottom: 0;
}
.month, .year {
	font-size: 16px;
	margin-bottom: 10px !important;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-sidedock.mod-right-split > div:nth-child(4) > div.workspace-tab-header-container{
	display: none;
}


/* header menu */
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-vertical.mod-root > div > div.workspace-tab-header-container > div.workspace-tab-header-container-inner{
	margin-top: -1px;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-vertical.mod-root > div > div.workspace-tab-header-container{
	margin-bottom: -4px;
}


/* side menu */
body:not(.is-grabbing) .nav-file-title.is-active:hover, body:not(.is-grabbing) .nav-folder-title.is-active:hover, .nav-file-title.is-active, .nav-folder-title.is-active {
    color: var(--nav-item-color-active);
    background-color: #3a455a;
    font-weight: var(--nav-item-weight-active);
}
.theme-dark {
    --nav-item-background-hover: #3a455a;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-sidedock.mod-right-split > div.workspace-tabs.mod-top.mod-top-right-space > div.workspace-tab-container > div:nth-child(1) > div > div.tag-container.node-insert-event > div > div > div > div.tree-item-inner{
	color: #d1ca00;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-sidedock.mod-right-split > div.workspace-tabs.mod-top.mod-top-right-space > div.workspace-tab-container > div:nth-child(1) > div > div.tag-container.node-insert-event > div > div> div > div.tree-item-flair-outer > span{
	color: #d1ca00!important;
}
.tree-item-inner-text{
	color: #d1ca00;
}
body > div.app-container > div.horizontal-main-container > div > div.workspace-split.mod-horizontal.mod-sidedock.mod-right-split > div.workspace-tabs.mod-top.mod-top-right-space > div.workspace-tab-container > div:nth-child(1) > div > div.tag-container.node-insert-event > div > div > div.tree-item-children > div > div.tree-item-self.tag-pane-tag.is-clickable > div.tree-item-flair-outer > span{
	color: #d1ca00;
}


/* Comments */
.token.comment{
	background-color: #282f3e;
	color: #6666ff;
	padding: 2px 20px 3px 10px;
	border-radius: 3px;
	position: relative;
	&:before{
		content: '';
		position: absolute;
		top: 0;
		left: 10px;
		width: 23px;
		height: 23px;
		z-index: 1;
		background-color: inherit;
	}
		&:after{
		content: '';
		position: absolute;
		top: 7px;
		left: 18px;
		width: 10px;
		height: 10px;
		border-radius: 50%;
		z-index: 1;
		background-color: #6666ff;
	}
}
```