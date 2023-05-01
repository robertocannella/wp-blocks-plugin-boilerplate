# wp-blocks-plugin-boilerplate

## Cloning

To use this repository as a starting point for new wp-blocks plugins:

* clone this repository with your plugins directory
* add a unique plug-in name at the end of the clone command

```
git clone https://github.com/robertocannella/wp-blocks-plugin-boilerplate.git text-box
```

* change into the repository directory
```
cd text-box/
```

* rename orgin to `upstream`

```
git remote rename origin upstream 
```
* create a new repository on github
* add the new repositor as origin
```
git remote add origin https://github.com/robertocannella/wp-blocks-text-box.git
```
* add all files to repository 
```
git add -A 
```
* commit 
```
git commit -m "initial commit"
```
* push and change origin
```
git push -u origin main
```
## Change following files:

* `blocks.json`
```
{
	"apiVersion": 2,
	"name": "blocks-course/todo-list",  <--- Change This
	"title": "To Do List",              <--- Change This
	"category": "widgets",              <--- Change This
	"icon": "editor-ul",                <--- Change This
	"description": "Display and edit todos in the data store.", <-- Change This
        "keyword": ["text", "paragraph","box"],                     <-- Change This (optional field)
	"supports": {
		"html": false
	},
	"textdomain": "blocks-course-todo-list",                    <-- Change This
	"editorScript": "file:build/index.js",
	"editorStyle": "file:./build/index.css",
	"style": "file:./build/style-index.css"
}

```
* src/index.js
```
import { registerBlockType } from '@wordpress/blocks';
import './style.scss';
import Edit from './edit';
import save from './save';
import { __ } from '@wordpress/i18n';

registerBlockType('blocks-course/todo-list', {
	title: __('To Do List', 'blocks-course-todo-list'),  <-- Change This (must match name in block.json)
	description: __(
		'Display and edit todos in the data store.', 
		'blocks-course-todo-list'
	),
	edit: Edit,
	save,
});
```
* rename `plugin.php` to approprate name: `todo-list.php`

## Build files
```
npm install
```
May need to run if getting this error: (HookWebpackError: error:0308010C:digital envelope routines::unsupported)
```
npm audit fix --force
```
