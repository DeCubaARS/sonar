# Use a Windows Server Core image as your base image
FROM mcr.microsoft.com/dotnet/sdk:6.0-windowsservercore-ltsc2019



# Note on .NET Framework Targeting Packs
# For .NET Framework (e.g., 4.7, 4.6.1, 4.6.2), ensure the base Windows image includes the required targeting packs.
# You may need to manually install these or use an image that already includes them.

# Set the working directory
WORKDIR /app

# Default command
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]