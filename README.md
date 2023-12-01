## Packages Monorepo

Source code for packages are contained within this repository.
A package should ideally be created if there is potential we are going to create something and then re-use it.

---

### Creating a package

A package should follow the same format as a standard Nevermore package would.

```
src
    Server
    Client
    Shared
default.project.json
package.json
```

**default.project.json**

```json
{
  "name": "{{PACKAGE_NAME}}",
  "tree": {
    "$path": "src"
  }
}
```

**package.json**

```json
{
  "name": "@marizma/{{PACKAGE_NAME}}",
  "version": "1.0.0",
  "description": "{{A SHORT DESCRIPTION}}",
  "repository": {
    "type": "git",
    "url": "https://github.com/Marizma/packages.git",
    "directory": "src/{{PACKAGE_NAME}}/"
  },
  "publishConfig": {
    "access": "public",
    "@marizma:registry": "https://npm.pkg.github.com"
  }
}
```

---

### Deploy a package

In order to deploy a package to the Marizma org, first commit the update to this repository.

```
cd PACKAGE_FOLDER
git push origin main
```

After that, login with the correct scope and publish the package.

> [!IMPORTANT]
> You must ensure that you are in the package folder before publishing.

```
npm login --registry=https://npm.pkg.github.com --scope=@marizma
npm publish
```
