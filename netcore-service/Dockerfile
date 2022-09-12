#ARCHIVO DE CONFIGURACIÓN PARA ARRANQUE DEL CONTENEDOR

#COMPILACIÓN DE LA APLICACION

#ESPECIFICA QUE IMAGEN VAMOS A OCUPAR
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env 
#DEFINE EL DIRECTORIO EN DONDE SE VA A TRABAJAR DENTRO DE LA IMAGEN DEL CONTENEDOR
WORKDIR /app
# . CARPETA ACTUAL ./CARPETA DONDE SE VA A COPIAR
COPY . ./
# SE EJECUTA EN TIEMPO DE COMPILACIÓN LO COMANDOS_ RESTAURA TODAS LAS DEPENDENCIAS QUE SE NECESITA
RUN dotnet restore "/app/Axity.Project.ServiceName.Api/Axity.Project.ServiceName.Api.csproj"
COPY . ./
RUN dotnet publish "/app/Axity.Project.ServiceName.Api/Axity.Project.ServiceName.Api.csproj" -c Release -o out

#COMPILACIÓN DE LA IMAGEN O CONTENEDOR
#aspnet: ayuda a ejecutar la aplicaicón
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
RUN apt-get update
RUN apt-get install -y libgdiplus
WORKDIR /app
COPY --from=build-env /app/out .
#comando que se ejecuta cuando ejecutamos docker run
ENTRYPOINT ["dotnet", "Axity.Project.ServiceName.Api.dll"]