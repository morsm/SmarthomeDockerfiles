FROM mono:latest
ARG RELEASE

LABEL description="ArduinoSerialDaemon mono container"

# Install GIT, we'll need it
RUN apt-get update && apt-get install -y git && apt-get clean

# Get and compile ArduinoSerial daemon
WORKDIR /seriald

RUN git clone -b $RELEASE --depth 1 https://github.com/morsm/HippoArduinoSerialDaemon.git . \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /seriald/bin/Release

EXPOSE 9003/tcp

CMD mono HippoArduinoSerialDaemon.exe

