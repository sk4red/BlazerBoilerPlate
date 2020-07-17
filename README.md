Cloned from https://github.com/enkodellc/blazorboilerplate

Blazor is a web framework designed to run in the browser on a WebAssembly-based .NET runtime. Blazor Boilerplate aka Blazor Starter Template is a SPA admin template that is able to BOTH (WebAssembly / Core-Hosted) and Server-Side Blazor with a .NET Core 3.1 Server. The UI for this application is by Material Design provided mostly by MatBlazor.
Version 0.2.3 and below utilize AspNETCore Authorization / Authentication. Version 0.3.0 and up will be using Identity Server 4. Version 0.6.0 and up are capable of both CSB and SSB!    

## Repository Notes
- Read the news below to stay up to date on the repo. We will try to keep the latest major changes on a different branch and have the more stable / tested version on the master branch.
- Development Branch is the latest dev code for future release.
- Fluxor - Branched from version 0.6.0 with an example with [Blazor Fluxor](https://github.com/enkodellc/blazorboilerplate/tree/blazorfluxor) *Note: not really being maintained at this time

[![Build Status](https://enkodellc.visualstudio.com/blazorboilerplate/_apis/build/status/enkodellc.blazorboilerplate?branchName=master)](https://enkodellc.visualstudio.com/blazorboilerplate/_build/latest?definitionId=1&branchName=master)
[![Live Demo](https://img.shields.io/badge/demo-online-green.svg)](https://blazorboilerplate.com)
[![GitHub Stars](https://img.shields.io/github/stars/enkodellc/blazorboilerplate.svg)](https://github.com/enkodellc/blazorboilerplate/stargazers)
[![GitHub Issues](https://img.shields.io/github/issues/enkodellc/blazorboilerplate.svg)](https://github.com/enkodellc/blazorboilerplate/issues)
[![MIT](https://img.shields.io/github/license/SamProf/MatBlazor.svg)](LICENSE)
[![Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.me/enkodellc)
[![Gitter](https://badges.gitter.im/BlazorBoilerplate/community.svg)](https://gitter.im/blazorboilerplate/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

## Goals
- This repository is community driven. It is not and never will be controlled by a corporation. It's success is dependent on people using it, reviewing it, offering suggestions and most importantly contributing. Please join the [gitter discussion](https://gitter.im/blazorboilerplate/community) 
- To create a boilerplate with Blazor / Razor components that includes the most common functionality to start a real world application quickly.
- Avoid many external components & libraries which can make it difficult to maintain, update, track down code, learn code and issues.
- Minimal Javascript. Currently only using them for SignalR for the Forum and MatBlazor / Material Design. We may use components with JS in them but so far no Javascript has been written specifically for anything in the repository.


# Live demo
- [Blazor Boilerplate - CSB/WASM](https://blazorboilerplate.com) - Kick the tires.  *Note Firewall does block some foreign IP addresses. Swagger UI to view the server API [https://blazorboilerplate.com/swagger/index.html](https://blazorboilerplate.com/swagger/index.html).
- [Demo for Development Branch - Blazor Server Side Tenant](https://blazor-server.quarella.net/)
- [Demo for Development Branch - Blazor WebAssembly Tenant](https://blazor-wasm.quarella.net/)

## Prerequisites
Don't know what Blazor is? Read [here](https://docs.microsoft.com/en-us/aspnet/core/blazor)

Complete all Blazor dependencies.

- The latest [.Net Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- Install the Latest Visual Studio 2019 with the ASP.NET and web development workload selected.
- Entity Framework Core on the command-line tools: **dotnet tool install --global dotnet-ef**

### How to run
1. Install the latest .NET Core SDK **https://dotnet.microsoft.com/download/dotnet-core/3.1** and the latest **Visual Studio 2019 (v16.6)**
2. Clone or download.
3. Open the solution in Visual Studio and press F5.
4. To view the API using Swagger UI, Run the solution and go to: [http://localhost:53414/swagger/index.html](http://localhost:53414/swagger/index.html). Live example:
[https://blazorboilerplate.com/swagger/index.html](https://blazorboilerplate.com/swagger/index.html)

## Publish on IIS - What works for me on my Windows Server 2016 & SQL Server 2014 (Enkodellc)
1. Publish BlazorBoilerplate.Server project to your IIS website folder using CSB or SSB.
2. Install your SSL. Make sure your SSL is in the **WebHosting** Certificate Store.
    - A free certificate from [Let's Encrypt](https://letsencrypt.org/) will work. 
    - For steps 2 & 3 the utility [win-acme](https://github.com/win-acme/win-acme) installs the
certificate on your server, performs renewal and configure your IIS Website Bindings to have https binding with the SSL certificate set and Port 443 for default.

4. Configure your IIS Website Bindings to have https binding with the SSL certificate set and Port 443 for default.
3. Configure / create appsettings.production.config. Set  Connection String, Thumbprint / SSL. Thumbprint example:  **143fbd7bc36e78b1bcf9a53c13336eaebe33353a**
4. Login with either the user **[user | user123]** or admin **[admin | admin123]** default accounts.


## License
This project is licensed under the terms of the [MIT license](LICENSE).

### Problem Solving Tips
- If you are having issues wih authentication or any other strange behavior try using Incognito mode / different browser. 
- Make sure you have all pre-requisites installed.
- Keep It Simple Stupid: If you are running into issues with SQL / connection string. First CHECK both appsettings.json (appsettings.production.json for production) and (appsettings.development.json for development). 
- Test out with SQLlite / file db. Then test out with a known good connection string.
- Go back to the Origin: BlazorBoilerplate was built off of [BlazorWithIdentity](https://github.com/stavroskasidis/BlazorWithIdentity) so first step is to run this and try and publish. The reasoning is that this is a very lean project to reduce the amount of code and resources requiring debugging.
- If still failing get on [Gitter BlazorBoilerplate](https://gitter.im/blazorboilerplate/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
 for Blazor Boilerplate or  [Gitter aspnet/Blazor](https://gitter.im/aspnet/Blazor?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge).
- Debugging is very limited on WebAssembly / Client-side Blazor. Use Debug_SSB for debugging the UI. Just be aware of browser caching issues when switching modes.
 The server side of the project can easily be debugged, just not there yet on the client-side code.
- If you are getting compiler errors try and close VS delete your .vs directory in the solution folder. If that doesn't work delete the solution and redownload the repo.
 
### Postgres Support
*Note this might be out of date.. Delete Existing Migrations in the BlazorBoilerplate.Server/Migrations Folder and then create your own migrations:  
  -`dotnet ef --startup-project ..\BlazerBoilerplate.Server migrations add InitialApplicationDbMigration --context ApplicationDbContext -o Migrations\ApplicationDb`  
  -`dotnet ef --startup-project ..\BlazorBoilerplate.Server\ migrations add InitialConfigurationDbMigration --context ConfigurationDbContext  -o Migrations\ConfigurationDb`  
  -`dotnet ef --startup-project ..\BlazorBoilerplate.Server\ migrations add PersistedGrantDbContext --context PersistedGrantDbContext -o Migrations\PersistedGrantDb`  

### Docker Support
- Prerequisite: Install [Docker Desktop](https://go.microsoft.com/fwlink/?linkid=847268) 
- Include / Reload **docker-compose** project in solution.
- [Do Docker stuff](https://docs.docker.com/v17.09/docker-for-windows/install/) - I don't have much experience with Docker.

### Azure Support
- [Azure Hosting Wiki](https://github.com/enkodellc/blazorboilerplate/wiki/Hosting-Blazor-boilerplate-on-Microsoft-Azure) 
- *Note that Azure isn't as up to date with their SDK as Blazor Boilerplate so you might have to use an older version
