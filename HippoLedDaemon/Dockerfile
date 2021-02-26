FROM mono:latest
ARG RELEASE

LABEL description="HippoLedDaemon mono container"

# Install GIT, we'll need it
RUN apt-get update && apt-get install -y git && apt-get clean

# Get and compile HippoLed daemon
WORKDIR /hippoledd

RUN git clone -b $RELEASE --depth 1 https://github.com/morsm/HippoLedDaemon.git . \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /hippoledd/bin/Release

EXPOSE 9000/tcp

CMD mono HippotronicsLedDaemon.exe

