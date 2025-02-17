# .NET SDK docker images for the Azure DevOps Container Jobs

The [official Docker images](https://hub.docker.com/_/microsoft-dotnet-sdk/) created by Microsoft provide the .NET SDK for many systems, but these images
are not generally usable for container jobs in Azure DevOps. The hosted agent will try to install the required Node.js runtime which is provided by NodeSource
and only supports glibc-based and windows-based systems. Alpine images eg do NOT work out of the box.

## Disclaimer

Images are published to ghcr.io/smkanadl/sdk. Use at your own risk! Dockerfiles are heavily inspired by the [official documentation](https://github.com/dotnet/dotnet-docker).
