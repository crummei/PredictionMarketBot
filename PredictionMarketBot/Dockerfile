# Use the official .NET SDK image to build the app
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the .csproj file and restore any dependencies (via 'dotnet restore')
COPY *.csproj ./
RUN dotnet restore

# Copy the entire source code into the container
COPY . ./

# Build the application
RUN dotnet publish -c Release -o /out

# Use the official .NET runtime image for running the app
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime

# Set the working directory for the runtime
WORKDIR /app

# Copy the build artifacts from the build image
COPY --from=build /out .

# Set the entry point to run the application
ENTRYPOINT ["dotnet", "YourBotName.dll"]
