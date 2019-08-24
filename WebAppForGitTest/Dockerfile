FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebAppForGitTest/WebAppForGitTest.csproj", "WebAppForGitTest/"]
RUN dotnet restore "WebAppForGitTest/WebAppForGitTest.csproj"
COPY . .
WORKDIR "/src/WebAppForGitTest"
RUN dotnet build "WebAppForGitTest.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebAppForGitTest.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebAppForGitTest.dll"]