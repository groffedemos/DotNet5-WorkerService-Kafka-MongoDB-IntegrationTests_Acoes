FROM mcr.microsoft.com/dotnet/sdk:5.0.202 AS build-env
WORKDIR /app

# Exibir a versão do SDK do .NET 5
RUN dotnet --version

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
FROM mcr.microsoft.com/dotnet/aspnet:5.0.5
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "WorkerAcoes.dll"]