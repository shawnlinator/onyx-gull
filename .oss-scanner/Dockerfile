FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src
COPY . .
RUN dotnet publish Jellyfin.Server/Jellyfin.Server.csproj -c Release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /src
COPY . /src
COPY --from=build /app /opt/jellyfin
