---
title: Adding a login page with React, MSAL and ASP.NET Core Web API 5
tag: [asp.net core, react]
category: development
---
Outline:
- What are we trying to achieve
- Assumptions & Prerequisites
- 

A lot of applications nowadays have login pages based on OAuth 2. Microsoft made it very easy with MSAL (Microsoft Authentican Library) to do the heavy lifting to support your application in using login via OAuth 2.0 using Microsoft Azure Active Directory.

In this tutorial we will learn:
- How to configure a React application to use the MSAL.js library for authentication
- Authorize our application to communicate with a backend API
- Call protected resources on the Web API to fetch data from the authenticated application

Assumptions:
- Created an empty React application
- Created an empty ASP.NET Web API

In the Web API solution run the command `dotnet add package Microsoft.Identity.Client` to add the MSAL package.
