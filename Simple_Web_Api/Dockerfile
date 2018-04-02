FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80
#EXPOSE 6000

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY Simple_Web_Api.sln ./
COPY Simple_Web_Api/Simple_Web_Api.csproj Simple_Web_Api/
RUN dotnet restore -nowarn:msb3202,nu1503
COPY . .
WORKDIR /src/Simple_Web_Api
RUN dotnet build -c Release -o /app

FROM build AS publish
RUN dotnet publish -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Simple_Web_Api.dll"]
