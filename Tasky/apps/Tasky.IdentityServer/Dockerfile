#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["services/administration/NuGet.Config", "services/administration/"]
COPY ["services/identity/NuGet.Config", "services/identity/"]
COPY ["services/saas/NuGet.Config", "services/saas/"]
COPY ["apps/Tasky.IdentityServer/Tasky.IdentityServer.csproj", "apps/Tasky.IdentityServer/"]
COPY ["services/administration/src/Tasky.AdministrationService.EntityFrameworkCore/Tasky.AdministrationService.EntityFrameworkCore.csproj", "services/administration/src/Tasky.AdministrationService.EntityFrameworkCore/"]
COPY ["services/administration/src/Tasky.AdministrationService.Domain/Tasky.AdministrationService.Domain.csproj", "services/administration/src/Tasky.AdministrationService.Domain/"]
COPY ["services/administration/src/Tasky.AdministrationService.Domain.Shared/Tasky.AdministrationService.Domain.Shared.csproj", "services/administration/src/Tasky.AdministrationService.Domain.Shared/"]
COPY ["services/identity/src/Tasky.IdentityService.EntityFrameworkCore/Tasky.IdentityService.EntityFrameworkCore.csproj", "services/identity/src/Tasky.IdentityService.EntityFrameworkCore/"]
COPY ["services/identity/src/Tasky.IdentityService.Domain/Tasky.IdentityService.Domain.csproj", "services/identity/src/Tasky.IdentityService.Domain/"]
COPY ["services/identity/src/Tasky.IdentityService.Domain.Shared/Tasky.IdentityService.Domain.Shared.csproj", "services/identity/src/Tasky.IdentityService.Domain.Shared/"]
COPY ["services/saas/src/Tasky.SaaSService.EntityFrameworkCore/Tasky.SaaSService.EntityFrameworkCore.csproj", "services/saas/src/Tasky.SaaSService.EntityFrameworkCore/"]
COPY ["services/saas/src/Tasky.SaaSService.Domain/Tasky.SaaSService.Domain.csproj", "services/saas/src/Tasky.SaaSService.Domain/"]
COPY ["services/saas/src/Tasky.SaaSService.Domain.Shared/Tasky.SaaSService.Domain.Shared.csproj", "services/saas/src/Tasky.SaaSService.Domain.Shared/"]
COPY ["shared/Tasky.Shared.Hosting/Tasky.Shared.Hosting.csproj", "shared/Tasky.Shared.Hosting/"]
# RUN dotnet restore "apps/Tasky.IdentityServer/Tasky.IdentityServer.csproj"
# COPY . .
# WORKDIR "/src/apps/Tasky.IdentityServer"
# RUN dotnet build "Tasky.IdentityServer.csproj" -c Release -o /app/build

# FROM build AS publish
# RUN dotnet publish "Tasky.IdentityServer.csproj" -c Release -o /app/publish /p:UseAppHost=false

# FROM base AS final
# WORKDIR /app
# COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Tasky.IdentityServer.dll"]