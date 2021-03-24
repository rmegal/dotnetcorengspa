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

## Notes
* I've done as little as possible to the original code created by the dotnet angular template in order to recreate the problem. The problem persists even after updating to the latest angular/material, including updating remaining packages.
