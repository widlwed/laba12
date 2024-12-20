# Этап 1: Сборка приложения с использованием SDK
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env

WORKDIR /app

# Копируем файл проекта и восстанавливаем зависимости
COPY *.csproj ./
RUN dotnet restore

# Копируем остальные файлы приложения
COPY . ./

# Собираем и публикуем приложение в папку out
RUN dotnet publish -c Release -o out

# Этап 2: Используем образ с .NET Runtime для запуска приложения
FROM mcr.microsoft.com/dotnet/runtime:6.0

WORKDIR /app

# Копируем опубликованное приложение из первого этапа
COPY --from=build-env /app/out .

# Устанавливаем точку входа для запуска приложения
ENTRYPOINT ["dotnet", "ProgramModuleHW12.dll"]