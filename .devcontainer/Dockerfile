FROM ubuntu:noble@sha256:72297848456d5d37d1262630108ab308d3e9ec7ed1c3286a32fe09856619a782
# ubuntu:noble-20250127

ENV DEBIAN_FRONTEND=noninteractive
# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE=1
# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED=1

RUN apt update && \
    apt install --no-install-recommends -y \
    python3 python3-pip git curl locales 
RUN apt install --no-install-recommends -y \
    texlive texlive-extra-utils \
    texlive-base texlive-latex-recommended texlive-latex-extra \
    latexmk texlive-xetex texlive-pstricks texlive-science \
    texlive-fonts-recommended texlive-fonts-extra \
    texlive-lang-german texlive-lang-english \
    libyaml-tiny-perl libfile-homedir-perl \
    texlive-bibtex-extra biber
RUN apt install --no-install-recommends -y tzdata \
    && ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime \
    && dpkg-reconfigure --frontend noninteractive tzdata

    # generating locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8 LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8

RUN texhash

RUN apt-get -y clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/apt/*


