##See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
#FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
#WORKDIR /app
#EXPOSE 80
#EXPOSE 443
#
#FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
#WORKDIR /src
#COPY ["DockerizedBlazor/DockerizedBlazor.csproj", "DockerizedBlazor/"]
#RUN dotnet restore "DockerizedBlazor/DockerizedBlazor.csproj"
#COPY . .
#WORKDIR "/src/DockerizedBlazor"
#RUN dotnet build "DockerizedBlazor.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DockerizedBlazor.csproj" -c Release -o /app/publish
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DockerizedBlazor.dll"]

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /vsdbg
RUN apt-get update \
    && apt-get install -y --no-install-recommends unzip \
    && rm -rf /var/lib/apt/lists/* \
    && curl -sSL https://aka.ms/getvsdbgsh | bash /dev/stdin -v latest -l /vsdbg
WORKDIR /app
EXPOSE 443 80
ENTRYPOINT dotnet watch run --no-launch-profile