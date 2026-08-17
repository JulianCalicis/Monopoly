# Monopoly
## Setup the workspace
```bat
npm i
```
## Known Issues 
1. npm error - Missing script: "test"
	- delete the file `.husky/pre-commit`
2. husky - commit-msg script failed (code 126)
	- change the encoding of the `.husky/commit-msg` to `Western European (Windows) - Code page 1252`
3. npm error code ENOENT - Could not read package.json
	- Manual package installation and configuration:
	```bat
	npm i -D @commitlint/cli @commitlint/config-conventional 
	npm pkg set scripts.prepare="husky"
	npm i -D husky
	node -e "fs.writeFileSync('commitlint.config.mjs', process.argv[1])" "export default { extends: ['@commitlint/config-conventional'] };"
	md .husky ; cmd /A /C "echo npx commitlint -s -e > .husky/commit-msg"
	npm run prepare
	```
4. commit passes without being linted - husky config issue
	- Manual configuration
	```bat	
	npm pkg set scripts.prepare="husky"
	md .husky ; cmd /A /C "echo npx commitlint -s -e > .husky/commit-msg"
	npm run prepare
	```