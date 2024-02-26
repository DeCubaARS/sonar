# Start from the .NET SDK base image
FROM mcr.microsoft.com/dotnet/sdk:latest

# Install Node.js
RUN curl -sL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs

# Install unzip and other necessary packages
RUN apt-get update && apt-get install -y \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install SonarScanner
ENV SONAR_SCANNER_VERSION 5.0.1.3006
ENV SONAR_SCANNER_HOME /opt/sonar-scanner
RUN curl --create-dirs -sSLo /tmp/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-${SONAR_SCANNER_VERSION}-linux.zip \
    && unzip -o /tmp/sonar-scanner.zip -d /opt \
    && mv /opt/sonar-scanner-${SONAR_SCANNER_VERSION}-linux ${SONAR_SCANNER_HOME} \
    && rm /tmp/sonar-scanner.zip \
    && chmod +x ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
    && ln -s ${SONAR_SCANNER_HOME}/bin/sonar-scanner /usr/bin/sonar-scanner

# Install JetBrains dotCover Command Line Tools (example using wget, adjust as necessary)
# You need to agree to the JetBrains license and terms to use dotCover.
# Please download dotCover command-line tools manually from the official site and follow their license agreement.
# The following is an example and might not work directly without adjusting for the actual dotCover CLI setup.
ENV DOTCOVER_HOME /opt/dotcover

ENV DOTCOVER_HOME /opt/dotcover
RUN mkdir -p ${DOTCOVER_HOME} \
    && wget -qO- https://download.jetbrains.com/resharper/dotUltimate.2023.3.3/JetBrains.dotCover.CommandLineTools.linux-arm64.2023.3.3.tar.gz | tar -xzC ${DOTCOVER_HOME} \
    && chmod +x ${DOTCOVER_HOME}/dotCover.sh \
    && ln -s ${DOTCOVER_HOME}/dotCover.sh /usr/bin/dotCover


# Set the working directory
WORKDIR /app

# Default command
CMD ["bash"]
