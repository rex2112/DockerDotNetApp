# FROM mono:5.20.1.34-slim AS build
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR webapp

EXPOSE 80
EXPOSE 5024

#COPY PROJECT FILES
COPY ./*.csproj ./
RUN dotnet restore

# COPY EVERYTHING ELSE
COPY . .
RUN dotnet publish -c Release -o out

#Build image
#FROM mono:5.20.1.34-slim
FROM mcr.microsoft.com/dotnet/sdk:5.0
WORKDIR /webapp
COPY --from=build /webapp/out .
ENTRYPOINT ["dotnet", "DockerDotNetApp.dll"]
