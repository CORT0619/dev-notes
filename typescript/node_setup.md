1. create package.json: run `npm init`
2. in order to es modules must add "type": "module" in package.json
 - es modules "import fs from 'fs';"
3. install typescript: npm install typescript --save-dev
4. in scripts section of package.json add: "build": "tsc" 
- converts the typescript code to javascript
5. create a src directory and add index.ts to it
6. if receive an error that it can't find the type declarations the run: "npm i -D @types/node"
7. configure behavior of typescript compiler by adding tsconfig.json

{
	"compilerOptions": {
		"module": "NodeNext", // module system for the program -- CommonJS -> NodeNext
		"moduleResolution": "Node", // how typescript will find code you import Node -> NodeNext
		"target": "ES2020", //flavor of js your code will compile to
		"sourceMap": true, // maps compiled js code to typescript, help with debugging
		"outDir": "dist" // where final js code will be compiled
	},
	"include": ["src/**/*"] // tells typescript where to find our code
}

8. when using nodenext we need to use the .js extension when importing files local to our project, but not needed with node_modules
9. can use .cts extension and then import file with .cjs

Source:
- https://www.youtube.com/watch?v=H91aqUHn8sE&t=15s