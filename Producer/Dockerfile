FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

COPY producer.csproj .
RUN dotnet restore

COPY src/. .
RUN dotnet publish producer.csproj -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "producer.dll"]
