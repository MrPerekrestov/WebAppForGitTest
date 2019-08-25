FROM mcr.microsoft.com/dotnet/core/sdk:2.2 
WORKDIR /app

COPY . /app

RUN dotnet restore
RUN dotnet build

EXPOSE 5000/tcp

ENTRYPOINT dotnet run



