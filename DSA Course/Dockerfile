FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["DSA Course/DSA Course.csproj", "DSA Course/"]
RUN dotnet restore "DSA Course/DSA Course.csproj"
COPY . .
WORKDIR "/src/DSA Course"
RUN dotnet build "DSA Course.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DSA Course.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DSA Course.dll"]
