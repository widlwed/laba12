# ���� 1: ������ ���������� � �������������� SDK
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env

WORKDIR /app

# �������� ���� ������� � ��������������� �����������
COPY *.csproj ./
RUN dotnet restore

# �������� ��������� ����� ����������
COPY . ./

# �������� � ��������� ���������� � ����� out
RUN dotnet publish -c Release -o out

# ���� 2: ���������� ����� � .NET Runtime ��� ������� ����������
FROM mcr.microsoft.com/dotnet/runtime:6.0

WORKDIR /app

# �������� �������������� ���������� �� ������� �����
COPY --from=build-env /app/out .

# ������������� ����� ����� ��� ������� ����������
ENTRYPOINT ["dotnet", "ProgramModuleHW12.dll"]