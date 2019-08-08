# Blaise_Case_Backup

The Blaise Case Backup application is a Windows service that runs on a virtual machine hosting a Blaise 5 server.
The application works on a timer and preiodically saves a copy of all of the case data from the Blaise system to a backup location on the local drive. This data is then overwritten each time the system is backed up.

# Setup Development Environment

Clone the git respository to your IDE of choice. Visual Studio 2019 is recomended.

Rename the App.config file to App.local.config and populate the key values. **Never use App.config for development.**

Build the solution to obtain the necessary references.

# Installing the Service

  - Build the Solution
    - In Visual Studio select "Release" as the Solution Configuration
    - Select the "Build" menu
    - Select "Build Solution" from the "Build" menu
  - Copy the release files (/bin/release/) to the install location on the server
  - Uninstall any previous installs
    - Stop the service from running
    - Open a command prompt as administrator
    - Navigate to the windows service installer location
      - cd c:\Windows\Microsoft.NET\Framework\v4.0.30319\
    - Run installUtil.exe /U from this location and pass it the location of the service executable
      - InstallUtil.exe /U {install location}\BlaiseCaseHandler.exe
  - Run the installer against the release build
    - Open a command prompt as administrator
    - Navigate to the windows service installer location
      - cd c:\Windows\Microsoft.NET\Framework\v4.0.30319\
    - Run installUtil.exe from this location and pass it the location of the service executable
      - InstallUtil.exe {install location}\BlaiseCaseHandler.exe
    - Set the service to delayed start
    - Start the service
