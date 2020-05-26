FROM raspbian/stretch:latest

# Version by Maarten ter Mors to build mono image based on Raspbian
# Install Mono, Mono-devel and basic gcc tools so we can build what will run in these containers from latest source


ENV MONO_VERSION 6.8.0.123

RUN apt-get update \
  && apt-get install -y --no-install-recommends gnupg dirmngr git gcc make libc6-dev g++ \
  && rm -rf /var/lib/apt/lists/* \
  && export GNUPGHOME="$(mktemp -d)" \
  && gpg --batch --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
  && gpg --batch --export --armor 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF > /etc/apt/trusted.gpg.d/mono.gpg.asc \
  && gpgconf --kill all \
  && rm -rf "$GNUPGHOME" \
  && rm -rf /var/lib/apt/lists/* /tmp/*

RUN echo "deb http://download.mono-project.com/repo/debian stable-raspbianstretch/snapshots/$MONO_VERSION main" > /etc/apt/sources.list.d/mono-official-vs.list \
    && apt-get update \
    && apt-get install -y mono-runtime binutils curl mono-devel ca-certificates-mono fsharp mono-vbnc nuget referenceassemblies-pcl \
  && rm -rf /var/lib/apt/lists/* /tmp/*

