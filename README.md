# jstype
javascript with type

### Configuration

- Start by installing TypeScript as a development dependency
```
npm install typescript --save-dev
```

- Create a tsconfig.json file
```
npx tsc --init
```

- Update your tsconfig.json
```
{
  "compilerOptions": {
    "allowJs": true,
    "checkJs": true,
    "noEmit": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": false,
    "skipLibCheck": true
  }
}
```
- Add a script to your package.json
```
"scripts": {
  "type-check": "tsc"
}
```
- Run npm run type-check
```
npm run type-check
```
- Fix missing types ex: Node
```
npm install @types/node --save-dev
```
- Add to the build process
```
"scripts": {
  "type-check": "tsc",
  "test": "node --test && npm run type-check"
}
```
- Adding more types using JSDoc
@type:
```
/**
 * @type {Array<string>}
 */
let names = [];
```
@typedef:
```
/**
 * @typedef {object} TeamMember
 * @property {string} name - the full name of a team member
 * @property {Array<string>} languages - the programming languages the member knows
 */

/**
 * @type {TeamMember}
 */
const teamMember = {
  name: "Phil Nash",
  languages: ["JavaScript", "TypeScript", "CSS", "HTML"],
};
```
param and return:
```
/**
 * @typedef {import("./teamMember").TeamMember} TeamMember
 * @param {Array<TeamMember>} teamMembers - a list of team members
 * @returns {Array<string>}
 */

function getNames(teamMembers) {
  return teamMembers.map(tm => tm.name);
}
```
More : [JSDoc supported types by TypeScript](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html)