---
layout: post
title: JWT Authentication in ASP.NET Core Minimal APIs with Swagger
subtitle: 
cover-img: /assets/img/dotnet.jpg
thumbnail-img: /assets/img/netthumb.jpg
share-img: /assets/img/netthumb.jpg
tags: [.net, .netframework, .netcore,.net8, .net6,,Swagger, Minimal APIs, JWT Authentication ]
comments: true
---

### What's inside...
- **_[Introduction](#introduction)_**
- **_[Step 1: Create a new ASP.NET Core Minimal API Project](#step-1-create-a-new-aspnet-core-minimal-api-project)_**
- **_[Step 2: Create Models and Minimal Endpoints](#step-2-create-models-and-minimal-endpoints)_**
- **_[Step 3: Install Necessary NuGet Packages](#step-3-install-necessary-nuget-packages)_**
- **_[Step 4: Update Program.cs with JWT Authentication](#step-4-update-programcs-with-jwt-authentication)_**
- **_[Step 5: Update Program.cs with Swagger Configuration](#step-5-update-programcs-with-swagger-configuration)_**
- **_[Step 6: Run Your Application](#step-6-run-your-application)_**

## Introduction   
In this blog I will walk you through the process of configuring JWT authentication in the ASP.NET Core minimal API and configuring Swagger to support JWT-based authorization. We’ll cover everything from building a project to protecting your end.

## Step 1: Create a new ASP.NET Core Minimal API Project

**Open Visual Studio:**

    Open Visual Studio and click on "Create a new project."

**Choose Project Template:**

    Select "ASP.NET Core Web API" and click "Next."

**Configure Project:**

    - Name your project MinimalApiWithAuth.
    - Choose a location to save your project.
    - Click "Next."

**Additional Information:**

    - Ensure that the "Framework" is set to .NET 6.0 or later.
    - Leave "Authentication Type" set to "None."
    - Click "Create."

## Step 2: Create Models and Minimal Endpoints

Before we set up JWT authentication and Swagger, let's create a simple model and some minimal endpoints.

**1) Create UserLogin Model:**

- Create a new folder named "Models"
- Create a new file inside Models named UserLogin.cs and add the following code:
```csharp
public class UserLogin
{
    public string Username { get; set; }
    public string Password { get; set; }
}
```

**2) Update Program.cs for Minimal Endpoints:**
- Open the Program.cs file and add the following minimal endpoints before **app.Run(); :**

```csharp
...

...

...
app.MapPost("/login", (UserLogin userLogin) =>
{
	if (userLogin.Username == "test" && userLogin.Password == "password")
	{
		return Results.Ok("Login successful");
	}

	return Results.Unauthorized();
});

app.MapGet("/secure", () => "This is a secure endpoint")
   .RequireAuthorization();

app.MapGet("/public", () => "This is a public endpoint");
```
- **/login** endpoint that checks for hardcoded credentials.
- **/secure** endpoint that is intended to be secured with authorization (we'll add authorization in the next steps).
- **/public** endpoint that is accessible without any authentication or authorization.

## Step 3: Install Necessary NuGet Packages

Next, we need to install the packages required for JWT authentication and Swagger.

**1) Open NuGet Package Manager:**

    - Right-click on your project in the Solution Explorer.
    - Select "Manage NuGet Packages".
**2) Install Microsoft.EntityFrameworkCore.SqlServer:**

    - Go to the "Browse" tab.
    - Search for Microsoft.EntityFrameworkCore.SqlServer.
    - Select the package and click "Install".
**3) Install Microsoft.AspNetCore.Authentication.JwtBearer:**

    - Search for Microsoft.AspNetCore.Authentication.JwtBearer.
    - Select the package and click "Install".

**4) Install System.IdentityModel.Tokens.Jwt:**

    - Search for System.IdentityModel.Tokens.Jwt.
    - Select the package and click "Install."


## Step 4: Update Program.cs with JWT Authentication

Open the Program.cs file and follow these steps to set up JWT authentication.

**1) Set Up JWT Authentication**

    Add Using Directives:
    At the top of the Program.cs file, add the following using directives:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.IdentityModel.Tokens;
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using System.Text;
```

**2) Configure JWT Authentication:**

Inside the var builder = WebApplication.CreateBuilder(args);
 section, 
 
 add the JWT authentication configuration:

```csharp

    // Secure key for JWT authentication
    var key = Encoding.ASCII.GetBytes("Your_32_Byte_Secure_Key_1234567890"); 

    builder.Services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuerSigningKey = true,
            IssuerSigningKey = new SymmetricSecurityKey(key),
            ValidateIssuer = false,
            ValidateAudience = false
        };
    });
