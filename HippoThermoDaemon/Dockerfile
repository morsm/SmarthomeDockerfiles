FROM mono:latest
ARG RELEASE

LABEL description="HippoThermoDaemon mono container"

# Install GIT, we'll need it
RUN apt-get update && apt-get install -y git && apt-get clean

# Get and compile HippoThermo daemon
WORKDIR /thermod

RUN git clone -b $RELEASE --depth 1 https://github.com/morsm/HippoThermoDeamon.git . \
    && nuget restore \
    && msbuild -p:Configuration=Release *csproj

WORKDIR /thermod/bin/Release

EXPOSE 9002/tcp

CMD mono HippotronicsThermoDaemon.exe

