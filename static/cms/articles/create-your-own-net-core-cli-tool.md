---
title: "Create your own .NET CLI Tool with .NET 8"
excerpt: Learn how to create a .NET Command Line Interface (CLI) Tool using .NET 8 and build your own global tools.
date: 2025-04-30
series: ["Development"]
weight: 1
aliases: ["/create-your-own-net-cli-tool-dotnet8"]
tags: [".NET", "CLI", "Development"]
showToc: true
---

In this guide, we will explore how to develop a .NET Command Line Interface (CLI) Tool using .NET 8 and build your own global tools to simplify your workflow.

## Source

You can find the source code for this tutorial on [GitHub](https://github.com/your-repo/dotnet-cli-tool).

## Built with

- .NET 8 Console App
- DotNet Tool & nupkg

## Prerequisites

- Ensure you have the latest .NET 8 SDK installed (SDK 8.0 and above only).
- Visual Studio 2022 (17.8 or later) or JetBrains Rider 2025.1.1.

## Create Your Own CLI

In this example, we will create a .NET CLI tool to fetch current weather data for a given city. You will need to register for an API key from [OpenWeatherMap](https://openweathermap.org/api).

### Step 1: Create a .NET Console App

Run the following command to create a new .NET Console App:

```shell
dotnet new console -n Weather.Cli
```

### Step 2: Add a Weather Service Class

Create a `WeatherService` class to fetch weather data from the OpenWeatherMap API. Use `HttpClient` to make API requests.

### Step 3: Build the nupkg

Run the following command to package your application into a `.nupkg` file:

```shell
dotnet pack
```

### Step 4: Install the Tool Globally

Install the `.nupkg` file as a global tool using the following command:

```shell
dotnet tool install --global --add-source ./nupkg weather.cli
```

### Step 5: Run the CLI Tool

You can now execute the CLI tool from anywhere by typing:

```shell
weather
```

## Additional Resources

For more details on creating .NET tools, refer to the official documentation: [Create .NET Tools](https://learn.microsoft.com/en-us/dotnet/core/tools/global-tools-how-to-create).

That's it! Start building your own CLI tools and enhance your productivity.