```

**3) Set Up Authorization**

    Add Authorization Services:
    Add the following line to the services configuration to enable authorization:

```csharp
builder.Services.AddAuthorization();
```

**4) Build and Configure the App**

    Build the App:
    Add the following code to build and configure the app:

```csharp

var app = builder.Build();

app.UseHttpsRedirection();

app.UseAuthentication();
app.UseAuthorization();
```

**5)Map Endpoints with Authentication:**

Update the /login and /secure endpoints to include JWT authentication and authorization:

```csharp

// Endpoint to handle user login and generate JWT
app.MapPost("/login", (UserLogin userLogin) =>
{
    // Validate user credentials (this is just an example, implement proper validation)
    if (userLogin.Username == "test" && userLogin.Password == "password")
    {
        var tokenHandler = new JwtSecurityTokenHandler();
        var tokenDescriptor = new SecurityTokenDescriptor
        {
            Subject = new ClaimsIdentity(new Claim[]
            {
                new Claim(ClaimTypes.Name, userLogin.Username) // Add user claims
            }),
            Expires = DateTime.UtcNow.AddHours(1), // Set token expiration
            SigningCredentials = new SigningCredentials(new SymmetricSecurityKey(key),  
            SecurityAlgorithms.HmacSha256Signature) // Sign the token
        };
        var token = tokenHandler.CreateToken(tokenDescriptor); // Create the token
        var tokenString = tokenHandler.WriteToken(token); // Write the token as a string

        return Results.Ok(new { Token = tokenString }); // Return the token
    }

    return Results.Unauthorized(); // Return unauthorized if validation fails
});

// Secure endpoint that requires authentication
app.MapGet("/secure", [Authorize] () => "This is a secure endpoint");

// Public endpoint that does not require authentication
app.MapGet("/public", () => "This is a public endpoint");

// Run the application
app.Run();

```

## Step 5: Update Program.cs with Swagger Configuration

Open the Program.cs file and follow these steps to set up Swagger with JWT support.

    Add Using Directive:
    Add the using directive for Swagger:

```csharp

using Microsoft.OpenApi.Models;
```

**Configure Swagger:**

Inside the builder.Services.AddEndpointsApiExplorer(); section,configure Swagger to use JWT authentication.
Define a security scheme and requirement for Bearer authentication.

```csharp
builder.Services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new OpenApiInfo { Title = "My API", Version = "v1" });

    var securityScheme = new OpenApiSecurityScheme
    {
        Name = "Authorization",
        Type = SecuritySchemeType.Http,
        Scheme = "bearer",
        BearerFormat = "JWT",
        In = ParameterLocation.Header,
        Description = "Enter your JWT token in the format 'Bearer {your token}'",
        Reference = new OpenApiReference
        {
            Type = ReferenceType.SecurityScheme,
            Id = "Bearer"
        }
    };

    c.AddSecurityDefinition("Bearer", securityScheme);

    var securityRequirement = new OpenApiSecurityRequirement
    {
        {
            new OpenApiSecurityScheme
            {
                Reference = new OpenApiReference
                {
                    Type = ReferenceType.SecurityScheme,
                    Id = "Bearer"
                }
            },
            new string[] {}
        }
    };

    c.AddSecurityRequirement(securityRequirement);
});
```

**Build and Configure Swagger:**

Add the following code to build and configure Swagger:

```csharp
    var app = builder.Build();

    if (app.Environment.IsDevelopment())
    {
        app.UseSwagger();
        app.UseSwaggerUI(c =>
        {
            c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
        });
    }
```


## Step 6: Run Your Application

**1) Build Your Application**

    - In Visual Studio, right-click on the solution in the Solution Explorer.
    - Click on "Build Solution."

**2: Run Your Application**

    Press the "Start" button in Visual Studio to run your application.

**3) Open Swagger UI**

    Navigate to https://localhost:<port>/swagger in your browser.

**4) Authorize with JWT Token**

    Click the "Authorize" button in the Swagger UI.
    Enter your JWT token which is generated after login


