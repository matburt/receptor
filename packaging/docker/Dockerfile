FROM registry.access.redhat.com/ubi8/python-36

USER root

RUN mkdir -p /receptor /receptor_data

ADD https://github.com/krallin/tini/releases/download/v0.18.0/tini /bin/tini
ADD entrypoint.sh /bin/entrypoint
ADD receptor.conf /receptor/receptor.conf
ADD receptor-0.2.0-py2.py3-none-any.whl /tmp

RUN pip install /tmp/receptor-0.2.0-py2.py3-none-any.whl

VOLUME /receptor
VOLUME /receptor_data

ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8
ENV RECEPTOR_MODE=node
ENV HOME=/receptor

ENTRYPOINT ["entrypoint"]
CMD ["receptor", "-c", "/receptor/receptor.conf", "$(RECEPTOR_MODE)"]
