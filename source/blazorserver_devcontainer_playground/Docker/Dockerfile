# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:7.0 as build
WORKDIR /app

COPY ./blazorserver_devcontainer_playground ./

RUN dotnet restore
RUN dotnet publish -c Release -o out --no-restore

# # # # final stage/image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app/out .
EXPOSE 80
ENTRYPOINT ["dotnet", "blazorserver_devcontainer_playground.dll"]