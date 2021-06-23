FROM registry.access.redhat.com/ubi8/dotnet-31-runtime:3.1 AS base
USER 1001
WORKDIR /app
EXPOSE 80

FROM registry.access.redhat.com/ubi8/dotnet-31:3.1 AS build
WORKDIR /src
COPY . .
WORKDIR /src/ProCodeGuide.Sample.Microservice
RUN dotnet restore

RUN dotnet build -c Release -o /app/build

FROM build AS publish
RUN dotnet publish -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ProCodeGuide.Sample.Microservice.dll"]
