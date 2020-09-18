# ABP Angular Quick Start

## How to Prepare Development Environment

Please follow the steps below to prepare your development environment for Angular.

1. **Install Node.js:** Please visit [Node.js downloads page](https://nodejs.org/en/download/) and download proper Node.js v12 or v14 installer for your OS. An alternative is to install [NVM](https://github.com/nvm-sh/nvm) and use it to have multiple versions of Node.js in your operating system.
2. **[Optional] Install Yarn:** You may install Yarn v1 (not v2) following the instructions on [the installation page](https://classic.yarnpkg.com/en/docs/install). Yarn v1 delivers an arguably better developer experience compared to npm v6 and below. You may skip this step and work with npm, which is built-in in Node.js, instead.
3. **[Optional] Install VS Code:** [VS Code](https://code.visualstudio.com/) is a free, open-source IDE which works seamlessly with TypeScript. Although you can use any IDE including Visual Studio or Rider, VS Code will most likely deliver the best developer experience when it comes to Angular projects. ABP project templates even contain plugin recommendations for VS Code users, which VS Code will ask you to install when you open the Angular project folder. Here is a list of recommended extensions:
   - [Angular Language Service](https://marketplace.visualstudio.com/items?itemName=angular.ng-template)
   - [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
   - [TSLint](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin)
   - [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=visualstudioexptteam.vscodeintellicode)
   - [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
   - [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
   - [Angular 10 Snippets - TypeScript, Html, Angular Material, ngRx, RxJS & Flex Layout](https://marketplace.visualstudio.com/items?itemName=Mikael.Angular-BeastCode)
   - [JavaScript (ES6) code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)
   - [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)
   - [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
   - [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)

## How to Start a New Angular Project

You have multiple options to initiate a new Angular project that works with ABP:

### 1. Using ABP CLI

ABP CLI is probably the most convenient and flexible way to initiate an ABP solution with an Angular frontend. Simply [install the ABP CLI](/CLI.md) and run the following command in your terminal:

```shell
abp new MyCompanyName.MyProjectName -csf -u angular
```

> To see further options in the CLI, please visit the [CLI manual](/CLI.md).

This command will prepare a solution with an Angular and a .NET Core project in it. Please visit [Getting Started section](/Getting-Started.md?UI=NG&DB=EF&Tiered=No#abp-cli-commands-options) for further instructions on how to set up the backend of your solution.

To continue reading without checking other methods, visit [Angular project structure section](#angular-project-structure).

### 2. Direct Download

You may [download a solution scaffold directly on ABP.io](https://abp.io/get-started) if you are more comfortable with GUI or simply want to try ABP without installing the CLI.

Please do the following:

1. Click on the "DIRECT DOWNLOAD" tab.
2. Fill out the short form about your project.
3. Click on the "Create now" button.

...and a customized download will start in a few seconds.

## Angular Project Structure

After creating a solution, open its "angular" directory in your IDE. Here is how the contents of the root folder looks like:

<img alt="Angular project root folder structure" src="./images/quick-start---root-folder-structure.png" width="300" />

Let's see what these folders and files are for:

- **.vscode** has extension recommendations in it.
- **e2e** is a separate app for possible end-to-end tests.
- **src** is where the source files for your application are placed. We will have a closer look in a minute.
- **.browserlistrc** helps [configuring browser compatibility of your Angular app](https://angular.io/guide/build#configuring-browser-compatibility).
- **.editorconfig** helps you have a shared coding style for separate editors and IDEs. Check [EditorConfig.org](https://editorconfig.org/) for details.
- **.gitignore** defined which files and folders should not be tracked by git. Check [git documentation](https://git-scm.com/docs/gitignore) for details.
- **.prettierrc** includes simple coding style choices for [Prettier](https://prettier.io/), an auto-formatter for TypeScript, HTML, CSS, and more. If you install recommended extensions to VS Code, you will never have to format your code anymore.
- **angular.json** is where Angular workspace is defined. It holds project configurations and workspace preferences. Please refer to [Angular workspace configuration](https://angular.io/guide/workspace-config) for details.
- **karma.conf.js** holds [Karma test runner](https://karma-runner.github.io/) configurations.
- **package.json** is where your [package dependencies](https://angular.io/guide/npm-packages) are listed. It also includes some useful scripts for developing, testing, and building your application.
- **README.md** includes some of Angular CLI command examples. You either have to install Angular CLI globally or run these commands starting with `yarn` or `npx` to make them work.
- **start.ps1** is a simple PowerShell script to install dependencies and start a [development server via Angular CLI](https://angular.io/cli/serve), but you probably will not need that after reading this document.
- **tsconfig.json** and all other [tsconfig files](https://angular.io/guide/typescript-configuration) in general, include some TypeScript and Angular compile options.
- **yarn.lock** enables installing consistent package versions across different devices so that working application build will not break because of a package update. Please read [Yarn documentation](https://classic.yarnpkg.com/en/docs/yarn-lock/) if you are interested in more information on the topic. If you have decided to use npm, please remove this file and keep the [package-lock.json](https://docs.npmjs.com/files/package-lock.json) instead.

Now let's take a look at the contents of the source folder.

<img alt="Angular project source folder structure" src="./images/quick-start---source-folder-structure.png" width="300" />

- **app** is the main directory you put your application files in. Any module, component, directive, service, pipe, guard, interceptor, etc. should be placed here. You are free to choose your own folder structure, but "folders reflecting your business features" is generally a fine practice.
- **home** is a predefined module and acts as a welcome page. It also demonstrates how a feature-based folder structure may look like. More complex features will probably have sub-features, thus inner folders. You may change the home folder however you like.
- **shared** is spared for reusable code that works for several modules. Some, including yours truly, may disagree with using a single module for all shared code, so consider adding standalone sub-modules inside this folder instead of adding everything into **shared.module.ts**.
- **app-routing.module.ts** is where your top-level routes are defined. Angular is capable of [lazy loading feature modules](https://angular.io/guide/lazy-loading-ngmodules), so not all routes will be here. You may think of Angular routing as a tree and this file is the top of the tree.
- **app.component.ts** is essentially the top component that holds the dynamic application layout.
- **app.module.ts** is the root module that includes information about how parts of your application are related and what to run at the initiation of your application.
- **route.provider.ts** is used for [modifying the menu](https://docs.abp.io/en/abp/latest/UI/Angular/Modifying-the-Menu).
- **assets** is for static files. A file (e.g. an image) placed in this folder will be available as is when the application is served.
- **environments** includes one file per environment configuration. There are two configurations by default, but you may always introduce another one. These files are directly referred to in _angular.json_ and help you have different builds and application variables. Please refer to [configuring Angular application environments](https://angular.io/guide/build#configuring-application-environments) for details.
- **index.html** is the HTML page served to visitors and will contain everything required to run your application. Servers should be configured to redirect every request to this page so that the Angular router can take over. Do not worry about how to add JavaScript and CSS files to it, because Angular CLI will do it automatically.
- **main.ts** bootstraps and configures Angular application to run in the browser. It is production-ready, so forget about it.
- **polyfill.ts** is where you can add polyfills if you want to support legacy browsers.
- **style.scss** is the default entry point for application styles. You can change this or add new entry points in _angular.json_.
- **test.ts** helps the unit test runner discover and bootstrap spec files.

Phew! So many files, right? Yet, most of them are typically not subject to change or even when they are so, the CLI tooling will do the job for you. The main focus should be on the **app** folder and its content.

Next, we will take a look at the commands used to prepare, build, and serve our application.