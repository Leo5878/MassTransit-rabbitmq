FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

COPY consumer.csproj .
RUN dotnet restore

COPY src/. .
RUN dotnet publish consumer.csproj -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "consumer.dll"]
