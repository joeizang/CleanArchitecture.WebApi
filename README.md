 # ASP.NET Core WebApi - Clean Architecture

![.NET Core](https://github.com/joeizang/CleanArchitecture.WebApi/workflows/.NET%20Core/badge.svg?branch=master)
[![Twitter Follow](https://img.shields.io/twitter/follow/codewithmukesh?style=social&label=follow)](https://twitter.com/josephizang1)

<br/>

An Implementation of Clean Architecture with .NET 6 & ASP.NET Core WebApi. With this Open-Source BoilerPlate Template, you will get access to the world of Loosely-Coupled and Inverted-Dependency Architecture in ASP.NET Core WebApi.

## Releases - ASP.NET Core Template
v1.5 - Stable Release - [Download the Stable Release](https://github.com/joeizang/CleanArchitecture.WebApi/releases/tag/v1.5) 

## v1.1

Follow these steps to get started with this Boiler Plate Template.

### Download the Extension
Make sure Visual Studio 2019 is installed on your machine with the latest SDK.
[Download from Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MukeshMurugan.CleanArchitectureWebApi). Install it on your machine.

Follow these Steps to get started.

![alt text](https://www.codewithmukesh.com/wp-content/uploads/2020/08/cleanArchitecture_VisualStudio.png)

![alt text](https://www.codewithmukesh.com/wp-content/uploads/2020/08/cleanArchitecture_NewProject.png)

You Solution Template is Ready!

![alt text](https://www.codewithmukesh.com/wp-content/uploads/2020/08/cleanArchitecture_FolderStructure.png)

Visit the Project Page to learn more - [Click Here](https://www.codewithmukesh.com/project/aspnet-core-webapi-clean-architecture/)

### Alternatively you can also clone the Repository.

1. Clone this Repository and Extract it to a Folder.
3. Change the Connection Strings for the Application and Identity in the WebApi/appsettings.json - (WebApi Project)
2. Run the following commands on Powershell in the WebApi Projecct's Directory.
- dotnet restore
- dotnet ef database update -Context ApplicationDbContext
- dotnet ef database update -Context IdentityContext
- dotnet run (OR) Run the Solution using Visual Studio 2019

Check out my [blog](https://www.codewithmukesh.com) or say [Hi on Twitter!](https://twitter.com/codewithmukesh)

### How to use PostgreSQL as your Data Provider
The Project currently uses MSSQL as the default Data Provider. If you are more comfortable with PostgreSQL, here is how to migrate to them easily.


1. delete all existing file inside migrations folder on both project
   - {YourProjectName}.Infrastructure.Identity
   - {YourProjectName}.Infrastructure.Persistence

2. In in `ServiceExtensions.cs` and `ServiceRegistration.cs` change from `options.UseSqlServer` to:
#### For PostgreSQL
`options.UseNpgsql`

3. Add NuGet packages to both projects (Infrastructure.Identity and Infrastructure.Persistence):
#### For PostgreSQL:
run 
```cli
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL.Design
```
(remember to do this on both projects)

4. on `IdentityContext.cs` comment `builder.HasDefaultSchema("Identity");` because ef doesn't support that on mysql

5. cd to `{YourProjectName}.Infrastructure.Identity` and run
   - `dotnet ef database update --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "IdentityContext"`
   - `dotnet ef migrations add Initial --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "IdentityContext"`

6. cd to `{YourProjectName}.Infrastructure.Persistence` and run
   - `dotnet ef database update --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "ApplicationDbContext"`
   - `dotnet ef migrations add Initial --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "ApplicationDbContext"`
   
The above guide (To use MySQL) was contributed by [geekz-reno](https://github.com/geekz-reno).

### Default Roles & Credentials
As soon you build and run your application, default users and roles get added to the database.

Default Roles are as follows.
- SuperAdmin
- Admin
- Moderator
- Basic

Here are the credentials for the default users.
- Email - superadmin@gmail.com  / Password - 123Pa$$word!
- Email - basic@gmail.com  / Password - 123Pa$$word!

You can use these default credentials to generate valid JWTokens at the ../api/account/authenticate endpoint.

## Purpose of this Project

Mukesh did a great job with this template. I just forked it because I don't really like the newer templates. So I took time and updated this template and it works very very well. Big thanks to Mukesh for the ground work.

## Give a Star ⭐️
If you found this Implementation helpful or used it in your Projects, do give it a star. Thanks!

## Technologies
- ASP.NET Core 6.0.2 WebApi
- REST Standards
- .NET 6.0

## Features
- [x] Onion Architecture
- [x] CQRS with MediatR Library
- [x] Entity Framework Core - Code First
- [x] Repository Pattern - Generic
- [x] MediatR Pipeline Logging & Validation
- [x] Serilog
- [x] Swagger UI
- [x] Response Wrappers
- [x] Healthchecks
- [x] Pagination
- [ ] In-Memory Caching
- [ ] Redis Caching
- [x] In-Memory Database
- [x] Microsoft Identity with JWT Authentication
- [x] Role based Authorization
- [x] Identity Seeding
- [x] Database Seeding
- [x] Custom Exception Handling Middlewares
- [x] API Versioning
- [x] Fluent Validation
- [x] Automapper
- [x] SMTP / Mailkit / Sendgrid Email Service
- [x] Complete User Management Module (Register / Generate Token / Forgot Password / Confirmation Mail)
- [x] User Auditing

## Questions? Bugs? Suggestions for Improvement?
Having any issues or troubles getting started? [Get in touch with me](https://www.codewithmukesh.com/contact) or [Raise a Bug or Feature Request](https://github.com/joeizang/CleanArchitecture.WebApi/issues/new/choose). Always happy to help.

## Licensing
joeizang/CleanArchitecture.WebApi Project is licensed with the [MIT License](https://github.com/joeizang/CleanArchitecture.WebApi/blob/master/LICENSE).
