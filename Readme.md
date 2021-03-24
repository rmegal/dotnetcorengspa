# Sample .NET Core Angular SPA

## Overview

I am using this repo to recreate a problem with Angular Material Tooltips where the tooltip displays and then immediately disappears after hovering over the element. This occurs only when using matTooltipClass and only in an Angular SPA running under .NET Core using the dotnet angular template.

![Demo](https://github.com/rmegal/media/blob/main/videos/dotnetcorengspa_001.gif)

## Steps to Create
* run `dotnet new angular` from the project directory.
* run `dotnet new sln` followed by `dotnet sln dotnetcorengspa.sln add dotnetcorengspa\dotnetcorengspa.csproj` from the parent directory.
* run `ng update @angular/core@8 @angular/cli@8` to clean up dependencies.
* run `ng add @angular/material`.
* Create class selector (.tooltip) in global styles for tooltips.
* Create a couple of buttons on the home page using Material. Assign tooltips to both and use matTooltipClass to assign tooltip class to one.
* Update to Angular/Material V9
  * Run `npm install tslib --save` to intall tslib dependency.
  * Running `ng update @angular/core@9 @angular/cli@9` results in the following at this point:

  ```
  Using package manager: 'npm'
  Collecting installed dependencies...
  Found 42 dependencies.
  Fetching dependency metadata from registry...
      Updating package.json with dependency @angular-devkit/build-angular @ "0.901.15" (was "0.803.29")...
      Updating package.json with dependency @angular/cli @ "9.1.15" (was "8.3.29")...
      Updating package.json with dependency @angular/compiler-cli @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/language-service @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency typescript @ "3.8.3" (was "3.5.3")...
      Updating package.json with dependency @angular/animations @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/common @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/compiler @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/core @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/forms @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/platform-browser @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/platform-browser-dynamic @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/platform-server @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency @angular/router @ "9.1.13" (was "8.2.14")...
      Updating package.json with dependency zone.js @ "0.10.3" (was "0.9.1")...
    UPDATE package.json (1751 bytes)
  ? Installing packages (npm)...npm ERR! code ERESOLVE
  npm ERR! ERESOLVE unable to resolve dependency tree
  npm ERR!
  npm ERR! Found: @angular-devkit/build-angular@0.803.29
  npm ERR! node_modules/@angular-devkit/build-angular
  npm ERR!   dev @angular-devkit/build-angular@"^0.901.15" from the root project
  npm ERR!
  npm ERR! Could not resolve dependency:
  npm ERR! dev @angular-devkit/build-angular@"^0.901.15" from the root project
  npm ERR!
  npm ERR! Conflicting peer dependency: @angular/compiler-cli@9.1.13
  npm ERR! node_modules/@angular/compiler-cli
  npm ERR!   dev @angular/compiler-cli@"^9.1.13" from the root project
  npm ERR!   peer @angular/compiler-cli@">=9.0.0 < 10" from @angular-devkit/build-angular@0.901.15
  npm ERR!   node_modules/@angular-devkit/build-angular
  npm ERR!     dev @angular-devkit/build-angular@"^0.901.15" from the root project
  npm ERR!
  npm ERR! Fix the upstream dependency conflict, or retry
  npm ERR! this command with --force, or --legacy-peer-deps
  npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
  npm ERR!
  npm ERR! See C:\Users\ray\AppData\Local\npm-cache\eresolve-report.txt for a full report.

  npm ERR! A complete log of this run can be found in:
  npm ERR!     C:\Users\ray\AppData\Local\npm-cache\_logs\2021-03-24T18_55_26_222Z-debug.log
  ? Package install failed, see above.
  × Migration failed. See above for further details.
  ```

  * The only way I was able to work around this was to run `npm install --force`. The `ng update` does update the package.json file but npm fails. Using `--force` allows it to complete. Things *look* OK.
  * Run `ng update @angular/core@9 @angular/cli@9` again to be sure.

  ```
  Using package manager: 'npm'
  Collecting installed dependencies...
  Found 42 dependencies.
  Fetching dependency metadata from registry...
  Package '@angular/core' is already up to date.
  Package '@angular/cli' is already up to date.
  ```

  * Run `ng update @angular/material@9`.
* Site works. Problem persists.
* Upgrade to Angular/Material V10.
  ```
  npm uninstall @nguniversal/module-map-ngfactory-loader
  ng update @angular/core@10 @angular/cli@10
  npm install --force
  ng update @angular/material@10
  ```
  * Remove import of ModuleMapLoaderModule from '@nguniversal/module-map-ngfactory-loader'.
* Site works. Problem persists.
* Upgrade to Angular/Material V11.
  ```
  ncu -u codelyzer
  npm install
  git commit -a
  ng update @angular/core@latest @angular/cli@latest
  npm install --force
  ng update @angular/material@11
  ```
* Site works. Problem persists.


## Notes

I've done as little as possible to the original code created by the dotnet angular template in order to recreate the problem. The problem persists even after updating to the latest angular/material, including updating remaining packages.
