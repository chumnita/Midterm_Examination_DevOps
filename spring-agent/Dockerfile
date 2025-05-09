FROM jenkins/ssh-agent:jdk17

# Install required tools
RUN apt-get update && \
    apt-get install -y wget unzip curl gnupg2 software-properties-common && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# ✅ Install JDK 24 (from Adoptium API)
RUN curl -L -o jdk-24.tar.gz "https://api.adoptium.net/v3/binary/latest/24/ga/linux/x64/jdk/hotspot/normal/adoptium?project=jdk" && \
    mkdir -p /opt/jdk && \
    tar -xzf jdk-24.tar.gz -C /opt/jdk --strip-components=1 && \
    rm jdk-24.tar.gz

ENV JAVA_HOME=/opt/jdk
ENV PATH="$JAVA_HOME/bin:$PATH"

# ✅ Install PostgreSQL Client
RUN apt-get update && \
    apt-get install -y postgresql-client && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# ✅ Optional: Install Gradle (not required for this part, only if needed later)
# RUN wget https://services.gradle.org/distributions/gradle-8.7-bin.zip && \
#     unzip gradle-8.7-bin.zip -d /opt/gradle && \
#     rm gradle-8.7-bin.zip
# 
# ENV GRADLE_HOME=/opt/gradle/gradle-8.7
# ENV PATH=$GRADLE_HOME/bin:$PATH
