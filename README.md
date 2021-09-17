# Discord.Net
[![NuGet](https://img.shields.io/nuget/vpre/Discord.Net.svg?maxAge=2592000?style=plastic)](https://www.nuget.org/packages/Discord.Net)
[![MyGet](https://img.shields.io/myget/discord-net/vpre/Discord.Net.svg)](https://www.myget.org/feed/Packages/discord-net)
[![Build Status](https://dev.azure.com/discord-net/Discord.Net/_apis/build/status/discord-net.Discord.Net?branchName=dev)](https://dev.azure.com/discord-net/Discord.Net/_build/latest?definitionId=1&branchName=dev)
[![Discord](https://discord.com/api/guilds/81384788765712384/widget.png)](https://discord.gg/jkrBmQR)

An unofficial .NET API Wrapper for the Discord client (https://discord.com).

## Documentation

- [Nightly](https://docs.stillu.cc/)
  - [Latest CI repo](https://github.com/discord-net/docs-static)

## Installation
### Stable (NuGet)
Our stable builds available from NuGet through the Discord.Net metapackage:
- [Discord.Net](https://www.nuget.org/packages/Discord.Net/)

The individual components may also be installed from NuGet:
- [Discord.Net.Commands](https://www.nuget.org/packages/Discord.Net.Commands/)
- [Discord.Net.Rest](https://www.nuget.org/packages/Discord.Net.Rest/)
- [Discord.Net.WebSocket](https://www.nuget.org/packages/Discord.Net.WebSocket/)
- [Discord.Net.Webhook](https://www.nuget.org/packages/Discord.Net.Webhook/)

### Unstable (MyGet)
Nightly builds are available through our MyGet feed (`https://www.myget.org/F/discord-net/api/v3/index.json`).

## Compiling
In order to compile Discord.Net, you require the following:

### Using Visual Studio
- [Visual Studio 2017](https://www.microsoft.com/net/core#windowsvs2017)
- [.NET Core SDK](https://www.microsoft.com/net/download/core)

The .NET Core workload must be selected during Visual Studio installation.

### Using Command Line
- [.NET Core SDK](https://www.microsoft.com/net/download/core)

## Known Issues

### WebSockets (Win7 and earlier)
.NET Core 1.1 does not support WebSockets on Win7 and earlier. This issue has been fixed since the release of .NET Core 2.1. It is recommended to target .NET Core 2.1 or above for your project if you wish to run your bot on legacy platforms; alternatively, you may choose to install the [Discord.Net.Providers.WS4Net](https://www.nuget.org/packages/Discord.Net.Providers.WS4Net/) package.

## Versioning Guarantees

This library generally abides by [Semantic Versioning](https://semver.org). Packages are published in MAJOR.MINOR.PATCH version format.

An increment of the PATCH component always indicates that an internal-only change was made, generally a bugfix. These changes will not affect the public-facing API in any way, and are always guaranteed to be forward- and backwards-compatible with your codebase, any pre-compiled dependencies of your codebase.

An increment of the MINOR component indicates that some addition was made to the library, and this addition is not backwards-compatible with prior versions. However, Discord.Net **does not guarantee forward-compatibility** on minor additions. In other words, we permit a limited set of breaking changes on a minor version bump.

Due to the nature of the Discord API, we will oftentimes need to add a property to an entity to support the latest API changes. Discord.Net provides interfaces as a method of consuming entities; and as such, introducing a new field to an entity is technically a breaking change. Major version bumps generally indicate some major change to the library, and as such we are hesitant to bump the major version for every minor addition to the library. To compromise, we have decided that interfaces should be treated as **consumable only**, and your applications should typically not be implementing interfaces. (For applications where interfaces are implemented, such as in test mocks, we apologize for this inconsistency with SemVer).

Furthermore, while we will never break the API (outside of interface changes) on minor builds, we will occasionally need to break the ABI, by introducing parameters to a method to match changes upstream with Discord. As such, a minor version increment may require you to recompile your code, and dependencies, such as addons, may also need to be recompiled and republished on the newer version. When a binary breaking change is made, the change will be noted in the release notes.

An increment of the MAJOR component indicates that breaking changes have been made to the library; consumers should check the release notes to determine what changes need to be made.
