FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY ["DemoFallback/DemoFallback.csproj", "DemoFallback/"]
RUN dotnet restore "DemoFallback/DemoFallback.csproj"
COPY . .
WORKDIR "/src/DemoFallback"
RUN dotnet build "DemoFallback.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "DemoFallback.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "DemoFallback.dll"]