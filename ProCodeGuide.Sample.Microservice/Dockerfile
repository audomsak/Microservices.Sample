FROM registry.access.redhat.com/ubi8/dotnet-31:3.1
USER 1001
RUN mkdir sample-ms
WORKDIR sample-ms
ADD . .

RUN dotnet publish -c Release

EXPOSE 8080
ENTRYPOINT ["dotnet", "./bin/Release/netcoreapp3.0/publish/ProCodeGuide.Sample.Microservice.dll"]
