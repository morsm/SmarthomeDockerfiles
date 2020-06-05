FROM morsm6777/raspbian-stretch-mono:latest

LABEL description="HippoCmdLightDaemon mono container"

# Get and compile daemon
WORKDIR /hippocmdlight

RUN git clone -b current --depth 1 https://github.com/morsm/HippoCmdLightDaemon.git . \
    && chmod +x querylamp \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /hippocmdlight/bin/Release

CMD mono HippotronicsThermoDaemon.exe

