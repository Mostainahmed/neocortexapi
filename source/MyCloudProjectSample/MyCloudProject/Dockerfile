FROM mcr.microsoft.com/dotnet/runtime:6.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["MyCloudProject/MyCloudProject.csproj", "MyCloudProject/"]
COPY ["MyCloudProject.Common/MyCloudProject.Common.csproj", "MyCloudProject.Common/"]
COPY ["MyExperiment/MyExperiment.csproj", "MyExperiment/"]
RUN dotnet restore "MyCloudProject/MyCloudProject.csproj"
COPY . .
WORKDIR "/src/MyCloudProject"
RUN dotnet build "MyCloudProject.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "MyCloudProject.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "MyCloudProject.dll"]
LABEL version="variablei-cc-project 1.0"