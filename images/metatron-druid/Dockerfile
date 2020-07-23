FROM centos:7 as builder

WORKDIR /app

RUN yum -y update
RUN yum -y install wget
#RUN wget "https://sktmetatronkrsouthshared.blob.core.windows.net/metatron-public/discovery-dist/latest/druid-0.9.1-latest-hadoop-2.7.3-bin.tar.gz"
RUN wget "https://github.com/metatron-app/metatron-discovery/releases/download/3.3.3/druid-metatron-3.3.3.tar.gz"
RUN tar -zxf druid-metatron-3.3.3.tar.gz
RUN ln -s druid-0.9.1-SNAPSHOT.201911201314-hadoop-2.7.3 druid

FROM centos:7

WORKDIR /app/druid

RUN yum -y update && \
    yum -y install java && \
    yum clean all

COPY --from=builder /app/druid /app/druid
