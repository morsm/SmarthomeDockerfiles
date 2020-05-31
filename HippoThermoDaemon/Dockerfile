FROM morsm6777/raspbian-stretch-mono:latest

LABEL description="HippoThermoDaemon mono container"

# Get and compile daemon
WORKDIR /hippothermo

RUN git clone -b current --depth 1 https://github.com/morsm/HippoThermoDeamon.git . \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /hippothermo/bin/Release

COPY config.json .

CMD mono HippotronicsThermoDaemon.exe

