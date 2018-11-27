FROM microsoft/dotnet:2.1-sdk

WORKDIR /home/app

COPY . .

RUN dotnet restore

RUN dotnet publish ./HelloWorld/HelloWorld.csproj -o /publish/

WORKDIR /publish

ENTRYPOINT ["dotnet", "HelloWorld.dll"]
