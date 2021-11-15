FROM mcr.microsoft.com/dotnet/sdk:6.0 as build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "PlatformService.dll"]

#Build a container:
# docker build -t andraderodrigosilva/platformservice .

#Run a container:
# docker run -p 8080:80 -d andraderodrigosilva/platformservice

#Login DockerHub
# docker login

#Push Container
# docker push andraderodrigosilva/platformservice