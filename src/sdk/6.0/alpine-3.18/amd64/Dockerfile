# escape=`

FROM ghcr.io/smkanadl/ado-base-images:alpine-3.18

LABEL org.opencontainers.image.source="https://github.com/smkanadl/ado-dotnet-sdk-images"

RUN apk add --upgrade --no-cache `
        ca-certificates-bundle `
        # runtime dependencies
        libgcc `
        libssl3 `
        libstdc++ `
        # sdk dependencies
        curl `
        git `
        icu-data-full `
        icu-libs `
        libatomic `
        tzdata

RUN `
    wget https://dot.net/v1/dotnet-install.sh && `
    sudo chmod +x ./dotnet-install.sh && `
    ./dotnet-install.sh --install-dir /usr/share/dotnet --channel '6.0' --no-path --architecture x64 && `
    rm dotnet-install.sh

ENV `
    # Root for dotnet
    DOTNET_ROOT=/usr/share/dotnet `
    # Enable detection of running in a container
    DOTNET_RUNNING_IN_CONTAINER=true `
    # .NET Runtime version
    DOTNET_VERSION=6.0.36 `
    # Do not generate certificate
    DOTNET_GENERATE_ASPNET_CERTIFICATE=false `
    # Do not show first run text
    DOTNET_NOLOGO=true `
    # SDK version
    DOTNET_SDK_VERSION=6.0.428 `
    # Enable correct mode for dotnet watch (only mode supported in a container)
    DOTNET_USE_POLLING_FILE_WATCHER=true `
    # Skip extraction of XML docs - generally not useful within an image/container - helps performance
    NUGET_XMLDOC_MODE=skip

ENV PATH="${DOTNET_ROOT}:${PATH}"
