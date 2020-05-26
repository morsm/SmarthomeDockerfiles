FROM morsm6777/raspbian-stretch-mono:latest

LABEL description="HippoLedDaemon mono container"

# Get and compile HippoLed daemon
WORKDIR /hippoledd

RUN git clone -b current --depth 1 https://github.com/morsm/HippoLedDaemon.git . \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /hippoledd/bin/Release

CMD mono HippotronicsLedDaemon.exe

