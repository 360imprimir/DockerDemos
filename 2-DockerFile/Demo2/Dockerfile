FROM microsoft/dotnet:2.1-sdk as build-image

WORKDIR /home/app

COPY . .

RUN dotnet restore

RUN dotnet publish ./HelloWorld/HelloWorld.csproj -o /publish/

FROM microsoft/dotnet:2.1-aspnetcore-runtime

WORKDIR /publish

COPY --from=build-image /publish .

ENTRYPOINT ["dotnet", "HelloWorld.dll"]
